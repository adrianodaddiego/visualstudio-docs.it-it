---
title: Estendere il DSL mediante MEF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 3e7be79a-53ab-4d79-863a-bef8d27839bd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be514104ebc3cd908cd9469c6b674a22f9dad401
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696192"
---
# <a name="extend-your-dsl-by-using-mef"></a>Estendere il DSL mediante MEF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile estendere il linguaggio specifico di dominio (DSL) mediante Managed Extensibility Framework (MEF). Utente o altri sviluppatori sarà in grado di scrivere le estensioni per il DSL senza modificare il codice del programma e definizione DSL. Tali estensioni includono comandi di menu, gestori di trascinamento e rilascio e la convalida. Gli utenti saranno in grado di installare il linguaggio DSL e, facoltativamente, installare le estensioni per tale.  
  
 Inoltre, quando si abilita MEF nel linguaggio DSL, potrebbe risultare più semplice per la scrittura di alcune delle funzionalità del linguaggio DSL, anche se sono tutti compilati con il linguaggio DSL.  
  
 Per altre informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Per abilitare il linguaggio DSL da parte MEF  
  
1. Creare una nuova cartella denominata **MefExtension** all'interno di **DslPackage** progetto. Aggiungere i file seguenti:  
  
    Nome file: `CommandExtensionVSCT.tt`  
  
   > [!IMPORTANT]
   > Il GUID del set in questo file per essere quella di CommandSetId il GUID definito in DslPackage\GeneratedCode\Constants.tt  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#  
   // CmdSet Guid must be defined before master template is included  
   // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt  
   Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");  
   string menuidCommandsExtensionBaseId="0x4000";  
   #>  
   <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>  
   ```  
  
    Nome file: `CommandExtensionRegistrar.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>  
   ```  
  
    Nome file: `ValidationExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>  
   ```  
  
    Nome file: `ValidationExtensionRegistrar.tt`  
  
    Se si aggiunge questo file, è necessario abilitare la convalida nel linguaggio DSL con almeno una delle opzioni **EditorValidation** in DSL Explorer.  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>  
   ```  
  
    Nome file: `PackageExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>  
   ```  
  
2. Creare una nuova cartella denominata **MefExtension** all'interno di **Dsl** progetto. Aggiungere i file seguenti:  
  
    Nome file: `DesignerExtensionMetaDataAttribute.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>  
   ```  
  
    Nome file: `GestureExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="Dsl\GestureExtensionEnablement.tt" #>  
   ```  
  
    Nome file: `GestureExtensionController.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="Dsl\GestureExtensionController.tt" #>  
   ```  
  
3. Aggiungere la riga seguente al file esistente denominato **Dslpackage\commands.vsct.** :  
  
   ```  
   <Include href="MefExtension\CommandExtensionVSCT.vsct"/>  
   ```  
  
    Inserire la riga alla fine dell'istruzione `<Include>` direttiva.  
  
4. `Open DslDefinition.dsl.`  
  
5. In Esplora DSL, selezionare **editor\convalida**.  
  
6. Nella finestra Proprietà, assicurarsi che almeno una delle proprietà denominato **Usa...**  è `true`.  
  
7. Sulla barra degli strumenti Esplora soluzioni, fare clic su **Trasforma tutti i modelli**.  
  
    File sussidiari vengono visualizzati di sotto di ogni file aggiunto.  
  
