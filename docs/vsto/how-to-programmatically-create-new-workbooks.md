---
title: 'Procedura: A livello di codice crea nuove cartelle di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4404541327aa5e42290847784f9faf3b35b51054
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412451"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Procedura: A livello di codice crea nuove cartelle di lavoro
  Una cartella di lavoro creata a livello di codice costituisce un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> nativo e non un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> per un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> in un progetto a livello di componente aggiuntivo VSTO. Per altre informazioni, vedere [estendere documenti Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>Per creare una nuova cartella di lavoro

1. Usare il metodo <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Workbooks> .

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > È possibile creare una cartella di lavoro basata su un modello diverso da quello predefinito. Passare il modello da usare come parametro al metodo <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.

## <a name="see-also"></a>Vedere anche
- [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: A livello di codice aprire cartelle di lavoro](../vsto/how-to-programmatically-open-workbooks.md)
- [Procedura: A livello di programmazione salvare cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: A livello di programmazione chiudere cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
