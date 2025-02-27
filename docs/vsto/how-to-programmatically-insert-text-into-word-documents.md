---
title: 'Procedura: A livello di programmazione inserire testo nei documenti di Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e04f3b4420cc8f3b56eee304ae199cf87fa4a3a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412580"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Procedura: A livello di programmazione inserire testo nei documenti di Word
  Esistono tre modi principali per inserire il testo nei documenti di Microsoft Office Word:

- Inserire il testo in un intervallo.

- Sostituire il testo in un intervallo con il nuovo testo.

- Usare il metodo <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Selection> per inserire il testo in corrispondenza del cursore o della selezione.

> [!NOTE]
> È anche possibile inserire il testo nei controlli contenuto e nei segnalibri. Per altre informazioni, vedere [controlli di contenuto](../vsto/content-controls.md) e [Bookmark (controllo)](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="insert-text-in-a-range"></a>Inserire il testo in un intervallo
 Usare la proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> per inserire il testo in un documento.

### <a name="to-insert-text-in-a-range"></a>Per inserire il testo in un intervallo

1. Specificare un intervallo all'inizio di un documento e inserire il testo **New Text**.

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]

2. Selezionare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> , che è stato espanso da un carattere alla lunghezza del testo inserito.

     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]

## <a name="replace-text-in-a-range"></a>Sostituire il testo in un intervallo
 Se l'intervallo specificato contiene testo, tutto il testo dell'intervallo viene sostituito con il testo inserito.

### <a name="to-replace-text-in-a-range"></a>Per sostituire il testo in un intervallo

1. Creare un oggetto <xref:Microsoft.Office.Interop.Word.Range> costituito dai primi 12 caratteri nel documento.

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]

2. Sostituire questi caratteri con la stringa **New Text**.

     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]

3. Selezionare l'intervallo.

     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]

## <a name="insert-text-using-typetext"></a>Inserire il testo con TypeText
 Il metodo <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> inserisce il testo in corrispondenza della selezione. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> si comporta in modo diverso a seconda delle opzioni impostate nel computer dell'utente. Il codice nella procedura seguente dichiara una variabile dell'oggetto <xref:Microsoft.Office.Interop.Word.Selection> e disattiva l'opzione **Overtype** , se attivata. Se l'opzione **Overtype** è attivata, l'eventuale testo accanto al cursore viene sovrascritto.

### <a name="to-insert-text-using-the-typetext-method"></a>Per inserire il testo usando il metodo TypeText

1. Dichiarare una variabile dell'oggetto <xref:Microsoft.Office.Interop.Word.Selection> .

    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]

2. Disattivare l'opzione **Overtype** se attivata.

    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]

3. Verificare se la selezione corrente si trova in corrispondenza del punto di inserimento.

    In questo caso, il codice inserisce una frase usando <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>, quindi un segno di paragrafo usando il metodo <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> .

    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]

4. Il codice nel blocco **ElseIf** verifica che la selezione sia una selezione normale. In questo caso, un altro blocco **If** verifica che l'opzione **ReplaceSelection** sia attivata. In questo caso, il codice usa il metodo <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> della selezione per comprimere la selezione in un punto di inserimento all'inizio del blocco di testo selezionato. Inserire il testo e un segno di paragrafo.

    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]

5. Se la selezione non è un punto di inserimento o un blocco di testo selezionato, il codice nel blocco **Else** non esegue alcuna operazione.

    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]

   È anche possibile usare la <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> metodo per il <xref:Microsoft.Office.Interop.Word.Selection> oggetto, che riproduce la funzionalità del **Backspace** sulla tastiera. Tuttavia, per l'inserimento e la modifica del testo, l'oggetto <xref:Microsoft.Office.Interop.Word.Range> offre un maggiore controllo.

   L'esempio seguente mostra il codice completo. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]

## <a name="see-also"></a>Vedere anche
- [Procedura: A livello di programmazione formattare il testo nei documenti](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: A livello di programmazione estendere gli intervalli nei documenti](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
