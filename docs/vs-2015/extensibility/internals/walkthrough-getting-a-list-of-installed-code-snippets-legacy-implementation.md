---
title: 'Procedura dettagliata: Come ottenere un elenco di installato i frammenti di codice (implementazione Legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 256430c0e41bfc0452282c89407335d997cc715c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440762"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Procedura dettagliata: Recupero di un elenco di frammenti di codice installati (implementazione legacy)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un frammento di codice è un frammento di codice che può essere inserito nel buffer di origine con un comando di menu (che consente di scegliere tra un elenco di frammenti di codice installati) o tramite la selezione di un collegamento al frammento da un elenco di completamento IntelliSense.  
  
 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> metodo ottiene tutti i frammenti di codice per un linguaggio specifico di GUID. I tasti di scelta rapida per i frammenti di codice possono essere inseriti in un elenco di completamento IntelliSense.  
  
 Visualizzare [supporto per i frammenti di codice in un servizio di linguaggio Legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) per informazioni dettagliate sull'implementazione di frammenti di codice in un servizio di linguaggio managed package framework (MPF).  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Per recuperare un elenco di frammenti di codice  
  
1. Il codice seguente viene illustrato come ottenere un elenco di frammenti di codice per una determinata lingua. I risultati vengono archiviati in una matrice di <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> strutture. Questo metodo Usa il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo per ottenere il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> dell'interfaccia dal <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> servizio. Tuttavia, è possibile usare anche il provider di servizi dato per il pacchetto VSPackage e chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> (metodo).  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>Per chiamare il metodo GetSnippets  
  
1. Il metodo seguente viene illustrato come chiamare il `GetSnippets` metodo al completamento di un'operazione di analisi. Il <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> metodo viene chiamato dopo un'operazione di analisi che è stata avviata con il motivo <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
> Il `expansionsList` listis memorizzato nella cache per motivi di prestazioni della matrice. Per i frammenti di codice non vengono riflesse nell'elenco fino a quando non viene arrestato e ricaricare il servizio di linguaggio (ad esempio, per arrestare e riavviare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]).  
  
```csharp  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>Usare le informazioni sul frammento di codice  
  
1. Il codice seguente viene illustrato come utilizzare le informazioni di frammento di codice restituite dal `GetSnippets` (metodo). Il `AddSnippets` viene chiamato dal parser in risposta a un qualsiasi motivo di analisi che consente di popolare un elenco di frammenti di codice. Questa operazione deve essere eseguita dopo che è stato eseguito l'analisi completa per la prima volta.  
  
     Il `AddDeclaration` metodo compila un elenco di dichiarazioni che in un secondo momento viene visualizzato in un elenco di completamento.  
  
     Il `TestDeclaration` classe contiene tutte le informazioni che possono essere visualizzate in un elenco di completamento, nonché il tipo di dichiarazione.  
  
    ```csharp  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto per i frammenti di codice in un servizio di linguaggio legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
