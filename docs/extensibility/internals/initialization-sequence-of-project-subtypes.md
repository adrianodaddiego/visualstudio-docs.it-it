---
title: Sequenza di inizializzazione dei sottotipi di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f8b256e25bc9a63093d14eab50d7628c76558b9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349846"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sequenza di inizializzazione dei sottotipi di progetto
L'ambiente costruisce un progetto chiamando l'implementazione della factory di progetto di base di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. La costruzione di un sottotipo di progetto inizia quando l'ambiente determina che l'elenco GUID tipo di progetto per l'estensione del file di progetto non è vuota. L'estensione di file di progetto e il GUID del progetto specificare se il progetto è un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tipo di progetto. Ad esempio, l'estensione vbproj e {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identificare un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto.

## <a name="environments-initialization-of-project-subtypes"></a>Inizializzazione dell'ambiente di sottotipi di progetto
 La procedura seguente illustra in dettaglio la sequenza di inizializzazione per un sistema di progetto aggregato da più sottotipi di progetto.

1. L'ambiente chiama il progetto di base <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, e anche se il progetto consente di analizzare il file di progetto individua che non è il tipo di progetto di aggregazione GUID elenco `null`. Il progetto interrompe direttamente la creazione di un progetto.

2. Le chiamate di progetto `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> per creare un sottotipo di progetto usando l'implementazione dell'ambiente del servizio il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> (metodo). All'interno di questo metodo l'ambiente effettua chiamate di funzione ricorsiva per le implementazioni di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> GUID, iniziando sottotipo di progetto più esterno del tipo di metodi mentre verifica l'elenco dei progetti.

     Di seguito vengono illustrati i passaggi di inizializzazione.

    1. Implementazione dell'ambiente del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> chiamate al metodo il `HrCreateInnerProj` metodo con la dichiarazione di funzione seguente:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Quando questa funzione viene chiamata per la prima volta, vale a dire, per il sottotipo di progetto più esterno, i parametri `pOuter` e `pOwner` vengono passati come `null` e la funzione imposta il sottotipo di progetto più esterno `IUnknown` a `pOuter`.

    2. Successivamente l'ambiente chiama `HrCreateInnerProj` funzione con il secondo tipo di progetto GUID nell'elenco. Questo GUID corrisponde alla secondario sottotipo di progetto interno l'esecuzione di istruzioni per il progetto di base nella sequenza di aggregazione.

    3. Il `pOuter` cora al `IUnknown` del sottotipo di progetto più esterno, e `HrCreateInnerProj` chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> seguita da una chiamata all'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. Nelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metodo si passa il controllo `IUnknown` del sottotipo di progetto più esterno, `pOuter`. Il progetto di proprietà (del sottotipo di progetto interna) deve creare qui il relativo oggetto progetto di aggregazione. Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> si passa un puntatore all'implementazione del metodo di `IUnknown` del progetto interno da aggregare. Questi due metodi di creano dell'oggetto di aggregazione e le implementazioni devono rispettare le regole di aggregazione COM per garantire che un sottotipo di progetto non terminare che contiene un conteggio dei riferimenti a se stesso.

    4. `HrCreateInnerProj` chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. In questo metodo, il sottotipo di progetto esegue l'attività di inizializzazione. È possibile, ad esempio, registrare gli eventi della soluzione in <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5. `HrCreateInnerProj` viene chiamato in modo ricorsivo fino a quando non viene raggiunto il GUID dell'ultimo (il progetto di base) nell'elenco. Per ognuna di queste chiamate, vengono ripetuti i passaggi da a d, c. `pOuter` punta al sottotipo di progetto più esterno `IUnknown` per ogni livello di aggregazione.

## <a name="example"></a>Esempio

Nell'esempio seguente illustra in dettaglio il processo a livello di codice in una rappresentazione approssimativo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> il metodo viene implementato dall'ambiente. Il codice è solo un esempio; non deve essere compilato e controllo degli errori è stato rimosso per maggiore chiarezza.

```cpp
HRESULT CreateAggregateProject
(
    LPCOLESTR lpstrGuids,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    REFIID iidProject,
    void **ppvProject)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpunkProj;
    CComPtr<IVsAggregatableProject> srpAggProject;
    CComBSTR bstrGuids = lpstrGuids;
    BOOL fCanceled = FALSE;
    *ppvProject = NULL;

    HrCreateInnerProj(
         bstrGuids, NULL, NULL, pszFilename, pszLocation,
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);
    srpunkProj->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggProject));
    srpAggProject->OnAggregationComplete();
    srpunkProj->QueryInterface(iidProject, ppvProject);
}

HRESULT HrCreateInnerProj
(
    WCHAR *pwszGuids,
    IUnknown *pOuter,
    IVsAggregatableProject *pOwner,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    IUnknown **ppInner,
    BOOL *pfCanceled
)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpInner;
    CComPtr<IVsAggregatableProject> srpAggInner;
    CComPtr<IVsProjectFactory> srpProjectFactory;
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;
    GUID guid = GUID_NULL;
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');
    WCHAR wszText[_MAX_PATH+150] = L"";

    if (pwszNextGuids)
    {
        *pwszNextGuids++ = 0;
    }

    CLSIDFromString(pwszGuids, &guid);
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(
        guid, &srpProjectFactory);
    srpProjectFactory->QueryInterface(
        IID_IVsAggregatableProjectFactory,
        (void **)&srpAggPF);
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);
    srpInner->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggInner);

    if (pOwner)
    {
        IfFailGo(pOwner->SetInnerProject(srpInner));
    }

    if (pwszNextGuids)
    {
        CComPtr<IUnknown> srpNextInner;
        HrCreateInnerProj(
            pwszNextGuids, pOuter ? pOuter : srpInner,
            srpAggInner, pszFilename, pszLocation, pszName,
            grfCreateFlags, &srpNextInner, pfCanceled);
    }

    return srpAggInner->InitializeForOuter(
        pszFilename, pszLocation, pszName, grfCreateFlags,
        IID_IUnknown, (void **)ppInner, pfCanceled);
}
```

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)