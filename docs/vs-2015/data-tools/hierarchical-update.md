---
title: Aggiornamento gerarchico | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 521f878c9d4fafa61f8c717f4c9752622ef339d9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699804"
---
# <a name="hierarchical-update"></a>Aggiornamento gerarchico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aggiornamento gerarchico * si riferisce al processo di salvataggio dei dati aggiornati (da un set di dati con due o più tabelle correlate) in un database, mantenendo le regole di integrità referenziale. *L'integrità referenziale* fa riferimento a regole di coerenza fornite tramite i vincoli in un database che controllano il comportamento di inserimento, aggiornamento ed eliminazione dei record correlati. È ad esempio, l'integrità referenziale che impone la creazione di un record del cliente prima di consentire gli ordini da creare per quel cliente.  Per altre informazioni sulle relazioni nei set di dati, vedere [relazioni nei DataSet](../data-tools/relationships-in-datasets.md)  
  
 La funzionalità di aggiornamento gerarchico Usa una `TableAdapterManager` per gestire il `TableAdapter`s in un dataset tipizzato. Il `TableAdapterManager` componente è un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-generato (classe), pertanto non è in parte il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Quando si trascina una tabella dalla finestra Origini dei dati in un Windows Form o nella pagina WPF, Visual Studio aggiunge una variabile di tipo TableAdapterManager al form o nella pagina e visualizzarlo nella finestra di progettazione nella barra dei componenti. Per informazioni dettagliate sul `TableAdapterManager` classe, vedere la sezione riferimento TableAdapterManager [Panoramica di TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
 Per impostazione predefinita, un set di dati considerati tabelle correlate ", solo le relazioni" che significa che non imporre vincoli di chiave esterna. È possibile modificare tale impostazione in fase di progettazione tramite Progettazione Dataset. Selezionare la linea di relazione tra due tabelle per visualizzare il **relazione** nella finestra di dialogo. Le modifiche apportate qui determinerà il componente TableAdapterManager comportamento quando invia le modifiche nelle tabelle correlate nel database.  
  
## <a name="enablehierarchical-update-in-a-dataset"></a>Aggiornamento Enablehierarchical in un set di dati  
 Per impostazione predefinita, l'aggiornamento gerarchico è abilitato per tutti i nuovi set di dati che vengono aggiunti o creati in un progetto. Attivare o disattivare l'aggiornamento gerarchico impostando il **aggiornamento gerarchico** proprietà di un dataset tipizzato in Progettazione DataSet per **True** oppure **False**:  
  
 ![Impostazione di aggiornamento gerarchico](../data-tools/media/hierarchical-update-setting.png "impostazione aggiornamento gerarchico")  
  
## <a name="create-a-new-relation-between-tables"></a>Creare una nuova relazione tra tabelle  
 Per creare una nuova relazione tra due tabelle, nella finestra di progettazione set di dati, selezionare la barra del titolo di ogni tabella, quindi fare doppio clic e selezionare**aggiungere una relazione**.  
  
 ![Aggiornamento gerarchico aggiungere menu relazione](../data-tools/media/hierarchical-update-add-relation-menu.png "aggiornamento gerarchico aggiungere menu relazione")  
  
## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Comprendere i vincoli foreign key, propagazione degli aggiornamenti ed eliminazioni  
 È importante comprendere i vincoli come chiave esterna e il comportamento a catena nel database vengono creati nel codice di set di dati generato.  
  
 Per impostazione predefinita, le tabelle di dati in un set di dati vengono generate con relazioni (<xref:System.Data.DataRelation>) che corrispondono alle relazioni nel database. Tuttavia, la relazione del set di dati non viene generata come vincolo di chiave esterna. Il <xref:System.Data.DataRelation> configurato come **solo relazione** senza <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> o <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> in vigore.  
  
 Per impostazione predefinita, gli aggiornamenti a catena e le eliminazioni sono state disabilitate anche se la relazione di database è impostata con gli aggiornamenti a catena e/o le eliminazioni a catena attivata. Creazione di un nuovo cliente e un nuovo ordine e quindi si tenta di salvare i dati, ad esempio, può provocare un conflitto con i vincoli di chiave esterna che sono definiti nel database. Per altre informazioni, vedere [Procedura: Configurare i vincoli Foreign Key in un set di dati](https://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e).  
  
## <a name="set-the-order-to-perform-updates"></a>Impostare l'ordine di esecuzione degli aggiornamenti  
 Imposta l'ordine dei singoli inserimenti, aggiornamenti ed eliminazioni che impostando l'ordine per eseguire gli aggiornamenti è necessari per salvare tutti i dati modificati in tutte le tabelle di un set di dati. Quando aggiornamento gerarchico è abilitata, gli inserimenti vengono eseguite per prime, quindi aggiorna ed eliminato. Il `TableAdapterManager` fornisce un `UpdateOrder` proprietà che può essere impostata per eseguire aggiornamenti in primo luogo, quindi inserimenti ed eliminazioni.  
  
> [!NOTE]
> È importante comprendere che l'ordine di aggiornamento è tutto compreso. Ovvero, quando vengono eseguiti gli aggiornamenti, inserimenti ed eliminazioni vengono eseguite per tutte le tabelle nel set di dati.  
  
 Per impostare il `UpdateOrder` proprietà, dopo il trascinamento degli elementi dal [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) in un form, selezionare il `TableAdapterManager` nella barra dei componenti e quindi impostare il `UpdateOrder` proprietà nel **proprietà** finestra. Per altre informazioni, vedere [Procedura: Impostare l'ordine quando si esegue un aggiornamento gerarchico](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).  
  
## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Creare una copia di backup di un set di dati prima di eseguire un aggiornamento gerarchico  
 Quando si salvano i dati (chiamando il `TableAdapterManager.UpdateAll()` metodo), il `TableAdapterManager` tenta di aggiornare i dati per ogni tabella in una singola transazione. Se qualsiasi parte dell'aggiornamento per tutte le tabelle non riesce, viene eseguito il rollback dell'intera transazione. Nella maggior parte dei casi, il ripristino dello stato precedente restituisce l'applicazione allo stato originale.  
  
 Tuttavia, in alcuni casi è consigliabile ripristinare il set di dati dalla copia di backup. Un esempio di questo può verificarsi quando si usano i valori a incremento automatico. Ad esempio, se un salvataggio operazione non riesce, i valori a incremento automatico vengono reimpostati non nel set di dati e il set di dati continui a creare i valori a incremento automatico. In tal modo un gap nella numerazione che potrebbe non essere accettabile all'interno dell'applicazione. In situazioni in cui si tratta di un problema, il `TableAdapterManager` fornisce un `BackupDataSetBeforeUpdate` proprietà che sostituisce il set di dati esistente con una copia di backup, se la transazione ha esito negativo.  
  
> [!NOTE]
> La copia di backup è solo in memoria, mentre il `TableAdapterManager.UpdateAll` metodo è in esecuzione. Pertanto, non è presente alcun accesso a livello di codice per questo set di dati di backup perché sostituisce il set di dati originale o abbandona l'ambito non appena il `TableAdapterManager.UpdateAll` metodo al termine dell'esecuzione.  
  
## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modificare il generato codice per eseguire l'aggiornamento gerarchico di salvataggio  
 Salvare le modifiche dalle tabelle dati correlate del set di dati nel database chiamando il metodo `TableAdapterManager.UpdateAll` e passando il nome del set di dati contenente le tabelle correlate. Ad esempio, eseguire il metodo `TableAdapterManager.UpdateAll(NorthwindDataset)` per inviare gli aggiornamenti da tutte le tabelle presenti in NorthwindDataSet al database back-end.  
  
 Dopo avere rilasciato gli elementi dalla finestra **Origini dati**, il codice viene automaticamente aggiunto all'evento `Form_Load` per popolare ogni tabella (metodi `TableAdapter.Fill`). Il codice viene anche aggiunto all'evento Click del pulsante **Salva** di <xref:System.Windows.Forms.BindingNavigator> per salvare i dati dal set di dati nel database (metodo `TableAdapterManager.UpdateAll`).  
  
 Il codice di salvataggio generato contiene anche una riga di codice che chiama il metodo `CustomersBindingSource.EndEdit`. In particolare, chiama il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> del primo metodo <xref:System.Windows.Forms.BindingSource>che viene aggiunto al form. In altre parole, questo codice viene generato solo per la prima tabella che viene trascinata dal **Zdroje dat** finestra nei form. La chiamata al metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> esegue il commit di tutte le modifiche in corso nei controlli associati a dati che si stanno modificando. Pertanto, se un controllo associato a dati ha lo stato attivo e si fa clic sul pulsante **Salva**, prima del salvataggio effettivo verrà eseguito il commit di tutte le modifiche in sospeso nel controllo (metodo `TableAdapterManager.UpdateAll`).  
  
> [!NOTE]
> La finestra di progettazione set di dati aggiunge solo il `BindingSource.EndEdit` codice per la prima tabella che viene rilasciata nel form. Pertanto, è necessario aggiungere una riga di codice per chiamare il metodo `BindingSource.EndEdit` per ogni tabella correlata nel form. Per questa procedura dettagliata, è necessario quindi aggiungere una chiamata al metodo `OrdersBindingSource.EndEdit`.  
  
#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Per aggiornare il codice in modo da eseguire il commit delle modifiche apportate alle tabelle correlate prima del salvataggio  
  
1. Fare doppio clic sul pulsante **Salva** in <xref:System.Windows.Forms.BindingNavigator> per aprire **Form1** nell'editor del codice.  
  
2. Aggiungere una riga di codice per chiamare il metodo `OrdersBindingSource.EndEdit` dopo la riga che chiama il metodo `CustomersBindingSource.EndEdit`. Il codice nell'evento Click del pulsante **Salva** deve essere simile al seguente:  
  
    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]  
  
   Oltre a eseguire il commit delle modifiche apportate a una tabella figlio correlata prima di salvare i dati in un database, potrebbe anche essere necessario eseguire il commit dei record padre appena creati prima di aggiungere i nuovi record figlio in un set di dati. In altre parole, potrebbe essere necessario aggiungere il nuovo record padre (Customer) al set di dati affinché i vincoli di chiave esterna consentano l'aggiunta dei nuovi record figli (Orders) al set di dati. A tale scopo, è possibile usare l'evento figlio `BindingSource.AddingNew`.  
  
> [!NOTE]
> Se è necessario eseguire il commit nuovi record padre dipende dal tipo di controllo che consente di eseguire l'associazione all'origine dati. In questa procedura dettagliata, singoli controlli consentono di eseguire l'associazione alla tabella padre. Ciò richiede il codice aggiuntivo per eseguire il commit del nuovo record padre. Se i record padre invece sono stati visualizzati in un controllo con associazione complessa come la <xref:System.Windows.Forms.DataGridView>, questo aggiuntivi <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per i record padre non sarebbe necessario chiamare. perché la funzionalità di data-binding sottostante del controllo gestisce l'esecuzione del commit dei nuovi record.  
  
#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Per aggiungere il codice per eseguire il commit dei record padre nel set di dati prima dell'aggiunta dei nuovi record figlio  
  
1. Creare un gestore eventi per l'evento `OrdersBindingSource.AddingNew`.  
  
    - Aprire **Form1** nella visualizzazione progettazione, selezionare **OrdersBindingSource** nella barra dei componenti, selezionare **eventi** nel **proprietà** finestra e quindi fare doppio clic il **AddingNew** evento.  
  
2. Aggiungere una riga di codice al gestore dell'evento che chiama il `CustomersBindingSource.EndEdit` (metodo). Il codice nel gestore eventi `OrdersBindingSource_AddingNew` deve essere simile al seguente:  
  
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]  
  
## <a name="tableadaptermanager-reference"></a>Riferimento a TableAdapterManager  
 Per impostazione predefinita, un `TableAdapterManager` classe viene generata quando si crea un set di dati che contiene le tabelle correlate. Per evitare che la classe da generare, modificare il valore della `Hierarchical Update` proprietà del set di dati su false. Quando si trascina una tabella che dispone di una relazione nell'area di progettazione di un Windows Form o nella pagina WPF, Visual Studio viene dichiarata una variabile membro della classe. Se non si usa l'associazione dati, è necessario dichiarare manualmente la variabile.  
  
 Il `TableAdapterManager` classe non è in parte il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Pertanto, è possibile cercarla nella documentazione. Viene creato in fase di progettazione come parte del processo di creazione del set di dati.  
  
 Di seguito sono i metodi usati di frequente e le proprietà di `TableAdapterManager` classe:  
  
|Member|Descrizione|  
|------------|-----------------|  
|Metodo `UpdateAll`|Salva tutti i dati da tutte le tabelle di dati.|  
|Proprietà`BackUpDataSetBeforeUpdate` |Determina se creare una copia di backup del set di dati prima di eseguire il `TableAdapterManager.UpdateAll` (metodo). Valore booleano.|  
|*tableName* `TableAdapter` proprietà|Rappresenta un `TableAdapter`. Generato `TableAdapterManager` contiene una proprietà per ogni `TableAdapter` gestisce. Ad esempio, viene generato un set di dati con una tabella Customers e Orders con un `TableAdapterManager` che contiene `CustomersTableAdapter` e `OrdersTableAdapter` proprietà.|  
|Proprietà`UpdateOrder` |Controlla l'ordine delle singole insert, update e i comandi delete. Impostare questa proprietà su uno dei valori di `TableAdapterManager.UpdateOrderOption` enumerazione.<br /><br /> Per impostazione predefinita, il `UpdateOrder` è impostata su **InsertUpdateDelete**. Ciò significa che inserisce, aggiorna quindi Elimina quindi vengono eseguite per tutte le tabelle nel set di dati. Per altre informazioni, vedere [Procedura: Impostare l'ordine quando si esegue un aggiornamento gerarchico](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
