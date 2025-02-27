---
title: Progetti di Office in ambiente di Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65f3a3abfe7e49872c7131a247d74612200bf42a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978058"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Progetti di Office in ambiente di Visual Studio
  L'esperienza di sviluppo relativa ai progetti di Microsoft Office è simile a quella per altri tipi di progetti in Visual Studio, ad esempio progetti Windows Form. Quando si crea o si apre un progetto di Office, gli elementi del progetto vengono visualizzati in **Esplora soluzioni**. Per i progetti a livello di documento, il documento (ossia il documento di Word o la cartella di lavoro di Excel) viene aperto in Visual Studio e funziona come una finestra di progettazione visiva.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="project-items-in-solution-explorer"></a>Elementi del progetto in Esplora soluzioni
 In un progetto a livello di documento, in **Esplora soluzioni** sono illustrati gli elementi predefiniti seguenti:

- I nodi per il documento, la cartella di lavoro e i fogli personalizzati per il progetto. Questi nodi fungono da contenitori per i file di codice associati al documento, alla cartella di lavoro e ai fogli.

- I file di codice associati al documento, alla cartella di lavoro e ai fogli personalizzato dal progetto. Nei progetti di Word i file di codice vengono associati al documento o al modello di Word. Nei progetti di Excel i file di codice vengono associati alla cartella di lavoro o al modello di Excel e a ogni foglio di lavoro e foglio grafico nella cartella di lavoro o nel modello.

