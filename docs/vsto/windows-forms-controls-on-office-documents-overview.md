---
title: Controlli Windows Form in panoramica di documenti di Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 927451ed35ce4bbdfbff7531b2828b0571354f34
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445361"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Controlli Windows Form in panoramica di documenti di Office
  I controlli Windows Form sono oggetti con cui gli utenti possono interagire per immettere o modificare i dati. Nei progetti a livello di documento per Microsoft Office Excel e Microsoft Office Word, è possibile aggiungere controlli Windows Form al documento o cartella di lavoro nel progetto in fase di progettazione oppure è possibile aggiungere questi controlli a livello di codice in fase di esecuzione. A livello di codice, è possibile aggiungere questi controlli a qualsiasi documento aperto o foglio di lavoro in fase di esecuzione in un componente aggiuntivo VSTO per Excel o Word.

 Per altre informazioni, vedere [Procedura: Aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="use-windows-forms-controls"></a>Usare i controlli Windows Form

È possibile aggiungere controlli Windows Form ai documenti e agli elementi personalizzabili dell'interfaccia utente, tra cui riquadri azioni, riquadri attività personalizzati e Windows Form. I controlli Windows Form in genere hanno lo stesso comportamento nei documenti e in questi altri elementi dell'interfaccia utente, ma esistono alcune differenze. Per informazioni, vedere [consente di controllare le limitazioni di Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

La decisione di aggiungere controlli Windows Form a un documento o a un altro elemento dell'interfaccia utente dipende da diversi fattori. Quando si progetta l'interfaccia utente della soluzione, tenere in considerazione gli usi dei controlli Windows Form descritti nella tabella seguente.

In un documento.
- Per fare in modo che i controlli siano visualizzati costantemente.

- Per consentire agli utenti di immettere dati direttamente nel documento, ad esempio in documenti basati su form in cui l'area di modifica è bloccata.

- Per visualizzare i controlli in linea con i dati nel documento. Ad esempio, se si aggiungono pulsanti a ogni riga di un oggetto elenco, è consigliabile che siano allineati alle singole voci dell'elenco.

Nel riquadro azioni o in un riquadro attività personalizzato
- Per fornire informazioni contestuali all'utente.

- Per fare in modo che nel documento vengano visualizzati solo i risultati e non i controlli e i dati di query.

- Per assicurarsi che i controlli non vengano stampati con il documento.

- Per assicurarsi che i controlli non interferiscano con la visualizzazione del documento.

In un Windows Form
- Per poter controllare le dimensioni dell'interfaccia utente.

- Per impedire agli utenti di nascondere o eliminare i controlli.

- Per ottenere l'input dall'utente e impedire a quest'ultimo di eseguire qualsiasi operazione nel documento fino a quando non viene ricevuto l'input.

## <a name="add-windows-forms-controls-programmatically"></a>Aggiungere controlli Windows Form a livello di codice
 È possibile aggiungere controlli Windows Form ai documenti Word e fogli di lavoro di Excel in fase di esecuzione. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fornisce metodi helper per l'aggiunta dei controlli Windows Form più comuni. Questi metodi helper consentono di aggiungere rapidamente controlli a un documento di Office e di accedere alle funzionalità combinate dei controlli Windows Form e alle funzionalità correlate a Office di questi controlli.

 Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="use-windows-forms-controls-in-document-level-projects"></a>Usare i controlli Windows Form nei progetti a livello di documento
 Alcuni aspetti dell'uso dei controlli Windows Form nei documenti sono specifici dei progetti a livello di documento, che consentono di progettare l'interfaccia utente del documento usando la finestra di progettazione di Visual Studio.

### <a name="create-custom-user-controls"></a>Creare controlli utente personalizzati
 È possibile aggiungere un controllo utente al progetto e quindi aggiungerlo alla **casella degli strumenti**. È quindi possibile trascinare il controllo utente direttamente nel documento così come si aggiunge un controllo Windows Form a un documento. Esistono alcuni aspetti da tenere presenti quando si creano controlli utente:

- Non creare un controllo utente **sealed** . Quando si trascina il controllo nel documento, Visual Studio genera una classe wrapper derivata dal controllo utente per estenderlo e supportarne l'uso nel documento. Se il controllo utente è **sealed**, Visual Studio non può generare la classe wrapper.

- I controlli utente devono avere l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su **true**. Nei controlli utente creati all'interno di un progetto di Office questo attributo è impostato su **true** per impostazione predefinita, ma nei controlli utente che fanno parte di progetti esterni questo stesso attributo potrebbe non essere impostato su **true**.

- Dopo aver aggiunto un controllo utente al documento, non rinominare o eliminare la classe <xref:System.Windows.Forms.UserControl> dal progetto. Se è necessario rinominare un controllo utente, bisogna prima eliminarlo dal documento e quindi aggiungerlo di nuovo dopo aver cambiato il nome.

### <a name="arrange-controls-at-design-time"></a>Disporre i controlli in fase di progettazione
 Se si aggiungono più controlli ai documenti di Word ed Excel in fase di progettazione, si può impostare rapidamente l'allineamento di tutti i controlli selezionati usando le barre degli strumenti **Microsoft Office Word** e **Microsoft Office Excel** in Visual Studio. Queste barre degli strumenti sono disponibili solo quando è aperto un documento o foglio di lavoro nella finestra di progettazione.

 Quando si selezionano più controlli nella finestra di progettazione, è possibile usare i pulsanti seguenti in queste barre degli strumenti per disporre i controlli:

- **Allinea a sinistra**

- **Allinea al centro**

- **Allinea a destra**

- **Allinea in alto**

- **Allinea in mezzo**

- **Allinea in basso**

- **Uniforma spaziatura orizzontale**

- **Uniforma spaziatura verticale**

> [!NOTE]
> Nei progetti di Word, questi pulsanti sono abilitati solo se i controlli selezionati non sono in linea con il testo. Per impostazione predefinita, i controlli aggiunti al documento in fase di progettazione sono in linea con il testo.

### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Impedire la visualizzazione nelle cartelle di lavoro di Excel durante il caricamento dei dati obsoleti
 Quando si aggiungono controlli Windows Form a documenti o fogli di lavoro in fase di progettazione, i controlli rimangono nel documento quando l'utente chiude il documento. I controlli aggiunti in fase di progettazione sono anche definiti *controlli statici*.

 Quando si apre una cartella di lavoro di Excel che contiene controlli statici, la cartella di lavoro mostra una bitmap del controllo in un controllo ActiveX fino a quando non viene eseguito il codice di personalizzazione e caricato il controllo effettivo. Excel crea questa bitmap e la archivia nella cartella di lavoro quando si salva la cartella di lavoro. La bitmap mostra l'aspetto del controllo al momento dell'ultimo salvataggio della cartella di lavoro, inclusi tutti i dati che vi erano visualizzati. Per altre informazioni sul controllo ActiveX che contiene controlli Windows Form e bitmap, vedere [consente di controllare le limitazioni di Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

 In determinate condizioni, il codice non viene caricato e viene visualizzata solo la bitmap, ad esempio quando l'utente apre la cartella di lavoro in modalità di progettazione. Inoltre, se l'utente apre la cartella di lavoro in un computer in cui non è installato [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , non viene eseguita la personalizzazione per caricare i caricare i controlli e pertanto è visibile solo la bitmap del controllo. È consigliabile rimuovere sempre le informazioni personali dai controlli nelle cartelle di lavoro prima di salvare una cartella di lavoro e inviarla a un altro utente per assicurarsi che le informazioni personali non vengano accidentalmente divulgate.

### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Dimensione del controllo corrispondono alle dimensioni di cella in un foglio di lavoro di Excel
 È possibile impostare il ridimensionamento automatico del controllo quando vengono modificate le dimensioni della cella padre. Per altre informazioni, vedere [Procedura: Ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Aggiungere i componenti condivisi da tutti i fogli di lavoro
 I componenti da condividere in tutti i fogli di lavoro, ad esempio un oggetto <xref:System.Data.DataSet>, possono essere aggiunti alla finestra di progettazione delle cartelle di lavoro anziché ai fogli di lavoro. Il componente verrà visualizzato nella barra dei componenti.

### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Formula per l'incorporamento di controlli in un foglio di lavoro di Excel
 Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

### <a name="layout-style-of-controls-on-a-word-document"></a>Stile di layout di controlli in un documento di Word
 Quando si aggiunge un controllo al documento di Word in un progetto a livello di documento usando la finestra di progettazione di Visual Studio, il controllo viene aggiunto in linea con il testo. Per modificare lo stile di layout del controllo, fare clic con il pulsante destro del mouse sul controllo e scegliere **Formato controllo**. Selezionare uno stile nella pagina **Layout** della finestra di dialogo **Formato oggetto** .

 Quando si aggiunge un controllo a un documento di Word in fase di esecuzione, è possibile specificare lo stile di layout del nuovo controllo usando diversi `Add` \< *classe del controllo*> esegue l'overload del metodo di <xref:Microsoft.Office.Tools.Word.ControlCollection> classe:

- Per aggiungere il controllo in linea con testo, usare un overload che accetta un oggetto <xref:Microsoft.Office.Interop.Word.Range> che specifica la posizione del controllo.

- Per aggiungere il controllo come forma mobile, usare un overload che accetta la coordinata superiore e la coordinata sinistra del controllo.

  Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Se si apre un modello di Word nella finestra di progettazione di Visual Studio, i controlli non inline nel modello potrebbero non essere visibili perché Visual Studio apre il modello in visualizzazione **Normale** . Per visualizzare i controlli, modificare la visualizzazione in **Layout di stampa**.

### <a name="controls-outside-the-main-document-body"></a>Controlli all'esterno del corpo principale del documento
 I controlli Windows Form non sono supportati all'interno di un'intestazione o piè di pagina o di un documento secondario.

### <a name="add-components-at-design-time"></a>Aggiungere i componenti in fase di progettazione
 Alcuni controlli o componenti non sono visibili nel documento e vengono invece visualizzati in una barra dei componenti. Visual Studio fornisce una barra dei componenti per ogni finestra del documento. La barra dei componenti viene visualizzata solo se sono presenti componenti nel documento.

## <a name="see-also"></a>Vedere anche
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Controlli Windows Form](/dotnet/framework/winforms/controls/index)
- [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Procedura: Aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedura: Ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Procedura: Nascondere controlli nei fogli di lavoro durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Procedura dettagliata: La modifica del foglio di lavoro della formattazione mediante controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Procedura dettagliata: Modificare la formattazione dei documenti mediante controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)
- [Procedura dettagliata: Testo visualizzato in una casella di testo in un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Procedura dettagliata: Testo visualizzato in una casella di testo in un documento tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)
- [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Procedura dettagliata: Aggiornare un grafico in un documento mediante pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)
- [Procedura dettagliata: Aggiornare un grafico in un foglio di lavoro mediante pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
