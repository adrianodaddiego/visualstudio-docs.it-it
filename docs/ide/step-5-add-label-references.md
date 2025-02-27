---
title: 'Passaggio 5: Aggiungere riferimenti alle etichette'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc94660debb3d4668fb5d9d50e68466fe7631e5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968930"
---
# <a name="step-5-add-label-references"></a>Passaggio 5: Aggiungere riferimenti alle etichette
Il programma deve tenere traccia dei controlli Label scelti dal giocatore. Al momento il programma mostra tutte le etichette scelte dal giocatore, ma è possibile modificare questa impostazione. Una volta scelta la prima etichetta, il programma dovrebbe visualizzarne l'icona. Una volta scelta la seconda etichetta, il programma dovrebbe visualizzare entrambe le icone per un istante, quindi renderle nuovamente invisibili. Il programma terrà ora traccia del controllo Label scelto per primo e di quello scelto per secondo usando *variabili di riferimento*.

## <a name="to-add-label-references"></a>Per aggiungere riferimenti alle etichette

1. Aggiungere i riferimenti alle etichette nel form utilizzando il codice seguente.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     Queste variabili di riferimento sono simili alle istruzioni utilizzate in precedenza per aggiungere oggetti (ad esempio oggetti <xref:System.Windows.Forms.Timer>, <xref:System.Collections.Generic.List%601> e <xref:System.Random>) al form. Queste istruzioni, tuttavia, non comportano la visualizzazione di due controlli Label aggiuntivi nel modulo, perché in nessuna delle due istruzioni è usata la parola chiave `new`. Senza la parola chiave `new` non viene creato alcun oggetto. Per questo motivo `firstClicked` e `secondClicked` sono definiti variabili di riferimento: tengono semplicemente traccia di (o fanno riferimento a) oggetti Label.

     Quando una variabile non tiene traccia di un oggetto, viene impostata su un valore riservato: `null` in Visual C# e `Nothing` in Visual Basic. Quando il programma viene avviato, quindi, `firstClicked` e `secondClicked` vengono impostati su `null` o `Nothing`, il che significa che le variabili non tengono traccia di alcun oggetto.

2. Modificare il gestore dell'evento <xref:System.Windows.Forms.Control.Click> per usare la nuova variabile di riferimento `firstClicked`. Rimuovere l'ultima istruzione nel metodo del gestore degli eventi `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) e sostituirla con l'istruzione `if` seguente. Assicurarsi di includere il commento e l'intera istruzione `if`.

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Salvare ed eseguire il programma. Scegliere uno dei controlli etichetta; verrà visualizzata la relativa icona.

4. Scegliere il controllo etichetta successivo. Non accadrà nulla. Il programma sta già tenendo traccia della prima etichetta scelta dal giocatore, pertanto `firstClicked` non è uguale a `null` in Visual C# o `Nothing` in Visual Basic. Quando l'istruzione `if` controlla `firstClicked` per stabilire se sia uguale a `null` o `Nothing`, rileva che non lo è e non esegue le istruzioni contenute nell'istruzione `if`. Per cui soltanto la prima icona scelta diventa nera, mentre le altre icone sono invisibili, come mostrato nell'immagine seguente.

     ![Gioco di abbinamenti con un'icona visualizzata](../ide/media/express_tut4step5.png)
**Gioco di abbinamenti** con un'icona visualizzata

     Questa situazione verrà corretta nel passaggio successivo dell'esercitazione aggiungendo un controllo **Timer**.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 6: Aggiungere un timer](../ide/step-6-add-a-timer.md).

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 4: Aggiungere un gestore dell'evento Click a ogni etichetta](../ide/step-4-add-a-click-event-handler-to-each-label.md).
