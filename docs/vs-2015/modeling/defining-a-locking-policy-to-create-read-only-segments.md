---
title: La definizione di un criterio di blocco per creare segmenti di sola lettura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6044e9c47a0dcbc95fd1503906cbd81ac8e44526
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422648"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definizione di un criterio di blocco per creare segmenti di sola lettura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'API di immutabilità del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK consente a un programma di blocco o parte di un modello di linguaggio specifico di dominio (DSL) in modo che è possibile leggere ma non modificato. Questa opzione di sola lettura, ad esempio, potrebbe essere usata in modo che un utente può chiedere i colleghi per aggiungere annotazioni e rivedere un modello DSL ma è possibile impedire loro di modificare l'originale.  
  
 Inoltre, l'autore di un linguaggio DSL, è possibile definire un *criteri blocco.* Un criterio di blocco definisce stabilisce quali blocchi sono consentite, non consentito o obbligatorio. Ad esempio, quando si pubblica un linguaggio DSL, è possibile incoraggiare gli sviluppatori di terze parti per estendere la soluzione con i nuovi comandi. Ma è anche possibile usare un criterio di blocco per impedire che modifica lo stato di sola lettura di parti specificate del modello.  
  
> [!NOTE]
> Un criterio di blocco può essere aggirato mediante l'uso della reflection. Fornisce un limite chiaro per gli sviluppatori di terze parti, ma non offrono sicurezza avanzata.  
  
 Altre informazioni ed esempi sono disponibili nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128) sito Web.  
  
## <a name="setting-and-getting-locks"></a>Impostazione e recupero di blocchi  
 È possibile impostare i blocchi nell'archivio, in una partizione o in un singolo elemento. Ad esempio, questa istruzione sarà impediscono l'eliminazione di un elemento del modello e anche impedirà le relative proprietà da modificare:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Altri valori di blocco sono utilizzabile per impedire modifiche nelle relazioni, la creazione dell'elemento, lo spostamento tra le partizioni e i collegamenti di ordinamento nuovamente in un ruolo.  
  
 I blocchi vengono applicate sia alle azioni dell'utente che il codice del programma. Se il codice del programma tenta di apportare una modifica, un `InvalidOperationException` verrà generata. I blocchi vengono ignorati in un'operazione di annullamento o ripristino.  
  
 È possibile individuare se un elemento dispone di un qualsiasi blocco di un set specifico utilizzando `IsLocked(Locks)` ed è possibile ottenere il set corrente di blocchi su un elemento usando `GetLocks()`.  
  
 È possibile impostare un blocco senza usare una transazione. Il database di blocco non è parte dell'archivio. Se si imposta un blocco in risposta a una modifica di un valore nell'archivio, ad esempio in OnValueChanged, è consigliabile consentire le modifiche che fanno parte di un'operazione di annullamento.  
  
 Questi metodi sono metodi di estensione definiti nel <xref:Microsoft.VisualStudio.Modeling.Immutability> dello spazio dei nomi.  
  
### <a name="locks-on-partitions-and-stores"></a>Blocchi su partizioni e archivi  
 I blocchi è applicabile anche per le partizioni e l'archivio. Un blocco che è impostato su una partizione si applica a tutti gli elementi nella partizione. Pertanto, ad esempio, l'istruzione seguente, potrà tutti gli elementi in una partizione in corso l'eliminazione, indipendentemente dal fatto gli stati dei propri blocchi. Tuttavia, altri blocchi, ad esempio `Locks.Property` potrebbe ancora essere impostato su singoli elementi:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Un blocco che è nastavit la Store si applica a tutti i relativi elementi, indipendentemente dalle impostazioni di tale blocco su partizioni e gli elementi.  
  
### <a name="using-locks"></a>L'utilizzo dei blocchi  
 È possibile usare i blocchi per implementare schemi come negli esempi seguenti:  
  
- Non consentire le modifiche apportate a tutti gli elementi e relazioni ad eccezione di quelli che rappresentano i commenti. Ciò consente agli utenti di aggiungere annotazioni di un modello senza modificarlo.  
  
- Impedire modifiche nella partizione predefinita, ma consentire modifiche della partizione del diagramma. L'utente è possibile ridisporre il diagramma, ma non è possibile modificare il modello sottostante.  
  
- Impedisce le modifiche alla Store, ad eccezione di un gruppo di utenti che sono registrati in un database separato. Per altri utenti, il diagramma e il modello sono di sola lettura.  
  
