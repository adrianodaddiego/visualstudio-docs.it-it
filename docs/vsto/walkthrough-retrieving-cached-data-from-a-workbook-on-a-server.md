---
title: 'Procedura dettagliata: Recuperare i dati memorizzati nella cache da una cartella di lavoro in un server'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ddf7bd222b61b3eb72a571857336c69deba6499f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421778"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Procedura dettagliata: Recuperare i dati memorizzati nella cache da una cartella di lavoro in un server
  Questa procedura dettagliata illustra come recuperare i dati da un set di dati memorizzato nella cache di una cartella di lavoro di Microsoft Office Excel senza avviare Excel utilizzando il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Questa procedura dettagliata illustra le attività seguenti:

- La definizione di un set di dati che contiene i dati dal *AdventureWorksLT* database.

- Creazione di istanze del set di dati in un progetto cartella di lavoro di Excel e un progetto applicazione console.

- Creazione di un <xref:Microsoft.Office.Tools.Excel.ListObject> che viene associato al set di dati nella cartella di lavoro e il popolamento di <xref:Microsoft.Office.Tools.Excel.ListObject> con i dati quando viene aperta la cartella di lavoro.

- Aggiunta di set di dati nella cartella di lavoro per la cache dei dati.

- Lettura dei dati dal set di dati memorizzati nella cache nel set di dati nell'applicazione console senza avviare Excel.

  Sebbene questa procedura dettagliata si presuppone che si esegue il codice nel computer di sviluppo, il codice illustrato da questa procedura dettagliata è utilizzabile in un server che non dispone di Excel sia installato.

