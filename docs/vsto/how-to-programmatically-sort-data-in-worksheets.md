---
title: 'Procedura: Ordinare i dati nei fogli di lavoro a livello di codice'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eeef19a04245d74d99050930cc3f66da627ffdd9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961784"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Procedura: Ordinare i dati nei fogli di lavoro a livello di codice
  È possibile ordinare i dati contenuti negli elenchi e negli intervalli del foglio di lavoro in fase di esecuzione. Il codice seguente ordina un intervallo a più colonne denominato `Fruits` in base ai dati nella prima colonna e quindi ai dati nella seconda colonna.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Ordinare i dati in una personalizzazione a livello di documento

### <a name="to-sort-data-in-a-namedrange-control"></a>Per ordinare i dati in un controllo NamedRange

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>. L'esempio seguente richiede un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `Fruits` in un foglio di lavoro. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]

   Inserire il codice seguente nel *Sheet1.vb* oppure *Sheet1.cs* ordinare i dati in un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo. Il codice presuppone l'esistenza di un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `fruitList` in un foglio di lavoro denominato `Sheet1`.

### <a name="to-sort-data-in-a-listobject-control"></a>Per ordinare i dati in un controllo ListObject

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> della proprietà <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> del controllo host <xref:Microsoft.Office.Tools.Excel.ListObject>.

     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]

## <a name="sort-data-in-a-vsto-add-in"></a>Ordinare i dati in un componente aggiuntivo VSTO

### <a name="to-sort-data-in-a-native-range"></a>Per ordinare i dati in un intervallo nativo

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> del controllo Excel nativo <xref:Microsoft.Office.Interop.Excel.Range>. L'esempio seguente richiede un controllo Excel nativo denominato `Fruits` in un foglio di lavoro.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]

### <a name="to-sort-data-in-a-listobject-control"></a>Per ordinare i dati in un controllo ListObject

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> della proprietà <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> del controllo Excel nativo <xref:Microsoft.Office.Interop.Excel.ListObject>. L'esempio seguente presuppone l'esistenza di un controllo Excel nativo <xref:Microsoft.Office.Interop.Excel.ListObject> denominato `fruitList` nel foglio di lavoro attivo.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Compilare a livello di codice automaticamente gli intervalli con dati modificati in modo incrementale](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Procedura: A livello di codice fare riferimento agli intervalli del foglio di lavoro nel codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Procedura: A livello di programmazione applicare stili agli intervalli in cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [ListObject (controllo)](../vsto/listobject-control.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