- Impedire modifiche al modello se una proprietà Boolean del diagramma è impostata su true. Specificare un comando di menu per modificare tale proprietà. In tal modo gli utenti che non hanno modificato accidentalmente.  
  
- Non consentire l'aggiunta e l'eliminazione di elementi e relazioni di particolari classi, ma consentire modifiche alle proprietà. Ciò fornisce agli utenti con un modulo predefinito in cui possono specificare le proprietà.  
  
## <a name="lock-values"></a>Valori di blocco  
 I blocchi possono essere impostati su una Store, la partizione o singoli ModelElement. Blocchi è un `Flags` enumerazione: è possibile combinare i relativi valori tramite '&#124;'.  
  
- I blocchi di un oggetto ModelElement includono sempre i blocchi della relativa partizione.  
  
- I blocchi di una partizione includono sempre i blocchi del Store.  
  
  È possibile impostare un blocco su una partizione o archiviare e allo stesso tempo disabilitare il blocco su un singolo elemento.  
  
|Value|Vale a dire se `IsLocked(Value)` è true|  
|-----------|------------------------------------------|  
|nessuno|Nessuna restrizione.|  
|Proprietà|Impossibile modificare le proprietà di dominio degli elementi. Ciò non è applicabile alle proprietà che vengono generate dal ruolo di una classe di dominio in una relazione.|  
|Aggiunta|Non è possibile creare nuovi elementi e collegamenti in una partizione o l'archiviazione.<br /><br /> Non applicabile a `ModelElement`.|  
|Move|Elemento non può essere spostato tra le partizioni se `element.IsLocked(Move)` è true, o se `targetPartition.IsLocked(Move)` è true.|  
|Eliminare|Un elemento non può essere eliminato se questo blocco è impostato sull'elemento stesso o in uno qualsiasi degli elementi a cui verrebbe propagare l'eliminazione, quali forme e gli elementi incorporati.<br /><br /> È possibile usare `element.CanDelete()` per individuare se un elemento può essere eliminato.|  
|Riordinare|L'ordine dei collegamenti a un assegnatario di ruolo non può essere modificato.|  
|RolePlayer|Il set di collegamenti che hanno origine in questo elemento non può essere modificato. Ad esempio, nuovi elementi non possono essere incorporati sotto questo elemento. Questa operazione non influenza i collegamenti per il quale questo elemento è la destinazione.<br /><br /> Se questo elemento è un collegamento, l'origine e destinazione non sono interessate.|  
|Tutti|OR bit per bit degli altri valori.|  
  
## <a name="locking-policies"></a>Criteri di blocchi  
 L'autore di un linguaggio DSL, è possibile definire un *criteri blocco*. Un criterio di blocco Modera il funzionamento di SetLocks(), in modo che è possibile impedire che i blocchi specifici da impostare o implica che è necessario impostare blocchi specifici. In genere, si utilizzerebbe un criterio di blocco per impedire agli utenti o agli sviluppatori da violino accidentalmente l'utilizzo previsto di un linguaggio DSL, in modo che è possibile dichiarare una variabile `private`.  
  
 È anche possibile usare un criterio di blocco per impostare i blocchi su tutti gli elementi dipende dal tipo dell'elemento. Infatti, `SetLocks(Locks.None)` viene sempre chiamato quando un elemento viene innanzitutto creato o deserializzato dal file.  
  
 Tuttavia, è possibile utilizzare un criterio per variare i blocchi su un elemento durante la sua vita. A tale scopo, è consigliabile usare le chiamate a `SetLocks()`.  
  
 Per definire un criterio di blocco, è necessario:  
  
- Creare una classe che implementi <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
- Aggiungere questa classe per i servizi disponibili tramite l'oggetto DocData del linguaggio DSL.  
  
### <a name="to-define-a-locking-policy"></a>Per definire un criterio di blocco  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> presenta la seguente definizione:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Questi metodi vengono chiamati quando viene effettuata una chiamata a `SetLocks()` su una Store, una partizione o un ModelElement. In ogni metodo, viene fornito un set di blocchi proposto. È possibile restituire il set di proposto oppure è possibile aggiungere o sottrarre i blocchi.  
  
 Ad esempio:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 Per assicurarsi che gli utenti possono sempre eliminare elementi, anche se le chiamate ad altro codice `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Per impedire modifiche in tutte le proprietà di ciascun elemento di MyClass:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>Per rendere i criteri disponibili come servizio  
 Nel `DslPackage` del progetto, aggiungere un nuovo file contenente codice simile al seguente:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```
