---
title: Gestori di Modifica valore proprietà di dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
ms.assetid: 96d8f392-045e-4bc5-b165-fbaa470a3e16
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c8dac5a999b4f11fb066edfc1b1d4c057a999bae
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442983"
---
# <a name="domain-property-value-change-handlers"></a>Gestori di modifica del valore delle proprietà del dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un linguaggio specifico di dominio di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], quando il valore di una proprietà di dominio cambia, i metodi `OnValueChanging()` e `OnValueChanged()` vengono richiamati nel gestore delle proprietà di dominio. Per rispondere alla modifica, è possibile eseguire l'override di tali metodi.  
  
## <a name="overriding-the-property-handler-methods"></a>Override dei metodi del gestore delle proprietà   
 Ogni proprietà di dominio del linguaggio specifico di dominio è gestita da una classe annidata nella propria classe di dominio padre. Il nome segue il formato *PropertyName*Gestoreproprietà. È possibile esaminare questa classe di gestore di proprietà nel file **Dsl\Generated Code\DomainClasses.cs**. Nella classe `OnValueChanging()` viene chiamato immediatamente prima che il valore cambi, mentre `OnValueChanged()` immediatamente dopo.  
  
 Ad esempio, si supponga di avere una classe di dominio denominata `Comment` che include una proprietà di dominio stringa denominata `Text` e una proprietà integer denominata `TextLengthCount`. Per fare in modo `TextLengthCount` sempre per contenere la lunghezza del `Text` stringa, è possibile scrivere il codice seguente in un file separato nel progetto Dsl:  
  
```  
// Domain Class "Comment":  
public partial class Comment   
{  
  // Domain Property "Text":  
  partial class TextPropertyHandler  
  {  
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)  
    {  
      base.OnValueChanging(element, oldValue, newValue);  
  
      // To update values outside the Store, write code here.  
  
      // Let the transaction manager handle undo:  
      Store store = element.Store;  
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;  
  
      // Update values in the Store:  
      this.TextLengthCount = newValue.Length;  
    }  
  }  
}  
  
```  
  
 Notare gli aspetti seguenti sui gestori delle proprietà:  
  
- I metodi del gestore delle proprietà vengono chiamati sia quando l'utente apporta modifiche a una proprietà di dominio che quando il codice programma assegna un valore diverso alla proprietà.  
  
- I metodi vengono chiamati solo quando il valore viene effettivamente modificato. Il gestore non viene richiamato se il codice programma assegna un valore uguale al valore corrente.  
  
- Le proprietà calcolate e personalizzate del dominio di storage non dispongono di metodi OnValueChanged e OnValueChanging.  
  
- Non è possibile usare un gestore delle modifiche per modificare il nuovo valore. Per eseguire questa operazione, ad esempio al fine di limitare il valore a un intervallo specifico, definire un `ChangeRule`.  
  
