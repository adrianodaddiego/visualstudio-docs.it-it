---
title: Esposizione di oggetti di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f40c523c058bf215cc4574b3aa4a2e038c833beb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044670"
---
# <a name="exposing-project-objects"></a>Esposizione di oggetti di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I tipi di progetto personalizzati possono fornire oggetti di automazione per consentire l'accesso al progetto usando le interfacce di automazione. Ogni tipo di progetto deve fornire lo standard <xref:EnvDTE.Project> oggetto di automazione a cui si accede da <xref:EnvDTE.Solution>, che contiene una raccolta di tutti i progetti aperti nell'IDE. È previsto che ogni elemento nel progetto devono essere esposte da un <xref:EnvDTE.ProjectItem> oggetto cui si accede con <xref:EnvDTE.Project.ProjectItems>. Oltre a questi oggetti di automazione standard, è possono scegliere i progetti offrire agli oggetti di automazione specifico del progetto.  
  
 È possibile creare oggetti di automazione a livello di radice personalizzata che è possibile accedere con associazione tardiva dall'oggetto DTE radice usando `DTE.<customeObjectName>` o `DTE.GetObject(“<customObjectName>”)`. Ad esempio, Visual C++ Crea raccolta di progetti specifici del progetto C++ denominato "VCProjects" che è possibile accedere usando DTE. VCProjects o DTE. GetObject("VCProjects"). È anche possibile creare un Project. Object, che è univoco per il tipo di progetto, un CodeModel, che è possibile eseguire query per l'oggetto più derivato, un oggetto ProjectItem, che espone un FileCodeModel e ProjectItem. Object.  
  
 È una convenzione comune per i progetti per esporre una raccolta di progetti personalizzati, specifici del progetto. Ad esempio, [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] crea una raccolta di progetti specifici di C++ che è quindi possibile accedere tramite `DTE.VCProjects` o `DTE.GetObject("VCProjects")`. È anche possibile creare un `Project.Object`, che è univoco per il tipo di progetto, un `Project.CodeModel`, che è possibile eseguire query per l'oggetto più derivato, un `ProjectItem`, che espone `ProjectItem.Object`e un `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Per contribuire a un oggetto specifico del VSPackage per un progetto  
  
1. Aggiungere le chiavi appropriate al file pkgdef del pacchetto VSPackage.  
  
     Ad esempio, ecco le impostazioni con estensione pkgdef per il progetto in linguaggio C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2. Implementare il codice nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (metodo), come nell'esempio seguente.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     Nel codice, `g_wszAutomationProjects` è il nome della raccolta di progetti. Il `GetAutomationProjects` metodo crea un oggetto che implementa le `Projects` interfaccia e restituisce un `IDispatch` puntatore all'oggetto chiamante, come illustrato nell'esempio di codice seguente.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     È consigliabile scegliere un nome univoco per l'oggetto di automazione. Conflitti di nomi sono imprevedibili e conflitti di causano un nome di oggetto in conflitto essere buttato arbitrariamente se più tipi di progetto usano lo stesso nome. È necessario includere il proprio nome azienda o alcuni aspetti del proprio nome di prodotto nel nome dell'oggetto di automazione univoco.  
  
     L'oggetto personalizzato `Projects` oggetto della raccolta è un punto di ingresso praticità per la parte rimanente del modello di automazione progetto. L'oggetto del progetto è accessibile dalle <xref:EnvDTE.Solution> nella raccolta di progetti. Dopo aver creato le voci appropriate di codice e del Registro di sistema che forniscono i consumer con `Projects` raccolta di oggetti, l'implementazione deve fornire rimanenti oggetti standard per il modello di progetto. Per altre informazioni, vedere [progetto di modellazione](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