> [!NOTE]
> I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un'istanza in esecuzione di Microsoft SQL Server o Microsoft SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Per altre informazioni sul collegamento di un database, vedere gli argomenti seguenti:

    - Per collegare un database usando SQL Server Management Studio o SQL Server Management Studio Express, vedere [come: Collegare un database (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

    - Per collegare un database tramite la riga di comando, vedere [come: Collegare un file di database a SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Creare un progetto di libreria di classi che definisce un set di dati
 Per usare lo stesso set di dati in un progetto cartella di lavoro di Excel e un'applicazione console, è necessario definire il set di dati in un assembly separato a cui viene fatto riferimento da entrambi questi progetti. Per questa procedura dettagliata, definire il set di dati in un progetto di libreria di classi.

### <a name="create-the-class-library-project"></a>Creare il progetto di libreria di classi

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3. Nel riquadro dei modelli, espandere **Visual c#** oppure **Visual Basic**, quindi fare clic su **Windows**.

4. Nell'elenco dei modelli di progetto, selezionare **libreria di classi**.

5. Nel **Name** , digitare **AdventureWorksDataSet**.

6. Fare clic su **esplorare**, passare alle *documenti %UserProfile%\My* (per Windows XP e versioni precedenti) o *%UserProfile%\Documents* (per Windows Vista) cartella e quindi fare clic su **Seleziona cartella**.

7. Nel **nuovo progetto** finestra di dialogo casella, verificare che il **Crea directory per soluzione** casella di controllo non è selezionata.

8. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **AdventureWorksDataSet** da progetto a **Esplora soluzioni** e apre il *Class1.cs* oppure *Class1.vb* file di codice.

9. Nella **Esplora soluzioni**, fare doppio clic su *Class1.cs* oppure *Class1.vb*, quindi fare clic su **Elimina**. Questo file non è necessario per questa procedura dettagliata.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definire un set di dati nel progetto libreria di classi
 Definire un set di dati tipizzato che contiene i dati dal database AdventureWorksLT per SQL Server 2005. Più avanti in questa procedura dettagliata, si farà riferimento questo set di dati da un progetto cartella di lavoro di Excel e un progetto applicazione console.

 Il set di dati è un *dataset tipizzato* che rappresenta i dati nella tabella Product del database AdventureWorksLT. Per altre informazioni sui dataset tipizzati, vedere [strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Definire un set di dati tipizzato nel progetto libreria di classi

1. Nelle **Esplora soluzioni**, fare clic sui **AdventureWorksDataSet** progetto.

2. Se il **Zdroje dat** finestra non è visibile, visualizzarla, dalla barra dei menu, scegliendo **View** > **Other Windows**  >   **Zdroje dat**.

3. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

4. Selezionare **Database**e quindi scegliere **Avanti**.

5. Se si dispone di una connessione esistente al database AdventureWorksLT, selezionarla e fare clic su **successivo**.

    In caso contrario, scegliere **Nuova connessione**e usare la finestra di dialogo **Aggiungi connessione** per creare la nuova connessione. Per altre informazioni, vedere [aggiungere le nuove connessioni](../data-tools/add-new-connections.md).

6. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.

7. Nel **Scegli oggetti di Database** , espandere **tabelle** e selezionare **Product (SalesLT)**.

8. Scegliere **Fine**.

    Il *AdventureWorksLTDataSet* file viene aggiunto per il **AdventureWorksDataSet** progetto. Questo file definisce gli elementi seguenti:

   - Un set di dati tipizzato denominato `AdventureWorksLTDataSet`. Questo set di dati rappresenta il contenuto della tabella Product nel database AdventureWorksLT.

   - Un oggetto TableAdapter denominato `ProductTableAdapter`. Questo oggetto TableAdapter consente di leggere e scrivere dati `AdventureWorksLTDataSet`. Per altre informazioni, vedere [panoramica degli oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Si useranno entrambi gli oggetti più avanti in questa procedura dettagliata.

9. Nelle **Esplora soluzioni**, fare doppio clic su **AdventureWorksDataSet** e fare clic su **compilare**.

     Verificare che il progetto venga compilato senza errori.

## <a name="create-an-excel-workbook-project"></a>Creare un progetto cartella di lavoro di Excel
 Creare un progetto cartella di lavoro di Excel per l'interfaccia per i dati. Più avanti in questa procedura dettagliata, si creerà un <xref:Microsoft.Office.Tools.Excel.ListObject> che visualizza i dati e si aggiungerà un'istanza del set di dati per la cache dei dati nella cartella di lavoro.

### <a name="create-the-excel-workbook-project"></a>Creare il progetto di cartella di lavoro di Excel

1. In **Esplora soluzioni**, fare doppio clic sul **AdventureWorksDataSet** soluzione, scegliere **Add**, quindi fare clic su **nuovo progetto**.

2. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

3. Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .

4. Nell'elenco di modelli di progetto selezionare il progetto **Cartella di lavoro di Excel 2010** o **Cartella di lavoro di Excel 2013** .

5. Nel **Name** , digitare **AdventureWorksReport**. Non modificare il percorso.

6. Fare clic su **OK**.

     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .

7. Assicurarsi che **creare un nuovo documento** sia selezionata e fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Apre la **AdventureWorksReport** cartella di lavoro nella finestra di progettazione e aggiunge il **AdventureWorksReport** progetto al **Esplora soluzioni**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Aggiungere il set di dati a origini dati nel progetto di cartella di lavoro di Excel
 Prima che sia possibile visualizzare il set di dati nella cartella di lavoro di Excel, è innanzitutto necessario aggiungere il set di dati alle origini dati nel progetto di cartella di lavoro di Excel.

1. Nella **Esplora soluzioni**, fare doppio clic su *Sheet1.cs* oppure *Sheet1.vb* sotto il **AdventureWorksReport** progetto.

     Consente di aprire la cartella di lavoro nella finestra di progettazione.

2. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

     Viene avviata la **Configurazione guidata origine dati**.

3. Fare clic su **oggetti**, quindi fare clic su **successivo**.

4. Nel **selezionare l'oggetto da associare** alla pagina, fare clic su **Aggiungi riferimento**.

5. Nel **progetti** scheda, fare clic su **AdventureWorksDataSet** e quindi fare clic su **OK**.

6. Sotto il **AdventureWorksDataSet** dello spazio dei nomi delle **AdventureWorksDataSet** assembly, fare clic su **AdventureWorksLTDataSet** e quindi fare clic su **fine** .

     Il **Zdroje dat** viene visualizzata una finestra e **AdventureWorksLTDataSet** viene aggiunto all'elenco di origini dati.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Creare un controllo ListObject associato a un'istanza del set di dati
 Per visualizzare il set di dati nella cartella di lavoro, creare un <xref:Microsoft.Office.Tools.Excel.ListObject> associato a un'istanza del set di dati. Per altre informazioni sull'associazione dei controlli ai dati, vedere [associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

1. Nel **Zdroje dat** finestra, espandere il **AdventureWorksLTDataSet** nodo sotto **AdventureWorksDataSet**.

2. Selezionare il **prodotto** nodo, fare clic sulla freccia giù visualizzata e selezionarla **ListObject** nell'elenco a discesa.

     Se la freccia a discesa non viene visualizzata, verificare che la cartella di lavoro è aperta nella finestra di progettazione.

3. Trascinare il **prodotto** alla cella A1.

     Oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato `productListObject` viene creato nel foglio di lavoro, a partire dalla cella A1. Allo stesso tempo vengono aggiunti al progetto un oggetto del set di dati denominato `adventureWorksLTDataSet` e un oggetto <xref:System.Windows.Forms.BindingSource> denominato `productBindingSource` . <xref:Microsoft.Office.Tools.Excel.ListObject> è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato all'oggetto del set di dati.

## <a name="add-the-dataset-to-the-data-cache"></a>Aggiungere il set di dati per la cache dei dati
 Per consentire al codice all'esterno del progetto cartella di lavoro di Excel per accedere ai set di dati nella cartella di lavoro, è necessario aggiungere il set di dati per la cache dei dati. Per altre informazioni sulla cache di dati, vedere [memorizzato nella cache i dati nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md) e [memorizzare nella Cache dati](../vsto/caching-data.md).

1. Nella finestra di progettazione, fare clic su **adventureWorksLTDataSet**.

2. Nel **proprietà** impostare nella finestra di **modificatori** proprietà **pubblica**.

3. Impostare il **CacheInDocument** proprietà **True**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Inizializzare il set di dati nella cartella di lavoro
 Prima di poter recuperare i dati dal set di dati memorizzati nella cache usando l'applicazione console, è necessario innanzitutto popolare il set di dati memorizzati nella cache con i dati.

1. In **Esplora soluzioni**, fare doppio clic il *Sheet1.cs* oppure *Sheet1.vb* file e fare clic su **Visualizza codice**.

2. Sostituire il gestore eventi `Sheet1_Startup` con il codice seguente. Questo codice usa un'istanza del `ProductTableAdapter` definito nella classe la **AdventureWorksDataSet** progetto per riempire il set di dati memorizzati nella cache con i dati, se è attualmente vuota.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Checkpoint
 Compilare ed eseguire il progetto di cartella di lavoro di Excel per garantire che compilato ed eseguito senza errori. Questa operazione anche riempie il set di dati memorizzati nella cache e Salva i dati nella cartella di lavoro.

### <a name="build-and-run-the-project"></a>Compilare ed eseguire il progetto

1. In **Esplora soluzioni**, fare doppio clic sul **AdventureWorksReport** del progetto, scegliere **Debug**, quindi fare clic su **Avvia nuova istanza**.

     Il progetto viene compilato e viene aperta la cartella di lavoro in Excel. Verificare quanto segue:

    - Il <xref:Microsoft.Office.Tools.Excel.ListObject> inserisce i dati.

    - Il valore nel **ListPrice** per la prima riga della colonna il <xref:Microsoft.Office.Tools.Excel.ListObject> è 1431.5. Più avanti in questa procedura dettagliata, si userà un'applicazione console per modificare i valori di **ListPrice** colonna.

2. Salvare la cartella di lavoro. Non modificare il nome del file o alla posizione della cartella di lavoro.

3. Chiudere Excel.

## <a name="create-a-console-application-project"></a>Creare un progetto di applicazione console
 Creare un progetto di applicazione console da usare per modificare i dati nel set di dati memorizzati nella cache nella cartella di lavoro.

1. In **Esplora soluzioni**, fare doppio clic sul **AdventureWorksDataSet** soluzione, scegliere **Add**, quindi fare clic su **nuovo progetto**.

2. Nel **tipi di progetto** riquadro, espandere **Visual c#** o **Visual Basic**, quindi fare clic su **Windows**.

3. Nel **modelli** riquadro, selezionare **applicazione Console**.

4. Nel **Name** , digitare **DataReader**. Non modificare il percorso.

5. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **DataReader** da progetto a **Esplora soluzioni** e apre il *Program.cs* oppure *Module1.vb* file di codice.

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Recuperare dati dal set di dati memorizzati nella cache usando l'applicazione console
 Usare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe nell'applicazione console per leggere i dati in una variabile locale `AdventureWorksLTDataSet` oggetto. Per verificare che il set di dati locale è stata inizializzata con i dati dal set di dati memorizzati nella cache, l'applicazione visualizza il numero di righe nel set di dati locale.

### <a name="retrieve-data-from-the-cached-dataset"></a>Recuperare i dati dal set di dati memorizzati nella cache

1. In **Esplora soluzioni**, fare doppio clic il **DataReader** progetto e quindi scegliere **Aggiungi riferimento**.

2. Nel **.NET** scheda, seleziona **ServerDocument**.

3. Fare clic su **OK**.

4. In **Esplora soluzioni**, fare doppio clic il **DataReader** progetto e quindi scegliere **Aggiungi riferimento**.

5. Nel **progetti** scheda, seleziona **AdventureWorksDataSet**, fare clic su **OK**.

6. Aprire il *Program.cs* oppure *Module1.vb* file nell'editor del codice.

7. Aggiungere il codice seguente **usando** (per c#) o **Imports** (per Visual Basic) all'inizio del file di codice.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Aggiungere al metodo `Main` il seguente codice. Questo codice dichiara gli oggetti seguenti:

   - Un'istanza del `AdventureWorksLTDataSet` tipo definito nel **AdventureWorksDataSet** progetto.

   - Il percorso alla cartella di lavoro nella cartella di compilazione di AdventureWorksReport il **AdventureWorksReport** progetto.

   - Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> oggetto da utilizzare per accedere alla cache dei dati nella cartella di lavoro.

     > [!NOTE]
     > Il codice seguente presuppone che la cartella di lavoro viene salvato usando il *xlsx* estensione. Se la cartella di lavoro nel progetto è un'estensione diversa, modificare il percorso in base alle esigenze.

     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]

9. Aggiungere il codice seguente per il `Main` (metodo), dopo il codice aggiunto nel passaggio precedente. Mediante il codice vengono effettuate le seguenti attività:

   - Usa il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà del <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe per accedere ai set di dati memorizzati nella cache nella cartella di lavoro.

   - Legge i dati dal set di dati memorizzati nella cache nel set di dati locale.

   - Visualizza il numero di righe nel set di dati locale, per assicurarsi che i dati.

     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]

10. Nel **compilare** menu, fare clic su **DataReader compilare**.

## <a name="test-the-project"></a>Il progetto di test
 Quando si esegue l'applicazione console, Visualizza il numero di righe nel set di dati locale.

### <a name="test-the-workbook"></a>La cartella di lavoro di test

1. In **Esplora soluzioni**, fare doppio clic sul **DataReader** , scegliere **Debug**, quindi fare clic su **Avvia nuova istanza**.

     Verificare che l'applicazione segnala che il set di dati locale è 295 righe.

2. Premere **invio** per chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi
 Altre informazioni sull'uso dei dati memorizzati nella cache gli argomenti seguenti:

- La modifica dei dati in un set di dati memorizzati nella cache senza avviare Excel. Per altre informazioni, vedere [Procedura dettagliata: Modificare i dati memorizzati nella cache in una cartella di lavoro in un server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Inserire dati in una cartella di lavoro in un server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [Procedura dettagliata: Modificare i dati memorizzati nella cache in una cartella di lavoro in un server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