- Non è possibile aggiungere un gestore delle modifiche a una proprietà che rappresenta un ruolo di una relazione. Definire invece un elemento `AddRule` e un elemento `DeleteRule` sulla classe relazione. Queste regole vengono attivate quando i collegamenti vengono creati o modificati. Per altre informazioni, vedere [le regole propagano le modifiche all'interno di the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
### <a name="changes-in-and-out-of-the-store"></a>Modifiche all'interno e all'esterno dell'archivio  
 I metodi del gestore delle proprietà vengono chiamati all'interno della transazione che ha iniziato la modifica. È quindi possibile apportare altre modifiche all'archivio senza aprire una nuova transazione. Le modifiche potrebbero determinare altre chiamate del gestore.  
  
 Quando una transazione viene annullata, riapplicata o ne viene eseguito il rollback, non devono essere operate modifiche nell'archivio, ossia modifiche a elementi di modello, relazioni, forme, connettori, diagrammi o alle relative proprietà.  
  
 Inoltre, i valori non vanno in genere aggiornati quando il modello viene caricato da file.  
  
 Le modifiche al modello devono quindi essere verificate da un test come il seguente:  
  
```  
if (!store.InUndoRedoOrRollback   
         && !store. InSerializationTransaction)  
{ this.TextLength = ...; // in-store changes   
}  
```  
  
 D'altra parte, se il gestore delle proprietà propaga le modifiche all'esterno dell'archivio, ad esempio in un file, in un database o in una variabile non di archivio, è necessario operare sempre tali modifiche in modo tale che i valori esterni vengano aggiornati quando l'utente richiama l'annullamento o il ripristino.  
  
### <a name="canceling-a-change"></a>Annullamento di una modifica  
 Se si vuole impedire una modifica, è possibile eseguire il rollback dell'ultima transazione. Si potrebbe ad esempio fare in modo che una proprietà resti compresa all'interno di un intervallo specifico.  
  
```  
if (newValue > 10)   
{ store.TransactionManager.CurrentTransaction.Rollback();  
  System.Windows.Forms.MessageBox.Show("Value must be less than 10");  
}  
  
```  
  
### <a name="alternative-technique-calculated-properties"></a>Tecnica alternativa: Proprietà calcolata  
 Nell'esempio precedente viene illustrato come usare OnValueChanged() per propagare valori da una proprietà di dominio a un'altra. Ogni proprietà presenta il proprio valore archiviato.  
  
 In alternativa, si potrebbe definire la proprietà derivata come proprietà calcolata. In questo caso la proprietà non dispone di archiviazione propria e la sua funzione di definizione viene valutata ogni volta che è necessario il relativo valore. Per altre informazioni, vedere [calcolate e le proprietà di archiviazione personalizzate](../modeling/calculated-and-custom-storage-properties.md).  
  
 Invece dell'esempio precedente, è possibile impostare il **tipo** campo `TextLengthCount` essere **Calculated** nella definizione DSL. È necessario fornire il proprio **ottenere** metodo per questa proprietà di dominio. Il **ottenere** metodo restituirebbe la lunghezza corrente del `Text` stringa.  
  
 Un potenziale svantaggio dell'uso di proprietà calcolate, tuttavia, è il fatto che l'espressione viene valutata ogni volta che viene usato il valore, il che potrebbe dare luogo a problemi di prestazioni. In una proprietà calcolata, inoltre, non sono presenti elementi OnValueChanging() e OnValueChanged().  
  
### <a name="alternative-technique-change-rules"></a>Tecnica alternativa: Regole di modifica  
 Se si definisce una regola ChangeRule, questa verrà eseguita al termine di una transazione in cui il valore di una proprietà viene modificato.  Per altre informazioni, vedere [le regole propagano le modifiche all'interno di the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Se in una transazione sono presenti numerose modifiche, la regola ChangeRule verrà eseguita dopo che queste sono state tutte applicate. Al contrario, il OnValue... i metodi vengono eseguiti quando alcune delle modifiche non sono state completate. A seconda del risultato che si intende raggiungere, la scelta di una regola ChangeRule potrebbe risultare più appropriata.  
  
 È anche possibile usare una regola ChangeRule per regolare il nuovo valore della proprietà per contenerlo entro un intervallo specificato.  
  
> [!WARNING]
> Se una regola opera modifiche al contenuto dell'archivio, potrebbe verificarsi l'attivazione di altre regole e gestori delle proprietà. Se una regola modifica la proprietà che ne ha determinato l'attivazione, verrà chiamata nuovamente. È necessario assicurarsi che le definizioni delle regole non risultino in attivazioni senza termine.  
  
```  
using Microsoft.VisualStudio.Modeling;   
...  
// Change rule on the domain class Comment:  
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]   
class MyCommentTrimRule : ChangeRule  
{  
  public override void   
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
  {  
    base.ElementPropertyChanged(e);  
    Comment comment = e.ModelElement as Comment;  
  
    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))  
      comment.Text = comment.Text.Trim();  
    // If changed, rule will trigger again.  
  }  
}  
  
// Register the rule:   
public partial class MyDomainModel   
{  
 protected override Type[] GetCustomDomainModelTypes()   
 { return new Type[] { typeof(MyCommentTrimRule) };   
 }  
}  
  
```  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente viene eseguito l'override del gestore delle proprietà di una proprietà di dominio e viene inviata notifica all'utente quando una proprietà per la classe di dominio `ExampleElement` viene modificata.  
  
### <a name="code"></a>Codice  
  
```  
using DslModeling = global::Microsoft.VisualStudio.Modeling;  
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;  
  
namespace msft.FieldChangeSample  
{  
  public partial class ExampleElement  
  {  
    internal sealed partial class NamePropertyHandler  
    {  
      protected override void OnValueChanged(ExampleElement element,  
         string oldValue, string newValue)  
      {  
        if (!this.Store.InUndoRedoOrRollback)  
        {  
           // make in-store changes here...  
        }  
        // This part is called even in undo:  
        System.Windows.Forms.MessageBox.Show("Value Has Changed");  
        base.OnValueChanged(element, oldValue, newValue);  
      }  
    }  
  }  
}  
```  
