---
title: "Procedura: Aggiornare un'origine dati con dati provenienti da un controllo host"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24bbd859b4867225e5ec5df95d298dd04146df46
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421011"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Procedura: Aggiornare un'origine dati con dati provenienti da un controllo host
  È possibile associare un controllo host a un'origine dati e aggiornare l'origine dati con le modifiche apportate ai dati nel controllo. Questo processo prevede due passaggi principali:

1. Aggiornare l'origine dati in memoria con i dati modificati nel controllo. In genere, l'origine dati in memoria è un oggetto <xref:System.Data.DataSet>, <xref:System.Data.DataTable>o un altro oggetto dati.

2. Aggiornare il database con i dati modificati nell'origine dati in memoria. Ciò è possibile solo se l'origine dati è connessa a un database back-end, ad esempio un database SQL Server o Microsoft Office Access.

   Per altre informazioni sui controlli host e il data binding, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md) e [associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>Aggiornare l'origine dati in memoria
 Per impostazione predefinita, i controlli host che consentono il data binding semplice (ad esempio i controlli contenuto in un documento di Word o un controllo di intervallo denominato in un foglio di lavoro di Excel) non salvano le modifiche all'origine dati in memoria. In altre parole, quando un utente finale modifica un valore in un controllo host e successivamente si sposta dal controllo, il nuovo valore del controllo non viene salvato nell'origine dati.

 Per salvare i dati all'origine dati, è possibile scrivere codice che aggiorna l'origine dati in risposta a un evento specifico in fase di esecuzione oppure è possibile configurare il controllo per aggiornare automaticamente l'origine dati quando viene modificato il valore del controllo.

 Non è necessario salvare le modifiche apportate a <xref:Microsoft.Office.Tools.Excel.ListObject> nell'origine dati in memoria. Quando si associa un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ai dati, il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> salva automaticamente le modifiche nell'origine dati in memoria senza che sia richiesto codice aggiuntivo.

### <a name="to-update-the-in-memory-data-source-at-runtime"></a>Per aggiornare l'origine dati in memoria in fase di esecuzione

- Chiamare il metodo <xref:System.Windows.Forms.Binding.WriteValue%2A> dell'oggetto <xref:System.Windows.Forms.Binding> che associa il controllo all'origine dati.

     Nell'esempio seguente le modifiche apportate a un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in un foglio di lavoro di Excel vengono salvate nell'origine dati. Questo esempio presuppone che sia presente un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `namedRange1` la cui proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> è associata a un campo in un'origine dati.

     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]

### <a name="automatically-update-the-in-memory-data-source"></a>Aggiornamento automatico dell'origine dati in memoria
 È anche possibile configurare un controllo in modo da aggiornare automaticamente l'origine dati in memoria. In un progetto a livello di documento, questa operazione può essere eseguita tramite codice o tramite la finestra di progettazione. In un progetto di componente aggiuntivo VSTO, è necessario usare codice.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Per impostare un controllo in modo che l'origine dati in memoria venga aggiornata automaticamente tramite codice

1. Usare la modalità DataSourceUpdateMode del <xref:System.Windows.Forms.Binding> oggetto che associa il controllo all'origine dati. Per aggiornare l'origine dati è possibile procedere in due modi:

   - Per aggiornare l'origine dati quando il controllo viene convalidato, impostare questa proprietà su System.Windows.Forms.DataSourceUpdateMode.OnValidation.

   - Per aggiornare l'origine dati quando cambia il valore della proprietà del controllo associato a dati, impostare questa proprietà su DataSourceUpdateMode.

     > [!NOTE]
     > L'opzione DataSourceUpdateMode non si applica ai controlli host di Word perché Word non le notifiche non offerta al documento o modifica del controllo. ma può essere usata per i controlli Windows Form nei documenti di Word.

     L'esempio seguente configura un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in modo che l'origine dati venga aggiornata automaticamente quando si modifica il valore del controllo. Questo esempio presuppone che sia presente un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `namedRange1` la cui proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> è associata a un campo in un'origine dati.

     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Per impostare un controllo in modo che l'origine dati in memoria venga aggiornata automaticamente tramite la finestra di progettazione

1. In Visual Studio, aprire il documento di Word o la cartella di lavoro di Excel nella finestra di progettazione.

2. Fare clic sul controllo desiderato per aggiornare automaticamente l'origine dati.

3. Nella finestra **Proprietà** espandere la proprietà **(DataBindings)** .

4. Accanto al **(avanzate)** proprietà, fare clic sul pulsante con puntini di sospensione (![schermata di VisualStudioEllipsesButton](../vsto/media/vbellipsesbutton.png "schermata di VisualStudioEllipsesButton")).

5. Nella finestra di dialogo **Formattazione e associazione avanzata** fare clic nell'elenco a discesa **Modalità aggiornamento origine dati** e selezionare uno dei valori seguenti:

    - Per aggiornare l'origine dati quando il controllo viene convalidato, selezionare **OnValidation**.

    - Per aggiornare l'origine dati quando si modifica il valore della proprietà del controllo associata ai dati, selezionare **OnPropertyChanged**.

        > [!NOTE]
        > L'opzione **OnPropertyChanged** non si applica ai controlli host di Word perché Word non fornisce notifiche relative alle modifiche al documento o al controllo, ma può essere usata per i controlli Windows Form nei documenti di Word.

6. Chiudere la finestra di dialogo **Formattazione e associazione avanzata** .

## <a name="update-the-database"></a>Aggiornare il database
 Se l'origine dati in memoria è associata a un database, è necessario aggiornare il database in base alle modifiche apportate all'origine dati. Per altre informazioni sull'aggiornamento di un database, vedere [salvare i dati nel database](../data-tools/save-data-back-to-the-database.md) e [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .

### <a name="to-update-the-database"></a>Per aggiornare il database

1. Chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per il controllo <xref:System.Windows.Forms.BindingSource> .

     L'oggetto <xref:System.Windows.Forms.BindingSource> viene generato automaticamente quando un controllo associato a dati viene aggiunto a un documento o a una cartella di lavoro in fase di progettazione. L'oggetto <xref:System.Windows.Forms.BindingSource> connette il controllo al set di dati tipizzato nel progetto. Per altre informazioni, vedere [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

     L'esempio di codice seguente presuppone che il progetto contenga un oggetto <xref:System.Windows.Forms.BindingSource> denominato `customersBindingSource`.

     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]

2. Chiamare il `Update` metodo dell'oggetto TableAdapter generati nel progetto.

     Oggetto TableAdapter viene generato automaticamente quando si aggiunge un controllo con associazione a dati a un documento o cartella di lavoro in fase di progettazione. Il TableAdapter si connette il set di dati tipizzato nel progetto per il database. Per altre informazioni, vedere [panoramica degli oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Esempio di codice seguente si presuppone di avere una connessione alla tabella Customers nel database Northwind e che il progetto contiene un oggetto TableAdapter denominato `customersTableAdapter` e un set di dati tipizzato denominato `northwindDataSet`.

     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]

## <a name="see-also"></a>Vedere anche
- [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
- [Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Procedura: Scorrere i record di database in un foglio di lavoro](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Procedura: Popolare fogli di lavoro con i dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Procedura: Popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: Popolare documenti con dati provenienti da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)