8. Compilare ed eseguire la soluzione per verificare che sia ancora funzionante.  
  
   Il linguaggio DSL è ora abilitata per il framework MEF. È possibile scrivere i comandi di menu, gestori di movimenti e vincoli di convalida come estensioni MEF. È possibile scrivere queste estensioni alla soluzione DSL insieme ad altro codice personalizzato. Inoltre, utente o altri sviluppatori possono scrivere separato [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensioni che estendono il linguaggio DSL.  
  
## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>Creazione di un'estensione per un DSL MEF-abilitata  
 Se si ha accesso a un DSL abilitati MEF creato dall'utente o un altro utente, è possibile scrivere le estensioni per tale. Le estensioni sono utilizzabile per aggiungere i comandi di menu e gestori movimenti o i vincoli di convalida. Per creare queste estensioni, si utilizza un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soluzione Extension (VSIX). La soluzione è costituito da due parti: un progetto di libreria di classi che compila l'assembly di codice e un progetto VSIX per creare l'assembly.  
  
#### <a name="to-create-a-dsl-extension-vsix"></a>Per creare una DSL estensione VSIX  
  
1. Creare un nuovo progetto Libreria di classi. A questo scopo, nella **nuovo progetto** finestra di dialogo **Visual Basic** oppure **Visual c#** e quindi selezionare **libreria di classi**.  
  
2. Nel nuovo progetto di libreria di classi, aggiungere un riferimento all'assembly del linguaggio DSL.  
  
   - Questo assembly è in genere un nome che termina con ". DSL.dll".  
  
   - Se si ha accesso al progetto DSL, è possibile trovare il file di assembly nella directory **Dsl\bin\\\\** *  
  
   - Se si ha accesso al file VSIX DSL, è possibile trovare l'assembly modificando l'estensione del file VSIX in "ZIP". Decomprimere il file con estensione zip.  
  
3. Aggiungere riferimenti agli assembly .NET seguenti:  
  
   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll  
  
   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll  
  
   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll  
  
   - System.ComponentModel.Composition.dll  
  
   - System.Windows.Forms.dll  
  
4. Creare un progetto VSIX nella stessa soluzione. A questo scopo, nella **nuovo progetto** finestra di dialogo, espandere **Visual Basic** oppure **Visual c#** , fare clic su **estendibilità**e quindi scegliere  **Progetto VSIX**.  
  
5. In Esplora soluzioni fare doppio clic su progetto VSIX e quindi fare clic su **imposta come progetto di avvio**.  
  
6. Nel nuovo progetto, aprire **vsixmanifest**.  
  
7. Fare clic su **aggiungere contenuto**. Nella finestra di dialogo, impostare **tipo di contenuto** al **componente MEF**, e **progetto Source** al progetto libreria di classi.  
  
8. Aggiungere un riferimento di progetto VSIX per il linguaggio DSL.  
  
   1. Nelle **vsixmanifest**, fare clic su **Aggiungi riferimento**  
  
   2. Nella finestra di dialogo, fare clic su **Payload aggiungere** e quindi individuare il file VSIX del linguaggio DSL. Il file VSIX viene compilato nella soluzione di DSL in * * DslPackage\bin\\\\* * *.  
  
       Ciò consente agli utenti di installare il linguaggio DSL e l'estensione nello stesso momento. Se l'utente ha già installato il linguaggio DSL, solo l'estensione verrà installata.  
  
9. Rivedere e aggiornare gli altri campi d' **vsixmanifest**. Fare clic su **Seleziona versioni** e verificare che i valori corretti [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edizioni sono impostate.  
  
10. Aggiungere codice al progetto libreria di classi. Usare gli esempi nella sezione seguente come guida.  
  
     È possibile aggiungere qualsiasi numero di comandi, movimenti e le classi di convalida.  
  
11. Per testare l'estensione, premere **F5**. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], creare o aprire un file di esempio del linguaggio DSL.  
  
## <a name="writing-mef-extensions-for-dsls"></a>Scrittura di estensioni MEF per linguaggi specifici di dominio  
 È possibile scrivere le estensioni nel progetto di codice assembly di una soluzione di estensione DSL separata. È anche possibile usare MEF nel progetto DslPackage come un modo pratico per scrivere i comandi, movimenti e codice di convalida come parte del linguaggio DSL.  
  
### <a name="menu-commands"></a>Comandi di menu  
 Per scrivere un comando di menu, definire una classe che implementa <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> e la classe con l'attributo definito nel linguaggio DSL, denominato del prefisso *Dslutente*`CommandExtension`. È possibile scrivere più di una classe di comando di menu.  
  
 `QueryStatus()` viene chiamato ogni volta che l'utente fa clic nel diagramma. Deve esaminare la selezione corrente e impostare `command.Enabled` per indicare quando il comando è applicabile.  
  
```  
using System.ComponentModel.Composition;  
using System.Linq;  
using Company.MyDsl; // My DSL  
using Company.MyDsl.ExtensionEnablement; // My DSL  
using Microsoft.VisualStudio.Modeling; // Transactions  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension  
  
namespace MyMefExtension  
{  
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:  
  [MyDslCommandExtension]   
  public class MyCommandClass : ICommandExtension  
  {   
    /// <summary>  
    /// Provides access to current document and selection.  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Called when the user selects this command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      // Transaction is required if you want to update elements.  
      using (Transaction t = SelectionContext.CurrentStore  
              .TransactionManager.BeginTransaction("fix names"))  
      {  
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)  
        {  
          ExampleElement element = shape.ModelElement as ExampleElement;  
          element.Name = element.Name + " !";  
        }  
        t.Commit();  
      }  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks the diagram.  
    /// Determines whether the command should appear.  
    /// This method should set command.Enabled and command.Visible.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled =  
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks the diagram.  
    /// Determines the text of the command in the menu.  
    /// </summary>  
    public string Text  
    {  
      get { return "My menu command"; }  
    }  
  }  
}  
  
```  
  
### <a name="gesture-handlers"></a>Gestori di movimento  
 Un gestore movimenti possa gestire gli oggetti trascinati nel diagramma da qualsiasi luogo, interne o esterne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Nell'esempio seguente consente all'utente di trascinare i file da Esplora risorse di Windows nel diagramma. Crea gli elementi che contengono i nomi dei file.  
  
 È possibile scrivere gestori eventi per gestire con il trascinamento da altri modelli di linguaggio specifico di dominio e i modelli UML. Per altre informazioni, vedere [Procedura: Aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
```  
  
using System.ComponentModel.Composition;  
using System.Linq;  
using Company.MyDsl;  
using Company.MyDsl.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling; // Transactions  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;   
  
namespace MefExtension  
{  
  [MyDslGestureExtension]  
  class MyGestureExtension : IGestureExtension  
  {  
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
    {  
      System.Windows.Forms.MessageBox.Show("double click!");  
    }  
  
    /// <summary>  
    /// Called when the user drags anything over the diagram.  
    /// Return true if the dragged object can be dropped on the current target.  
    /// </summary>  
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>  
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>  
    /// <returns></returns>  
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)  
    {  
      // This handler only allows items to be dropped onto the diagram:  
      return targetMergeElement is MefDsl2Diagram &&  
      // And only accepts files dragged from Windows Explorer:  
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");  
    }  
  
    /// <summary>  
    /// Called when the user drops an item onto the diagram.  
    /// </summary>  
    /// <param name="targetDropElement"></param>  
    /// <param name="diagramDragEventArgs"></param>  
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
    {  
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;  
      if (diagram == null) return;  
  
      // This handler only accepts files dragged from Windows Explorer:  
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];  
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;   
  
      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))  
      {  
        // Create an element to represent each file:  
        foreach (string fileName in draggedFileNames)  
        {  
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);  
          element.Name = fileName;  
  
          // This method of adding the new element allows the position  
          // of the shape to be specified:            
          ElementGroup group = new ElementGroup(element);  
          diagram.ElementOperations.MergeElementGroupPrototype(  
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));  
        }  
        t.Commit();  
      }  
    }  
  }  
}  
  
```  
  
### <a name="validation-constraints"></a>Vincoli di convalida  
 Metodi di convalida sono contrassegnati con il `ValidationExtension` attributo generato dal linguaggio DSL e anche da <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Il metodo può apparire in qualsiasi classe che non è contrassegnato da un attributo.  
  
 Per altre informazioni, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
```  
using Company.MyDsl;  
using Company.MyDsl.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.Validation;  
  
namespace MefExtension  
{  
  class MyValidationExtension // Can be any class.  
  {  
    // SAMPLE VALIDATION METHOD.  
    // All validation methods have the following attributes.  
  
    // Specific to the extended DSL:  
    [MyDslValidationExtension]   
  
    // Determines when validation is applied:  
    [ValidationMethod(  
       ValidationCategories.Save  
     | ValidationCategories.Open  
     | ValidationCategories.Menu)]  
  
    /// <summary>  
    /// When validation is executed, this method is invoked  
    /// for every element in the model that is an instance  
    /// of the second parameter type.  
    /// </summary>  
    /// <param name="context">For reporting errors</param>  
    /// <param name="elementToValidate"></param>  
    private void ValidateClassNames  
      (ValidationContext context,  
       // Type determines to what elements this will be applied:  
       ExampleElement elementToValidate)  
    {   
      // Write code here to test values and links.  
      if (elementToValidate.Name.IndexOf(' ') >= 0)  
      {  
        // Log any unacceptable values:  
        context.LogError(  
          // Description:  
          "Name must not contain spaces"   
          // Error code unique to this type of error:  
          , "MyDsl001"   
          // Element to highlight when user double-clicks error:  
          , elementToValidate);   
} } } }  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Visual Studio di spedizione](../extensibility/shipping-visual-studio-extensions.md)   
 [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)   
 [Procedura: Aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)
