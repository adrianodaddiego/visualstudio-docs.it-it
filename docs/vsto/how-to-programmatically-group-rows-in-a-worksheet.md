---
title: 'Procedura: A livello di programmazione le righe di gruppo in un foglio di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 269ecdb67fe58a5ad2aff6af63ba6ea45647811a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412612"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Procedura: A livello di programmazione le righe di gruppo in un foglio di lavoro
  È possibile raggruppare una o più righe intere. Per creare un gruppo in un foglio di lavoro, usare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 Se si aggiunge un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un progetto a livello di documento in fase di progettazione, è possibile usare il controllo a livello di codice, creare un gruppo. Nell'esempio seguente si presuppone che siano presenti tre <xref:Microsoft.Office.Tools.Excel.NamedRange> controlli sul foglio di lavoro: `data2001`, `data2002`, e `dataAll`. Ogni intervallo denominato fa riferimento a un'intera riga del foglio di lavoro.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Per creare un gruppo di controlli NamedRange in un foglio di lavoro

1. Raggruppare i tre intervalli denominati chiamando il <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> (metodo) di ogni intervallo. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Per separare le righe, chiamare il <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> (metodo).

## <a name="use-native-excel-ranges"></a>Usare gli intervalli di Excel nativi
 Nel codice si presuppone che siano presenti tre intervalli di Excel denominati `data2001`, `data2002`, e `dataAll` nel foglio di lavoro.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Per creare un gruppo di intervalli di Excel in un foglio di lavoro

1. Raggruppare i tre intervalli denominati chiamando il <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> (metodo) di ogni intervallo. Nell'esempio seguente si presuppone che siano presenti tre <xref:Microsoft.Office.Interop.Excel.Range> controlli denominati `data2001`, `data2002`, e `dataAll` nel foglio di lavoro stesso. Ogni intervallo denominato fa riferimento a un'intera riga del foglio di lavoro.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Per separare le righe, chiamare il <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> (metodo).

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