- I file di progetto nascosti per i quali non è prevista la modifica diretta. Per altre informazioni, vedere [file di progetto nascosti](#hiddenfiles).

  In un progetto di componente aggiuntivo VSTO, in **Esplora soluzioni** sono illustrati gli elementi predefiniti seguenti:

- Il nodo dell'applicazione. Questo nodo ha lo stesso nome dell'applicazione host, ad esempio **Word**, **Excel**oppure **Outlook**. Il nodo dell'applicazione contiene il file di codice ThisAddIn. Fornisce anche la proprietà **Spazio dei nomi per elemento host** . Per altre informazioni su questa proprietà, vedere [delle proprietà nei progetti di Office](../vsto/properties-in-office-projects.md).

- Il file di codice ThisAddIn. Questo file contiene la classe `ThisAddIn` generata per il componente aggiuntivo VSTO. Per altre informazioni su questa classe, vedere [programma VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

- I file di progetto nascosti per i quali non è prevista la modifica diretta. Per altre informazioni, vedere [file di progetto nascosti](#hiddenfiles).

### <a name="temporary-certificates"></a>Certificati temporanei
 I progetti di Office includono anche un certificato temporaneo denominato *Nome progetto_TemporaryKey.pfx*. Questo certificato viene usato per firmare i manifesti dell'applicazione e della distribuzione per il progetto durante lo sviluppo. Per altre informazioni, vedere [concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md) e [soluzioni Office Secure](../vsto/securing-office-solutions.md).

### <a name="hiddenfiles"></a> File di progetto nascosti
 Alcuni file di progetto sono nascosti per impostazione predefinita. Questi file vengono generati da Visual Studio e si differenziano in base al tipo di progetto. Per visualizzare i file nascosti, fare clic su **Mostra tutti i file** in **Esplora soluzioni**.

 Non modificare i file di progetto nascosti. La modifica diretta di questi file non è supportata e potrebbe danneggiare il progetto. I file di progetto nascosti vengono rigenerati ogni volta che vengono apportate determinate modifiche al documento. Se si apportano modifiche manuali a un file di progetto nascosto, tali modifiche vengono perse quando il file viene rigenerato.

## <a name="document-designer-in-document-level-projects"></a>Creazione di documenti nei progetti a livello di documento
 I progetti a livello di documento per Excel e Word forniscono una finestra di progettazione che ospita il documento associato al progetto in Visual Studio. La finestra di progettazione consente di modificare il documento senza uscire dall'ambiente di Visual Studio.

 Per aprire un documento nella finestra di progettazione, fare doppio clic sul file di codice associato al documento in **Esplora soluzioni** . Ad esempio, per aprire il foglio di lavoro **Foglio1** nella finestra di progettazione in un progetto di Excel, fare doppio clic sul file di codice **Foglio1** .

 Quando si modifica il documento nella finestra di progettazione, è possibile usare la funzionalità nativa dell'applicazione di Office. Ad esempio, è possibile digitare il testo nel documento o in un foglio di lavoro oppure usare la barra multifunzione per eseguire attività quali l'aggiunta di una tabella o di un grafico. Per impostazione predefinita, per i tasti di scelta rapida viene usato automaticamente il mapping di Visual Studio. Per usare invece i mapping dei tasti di scelta rapida di Office, modificare le impostazioni in corrispondenza del nodo **Impostazioni tastiera Microsoft Office** nella finestra di dialogo **Opzioni** del menu **Strumenti** .

### <a name="controls-on-documents"></a>Controlli nei documenti
 È possibile trascinare i *controlli host* e i controlli Windows Form dalla **Casella degli strumenti** di Visual Studio all'area di progettazione del documento. I controlli host sono versioni specifiche di oggetti di Office, quali controlli del contenuto di Word e intervalli di Excel, che possono essere usati in progetti di Office creati tramite Visual Studio. I controlli host dispongono di funzionalità aggiuntive che non sono disponibili negli oggetti di Office corrispondenti, ad esempio associazione dati e ulteriori eventi.

 Per altre informazioni, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md) e [Windows Form controlli nella panoramica di documenti Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Fogli di lavoro di Excel e le cartelle di lavoro nella finestra di progettazione
 Quando si apre un foglio di lavoro nella finestra di progettazione, è possibile modificarlo come se fosse aperto direttamente in Excel. Se si fa doppio clic su una cella del foglio di lavoro, la cella passa alla modalità di modifica. Se si fa doppio clic su una cella che contiene un controllo host, si apre l'Editor di codice e Visual Studio genera il gestore eventi predefinito per il controllo. Per passare agli altri fogli di lavoro, è possibile fare clic sulle schede dei fogli di lavoro nella parte inferiore della finestra di progettazione.

 Quando si apre la cartella di lavoro nella finestra di progettazione, non è visualizzata alcuna area di progettazione. La visualizzazione Progettazione per la cartella di lavoro è una barra dei componenti di grandi dimensioni che occupa la finestra di progettazione.

 Alla cartella di lavoro e a ciascun foglio di lavoro è associato un file di codice. Ogni file di codice contiene una classe *elemento host* generata che rappresenta la cartella di lavoro o il foglio. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).

### <a name="word-documents-in-the-designer"></a>Documenti di Word nella finestra di progettazione
 Quando si apre il documento nella finestra di progettazione, è possibile modificarlo come se fosse aperto direttamente in Word. Se si fa doppio clic su una parola nel documento, tale parola viene selezionata. Se tuttavia la parola è all'interno di un controllo host, viene aperto l'editor di codice e in Visual Studio viene generato il gestore eventi predefinito per il controllo.

 Al documento è associato un file di codice. Il file di codice contiene una classe *elemento host* generata che rappresenta il documento. Per altre informazioni, vedere [elemento host Document](../vsto/document-host-item.md).

### <a name="design-mode-vs-runtime-mode"></a>Modalità di progettazione anziché in fase di esecuzione
 Se aperto nell'ambiente Visual Studio, il documento è sempre in *modalità di progettazione*. È possibile eseguire alcune attività, ad esempio il trascinamento di un controllo host nell'area del documento, solo in modalità di progettazione.

 Per visualizzare il documento nel *modalità runtime*, è necessario aprire l'applicazione e il documento all'esterno di Visual Studio. È anche possibile compilare ed eseguire il progetto, che aprirà automaticamente il documento e l'applicazione all'esterno di Visual Studio.

## <a name="code-editor"></a>Editor di codice
 L'editor di codice consente di visualizzare e modificare i file di codice visibili nella soluzione. Questi file contengono il codice che definisce il comportamento della soluzione.

 Per altre informazioni sull'Editor di codice, vedere [scrivere codice nell'editor del codice e testo](../ide/writing-code-in-the-code-and-text-editor.md). Per altre informazioni su come scrivere codice nei progetti di Office, vedere [scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md).

## <a name="properties-window"></a>Finestra Proprietà
 La finestra **Proprietà** mostra le proprietà per gli elementi del progetto selezionati in **Esplora soluzioni**e per gli elementi dell'interfaccia utente selezionati nella finestra di progettazione, ad esempio i controlli o il documento in un progetto a livello di documento. Alcune proprietà sono specifiche dell'applicazione e del documento, mentre altre sono identiche per tutti i progetti.

## <a name="data-sources-window"></a>Finestra Origini dati
 È possibile usare la finestra **Origini dati** all'interno dei progetti di Office a livello di documento per trascinare un'origine dati nel documento e creare un controllo associato all'origine dati. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche

- [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md)
- [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Proprietà nei progetti di Office](../vsto/properties-in-office-projects.md)
