---
title: Estendere il filtro di Esplora soluzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 687663a79ea5dca75da68013519f4652fa71460c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110570"
---
# <a name="extending-the-solution-explorer-filter"></a>Estensione del filtro di Esplora soluzioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile estendere **Esplora soluzioni** filtrare la funzionalità per mostrare o nascondere file diversi. Ad esempio, è possibile creare un filtro che mostra solo classi factory file c# la **Esplora soluzioni**, come illustrato di seguito in questa procedura dettagliata.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="create-a-visual-studio-package-project"></a>Creare un progetto di pacchetto di Visual Studio  
  
1. Creare un progetto VSIX denominato `FileFilter`. Aggiungere un modello di elemento di comando personalizzato denominato **FileFilter**. Per altre informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Aggiungere un riferimento a `System.ComponentModel.Composition` e `Microsoft.VisualStudio.Utilities`.  
  
3. Visualizzazione del comando di menu sul **Esplora soluzioni** sulla barra degli strumenti. Aprire il file FileFilterPackage.vsct.  
  
4. Modifica il `<Button>` blocco alla seguente:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### <a name="update-the-manifest-file"></a>Aggiornare il File manifesto  
  
1. Nel file vsixmanifest, aggiungere un asset è un componente MEF.  
  
2. Nel **asset** scheda, scegliere il **New** pulsante.  
  
3. Nel **tipo** campo, scegliere **MEFComponent**.  
  
4. Nel **origine** campo, scegliere **un progetto nella soluzione corrente**.  
  
5. Nel **progetto** campo, scegliere **FileFilter**, quindi scegliere il **OK** pulsante.  
  
### <a name="add-the-filter-code"></a>Aggiungere il codice di filtro  
  
1. Aggiungere alcuni GUID nel file FileFilterPackageGuids.cs:  
  
    ```csharp  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2. Aggiungere un file di classe al progetto FileFilter denominato FileNameFilter.cs.  
  
3. Sostituire lo spazio dei nomi vuoto e la classe vuota con il codice seguente.  
  
     Il `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` metodo accetta la raccolta che contiene la radice della soluzione (`rootItems`) e restituisce la raccolta di elementi da includere nel filtro.  
  
     Il `ShouldIncludeInFilter` metodo filtra gli elementi di **Esplora soluzioni** gerarchia in base a condizione che si specifica.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Text.RegularExpressions;  
    using System.Threading.Tasks;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
  
    namespace FileFilter  
    {  
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component  
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]  
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider  
        {  
            SVsServiceProvider svcProvider;  
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
            // Constructor required for MEF composition  
            [ImportingConstructor]  
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)  
            {  
                this.svcProvider = serviceProvider;  
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
            }  
  
            // Returns an instance of Create filter class.  
            protected override HierarchyTreeFilter CreateFilter()  
            {  
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);  
            }  
  
            // Regex pattern for CSharp factory classes  
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";  
  
            // Implementation of file filtering  
            private sealed class FileNameFilter : HierarchyTreeFilter  
            {  
                private readonly Regex regexp;  
                private readonly IServiceProvider svcProvider;  
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
                public FileNameFilter(  
                    IServiceProvider serviceProvider,  
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,  
                    string fileNamePattern)  
                {  
                    this.svcProvider = serviceProvider;  
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);  
                }  
  
                // Gets the items to be included from this filter provider.   
                // rootItems is a collection that contains the root of your solution  
                // Returns a collection of items to be included as part of the filter  
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)  
                {  
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);  
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;  
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(  
                                        root.HierarchyIdentity.NestedHierarchy,  
                                        CancellationToken);  
  
                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(  
                        sourceItems,  
                        ShouldIncludeInFilter,  
                        CancellationToken);  
                    return includedItems;  
                }  
  
                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>  
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)  
                {  
                    if (hierarchyItem == null)  
                    {  
                        return false;  
                    }  
                    return this.regexp.IsMatch(hierarchyItem.Text);  
                }  
            }  
        }  
    }  
  
    ```  
  
4. In FileFilter.cs, rimuovere il codice di posizionamento e la gestione del comando dal costruttore FileFilter. Il risultato dovrebbe essere simile al seguente:  
  
    ```csharp  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     Rimuovere anche il metodo ShowMessageBox().  
  
5. In FileFilterPackage, cs, sostituire il codice nel metodo Initialize () con gli elementi seguenti:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>Testare il codice  
  
1. Compilare ed eseguire il progetto. Verrà visualizzata una seconda istanza di Visual Studio. Ciò è chiamata istanza sperimentale.  
  
2. Nell'istanza sperimentale di Visual Studio, aprire un progetto c#.  
  
3. Cercare il pulsante che è stato aggiunto nella barra degli strumenti Esplora soluzioni. Deve essere il quarto pulsante da sinistra.  
  
4. Quando si fa clic sul pulsante, tutti i file devono essere filtrati e dovrebbe essere "tutti gli elementi sono stati filtrati dalla visualizzazione". in Esplora soluzioni.
