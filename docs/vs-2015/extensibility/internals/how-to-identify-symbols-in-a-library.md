---
title: 'Procedura: Identificare i simboli in una libreria | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f154c63940189f1a6035246fb7f72ec27be677f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116251"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Procedura: Identificare i simboli in una libreria
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Strumenti di esplorazione dei simboli visualizzano le visualizzazioni gerarchiche di simboli. I simboli rappresentano gli spazi dei nomi, oggetti, classi, membri di classi e altri elementi del linguaggio.  
  
 Ogni simbolo nella gerarchia può essere identificata mediante le informazioni di navigazione passate dalla libreria di simboli per il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestione degli oggetti tramite le interfacce seguenti:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 La posizione del simbolo nella gerarchia consente di distinguere un simbolo. Consente gli strumenti di esplorazione dei simboli passare a un simbolo specifico. Il percorso completo univoco per il simbolo determina la posizione. Ogni elemento nel percorso è un nodo. Il percorso inizia con il nodo di primo livello e termina con il simbolo specifico. Ad esempio, se il metodo M1 è un membro della classe C1 e C1 è N1 dello spazio dei nomi, il percorso completo del metodo M1 viene N1. C1. M1. Questo percorso contiene tre nodi: N1, C1 e M1.  
  
 Le informazioni sulla navigazione consente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] object manager per individuare, selezionare e mantenere selezionato i simboli nella gerarchia. Consente di passare da uno strumento di esplorazione a altra. Quando si usa **Visualizzatore oggetti** per individuare i simboli in un [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] progetto, è possibile fare clic con il pulsante destro un metodo e avviare la **Visualizzatore chiamate** strumento che mostra il metodo in un grafico delle chiamate.  
  
 Due forme descrivono la posizione del simbolo. La forma canonica si basa su un percorso completo del simbolo. Rappresenta una posizione esclusiva del simbolo nella gerarchia. È indipendente dello strumento di esplorazione dei simboli. Per ottenere le informazioni sul formato canonico, il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] object manager chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> (metodo). Il formato di presentazione descrive la posizione del simbolo all'interno di uno strumento specifico per l'esplorazione del simbolo. La posizione del simbolo è rispetto alla posizione di altri simboli nel hierarchicy. Un determinato simbolo può avere diversi percorsi di presentazione, ma solo un percorso canonico. Ad esempio, se la classe C1 viene ereditata dalla classe C2 e sono entrambe le classi nello spazio dei nomi N1, il **Visualizzatore oggetti** consente di visualizzare lo struttura ad albero gerarchica seguente:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Il percorso canonico della classe C2, in questo esempio è N1 + C2. Percorso di presentazione del C2 include nodi C1 e "Basi e interfacce": N1 + C1 + "basi e interfacce" + C2.  
  
 Per ottenere le informazioni sul formato di presentazione, le chiamate di gestione di oggetti <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> (metodo).  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Che identifica un simbolo nella gerarchia  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Per ottenere canonico e presentazione basata su form informazioni  
  
1. Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     Il gestore oggetti chiama questo metodo per ottenere l'elenco dei nodi contenuti nel percorso canonico del simbolo.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2. Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     Il gestore oggetti chiama questo metodo per ottenere l'elenco dei nodi contenuti nel percorso di presentazione del simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Procedura: Registrare una libreria con il gestore oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Procedura: Esporre gli elenchi dei simboli forniti dalla libreria al gestore degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
