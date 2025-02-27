---
title: Incorporamento di un diagramma in Windows Form | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 440b60697d4ab1e88f535b6c5ef824bc74e19c48
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068691"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Incorporamento di un diagramma in Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile incorporare un diagramma DSL in un controllo Windows, che viene visualizzata nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] finestra.  
  
## <a name="embedding-a-diagram"></a>Incorporamento di un diagramma  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Per incorporare un diagramma DSL in un controllo di Windows  
  
1. Aggiungere un nuovo **controllo utente** file al progetto DslPackage.  
  
2. Aggiungere un controllo Panel al controllo utente. Questo pannello conterrà il diagramma DSL.  
  
     Aggiungere altri controlli necessari.  
  
     Impostare le proprietà di ancoraggio dei controlli.  
  
3. In Esplora soluzioni fare doppio clic su file del controllo utente e fare clic su **Visualizza codice**. Aggiungere questo costruttore e una variabile per il codice:  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4. Aggiungere un nuovo file al progetto DslPackage, con il contenuto seguente:  
  
    ```  
    using System.Windows.Forms;  
    namespace Company.MyDSL  
    {  
      partial class MyDSLDocView  
      {  
        private UserControl1 container;  
        public override IWin32Window Window  
        {  
          get  
          {  
            if (container == null)  
            {  
              // Put our own form inside the DSL window:  
              container = new UserControl1(this,  
                (Control)base.Window);  
            }  
            return container;  
    } } } }  
  
    ```  
  
5. Per testare il linguaggio DSL, premere F5 e aprire un file di modello di esempio. Il diagramma viene visualizzato all'interno del controllo. Casella degli strumenti e altre funzionalità funzionano normalmente.  
  
#### <a name="updating-the-form-using-store-events"></a>Aggiornamenti del modulo usando gli eventi di Store  
  
1. In Progettazione Windows form, aggiungere un **ListBox** denominata `listBox1`. Verrà visualizzato un elenco degli elementi del modello. Verrà conservato nel synchronism con il modello usando *archiviare eventi*. Per altre informazioni, vedere [gestori di propagare le modifiche di fuori il modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2. Nel file di codice personalizzato, eseguire l'override ulteriormente metodi alla classe DocView:  
  
    ```  
  
    partial class MyDSLDocView  
    {  
     /// <summary>  
     /// Register store event listeners.  
     /// This method is called when the model and diagram    
     /// have completed loading.   
     /// </summary>  
     protected override bool LoadView()  
      {  
        bool result = base.LoadView();  
        Store store = this.DocData.Store;  
        EventManagerDirectory emd = store.EventManagerDirectory;  
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));  
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));  
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));  
  
        // Do the initial parts list:  
        container.SetUpFormFromModel();  
        return result;  
      }  
     /// <summary>  
     /// Listener method called on creation of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void AddElement(object sender, ElementAddedEventArgs e)  
     {  
       container.Add(e.ModelElement as ExampleElement);  
     }  
     /// <summary>  
     /// Listener method called after deletion of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void RemoveElement(object sender, ElementDeletedEventArgs e)  
     {  
       container.Remove(e.ModelElement as ExampleElement);  
     }  
  
    ```  
  
3. Nel code-behind del controllo utente, inserire i metodi per l'ascolto per gli elementi aggiunti e rimossi:  
  
    ```  
  
          public partial class UserControl1 : UserControl { ...  
  
    private ExampleModel modelRoot;  
  
    internal void Add(ExampleElement e) { UpdatePartsList(); }  
    internal void Remove(ExampleElement e) { UpdatePartsList(); }  
  
    internal void SetUpFormFromModel()  
    {  
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;  
      UpdatePartsList();  
    }  
  
    private void UpdatePartsList()  
    {  
      StringBuilder builder = new StringBuilder();  
      listBox1.Items.Clear();  
      foreach (ExampleElement c in modelRoot.Elements)  
      {  
        listBox1.Items.Add(c.Name);  
      }  
    }  
  
    ```  
  
4. Per testare il linguaggio DSL, premere F5 e nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aprire un file di modello di esempio.  
  
     Si noti che la casella di riepilogo Mostra un elenco degli elementi del modello e che sia corretto dopo qualsiasi aggiunta o eliminazione e dopo l'annullamento e ripristino.  
  
## <a name="see-also"></a>Vedere anche  
 [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
