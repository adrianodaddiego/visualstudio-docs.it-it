---
title: Accesso globale a oggetti nei progetti di Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7266e7fa26574332bcb343b552eea2b707a8672b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427949"
---
# <a name="global-access-to-objects-in-office-projects"></a>Accesso globale a oggetti nei progetti di Office
  Quando si crea un progetto di Office, Visual Studio genera automaticamente una classe denominata `Globals` nel progetto. È possibile usare la classe `Globals` per accedere ai diversi elementi del progetto in fase di esecuzione da qualsiasi codice del progetto.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="how-to-use-the-globals-class"></a>Come usare la classe Globals
 `Globals` è una classe statica che mantiene i riferimenti ad alcuni elementi del progetto. Usando la `Globals` , è possibile accedere agli elementi seguenti da qualsiasi codice del progetto in fase di esecuzione:

- Le classi `ThisWorkbook` e `Sheet`*n* in un progetto modello o cartella di lavoro di Excel. È possibile accedere a questi oggetti usando le proprietà `Globals.ThisWorkbook` e `Sheet`*n* .

- La classe `ThisDocument` in un progetto modello o documento di Word. È possibile accedere a questo oggetto stato usando la proprietà `Globals.ThisDocument` .

- Il `ThisAddIn` classe in un progetto di componente aggiuntivo VSTO. È possibile accedere a questo oggetto stato usando la proprietà `Globals.ThisAddIn` .

- Tutte le barre multifunzione del progetto che sono state personalizzate usando la finestra di progettazione della barra multifunzione. È possibile accedere alle barre multifunzione usando la proprietà `Globals.Ribbons` . Per altre informazioni, vedere [accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md).

- Tutte le aree del modulo di Outlook in un progetto di componente aggiuntivo VSTO di Outlook. È possibile accedere alle aree del modulo usando la proprietà `Globals.FormRegions` . Per altre informazioni, vedere [accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md).

- L'oggetto factory che consente di creare controlli della barra multifunzione e ospitare elementi in fase di esecuzione nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. È possibile accedere a questo oggetto stato usando la proprietà `Globals.Factory` . Questo oggetto è l'istanza di una classe che implementa una le interfacce seguenti:

  - <xref:Microsoft.Office.Tools.Factory>

  - <xref:Microsoft.Office.Tools.Excel.Factory>

  - <xref:Microsoft.Office.Tools.Outlook.Factory>

  - <xref:Microsoft.Office.Tools.Word.Factory>

  Ad esempio, è possibile usare la proprietà `Globals.Sheet1` per inserire testo in un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in `Sheet1` quando un utente fa clic su un pulsante del riquadro delle azioni in un progetto livello di documento per Excel.

  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]

## <a name="initialize-the-globals-class"></a>Inizializzare la classe Globals
 Il codice che tenta di usare il `Globals` classe prima che il documento o un componente aggiuntivo VSTO viene inizializzato potrebbe generare un'eccezione in fase di esecuzione. Ad esempio, l'utilizzo di `Globals` per la dichiarazione di una variabile a livello di classe potrebbe avere esito negativo perché la classe `Globals` potrebbe non essere inizializzata con i riferimenti a tutti gli elementi host prima della creazione di un'istanza dell'oggetto dichiarato.

> [!NOTE]
> La classe `Globals` non viene mai inizializzata in fase di progettazione, ma vengono create istanze di controllo nella finestra di progettazione. Ciò significa che se si crea un controllo utente che usa una proprietà del `Globals` classe dall'interno una classe del controllo utente, è necessario controllare se la proprietà restituisce **null** prima di provare a usare l'oggetto restituito.

## <a name="see-also"></a>Vedere anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Elemento host Document](../vsto/document-host-item.md)
- [Elemento host Workbook](../vsto/workbook-host-item.md)
- [Elemento host Worksheet](../vsto/worksheet-host-item.md)
- [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
