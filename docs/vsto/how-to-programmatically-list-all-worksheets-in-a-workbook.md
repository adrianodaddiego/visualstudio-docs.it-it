---
title: 'Procedura: A livello di programmazione elencare tutti i fogli di lavoro in una cartella di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2153091b2b2abae05bf6f6c7856d2fa6d43f8967
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812423"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Procedura: A livello di programmazione elencare tutti i fogli di lavoro in una cartella di lavoro
  La classe <xref:Microsoft.Office.Interop.Excel.Workbook> fornisce un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheets>. Questo oggetto contiene una raccolta di tutti gli oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet> presenti nella cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Per elencare tutti i fogli di lavoro presenti in una cartella di lavoro in una personalizzazione a livello di documento

1. Scorrere la raccolta <xref:Microsoft.Office.Interop.Excel.Worksheets> e inviare il nome di ciascun foglio a un offset di cella determinato da un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>.

     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Per elencare tutti i fogli di lavoro presenti in una cartella di lavoro in un componente aggiuntivo VSTO

1. Scorrere la raccolta <xref:Microsoft.Office.Interop.Excel.Worksheets> e inviare il nome di ciascun foglio a un offset di cella determinato da un oggetto <xref:Microsoft.Office.Interop.Excel.Range>.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: A livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Procedura: A livello di programmazione spostare fogli di lavoro all'interno di cartelle di lavoro](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
