---
title: Elemento host Worksheet
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e4a5287648d515d1aca340ab55d5f21b494610b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814731"
---
# <a name="worksheet-host-item"></a>Elemento host Worksheet
  L'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> è un tipo che estende il tipo <xref:Microsoft.Office.Interop.Excel.Worksheet> dall'assembly di interoperabilità primario per Excel. L'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> offre tutte le stesse proprietà, gli stessi metodi ed eventi di un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> , ma espone anche eventi aggiuntivi e funge da contenitore per i controlli host e quelli Windows Form.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Nei progetti a livello di documento è possibile aggiungere elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> al progetto in fase di progettazione. Nei progetti di componente aggiuntivo VSTO, è possibile generare <xref:Microsoft.Office.Tools.Excel.Worksheet> ospitare elementi in fase di esecuzione.

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Comprendere elementi host worksheet nei progetti a livello di documento
 Quando si crea un progetto a livello di documento per Excel, Visual Studio automaticamente crea tre elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> nel progetto. I nomi predefiniti dei fogli di lavoro sono `Sheet1`, `Sheet2`e `Sheet3`. Se si crea un progetto in base a una cartella di lavoro esistente, il numero di elementi host dipende dal numero di fogli di lavoro nella cartella di lavoro.

 Queste classi del foglio di lavoro offrono l'accesso ai membri dell'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> per eseguire attività di base nella personalizzazione, come ad esempio la modifica dei contenuti in un foglio di lavoro. È anche possibile usare queste classi per aggiungere controlli ai fogli di lavoro. Con la combinazione di set di controlli diversi e con la scrittura di codice, è possibile associare i controlli ai dati, raccogliere le informazioni relative all'utente e rispondere alle azioni utente. Per altre informazioni, vedere [programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).

 Le classi del foglio di lavoro offrono un punto di partenza per iniziare a scrivere codice nel progetto. Dal momento che la classe offre tutte le stesse proprietà, gli stessi metodi ed eventi dell'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nell'assembly di interoperabilità primario per Excel, è possibile usare anche queste classi per accedere al modello a oggetti di Excel. Per altre informazioni, vedere [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md).

 Nei progetti a livello di documento è possibile aggiungere elementi host <xref:Microsoft.Office.Tools.Excel.Worksheet> aggiuntivi al progetto in fase di progettazione aggiungendo un nuovo foglio di lavoro nella finestra di progettazione.

### <a name="rename-worksheets"></a>Rinominare i fogli di lavoro
 In un progetto a livello di documento è possibile rinominare i fogli di lavoro nella finestra di progettazione di Visual Studio, ma in tal modo viene modificato solo il nome visualizzato del foglio di lavoro. Il nome a livello di codice rimane il nome predefinito del foglio di lavoro. Se si rinomina il foglio di lavoro nella finestra **Proprietà** , viene modificato solo il nome a livello di codice.

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Limitazioni dell'elemento host foglio di lavoro nei progetti a livello di documento
 È possibile creare nuovi <xref:Microsoft.Office.Tools.Excel.Worksheet> elementi in fase di esecuzione in un progetto a livello di documento host. Se si crea un nuovo foglio di lavoro di Excel in fase di esecuzione, sarà di tipo <xref:Microsoft.Office.Interop.Excel.Worksheet>. Dal momento che non si tratta di un elemento host, non può contenere alcun controllo host o controllo Windows Form. Per altre informazioni sulla creazione di documenti in fase di esecuzione, vedere [come: A livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Comprendere elementi host worksheet nei progetti di componente aggiuntivo VSTO
 Nei progetti a livello di applicazione è possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione per qualsiasi foglio di lavoro in Excel. È possibile usare l'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> per aggiungere controlli al foglio di lavoro associato oppure per gestire eventi che non sono disponibili su oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet> .

 Per generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>, usare il metodo `GetVstoObject`. Per altre informazioni, vedere [estendere documenti Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Vedere anche
- [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)
- [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Elemento host Workbook](../vsto/workbook-host-item.md)
- [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
