---
title: Azioni rapide, lampadine e cacciavite
ms.date: 03/28/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1a08e54025ac0826b88a3d3fcee299beef245d13
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62811997"
---
# <a name="quick-actions"></a>Azioni rapide

Le azioni rapide consentono di generare codice, effettuarne il refactoring o modificarlo in altro modo con facilità tramite un'unica azione. Sono disponibili azioni rapide per C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) e i file di codice Visual Basic. Alcune azioni sono specifiche per un linguaggio e altre si applicano a tutti i linguaggi.

È possibile usare le azioni rapide per:

- Applicare una correzione del codice per la violazione di una regola dell'[analizzatore del codice](../code-quality/roslyn-analyzers-overview.md)

- [Eliminare](../code-quality/use-roslyn-analyzers.md#suppress-violations) la violazione di una regola dell'analizzatore del codice

- Effettuare un refactoring (ad esempio [impostare come inline una variabile temporanea](../ide/reference/inline-temporary-variable.md))

- Generare codice (ad esempio [introdurre una variabile locale](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Refactoring (Visual Studio per Mac)](/visualstudio/mac/refactoring).

Le azioni rapide possono essere applicate usando le icone a forma di lampadina ![icona lampadina](media/light-bulb-icon.png) o di cacciavite ![icona cacciavite](media/screwdriver-icon.png) oppure premendo **CTRL**+**.** quando il cursore si trova su una riga di codice per la quale è disponibile un'azione. Si noterà una lampadina di errore ![icona lampadina errore](media/error-light-bulb-icon.png) se è presente una sottolineatura ondulata rossa che indica un errore e in Visual Studio è disponibile una correzione per tale errore.

È possibile che fornitori terzi offrano diagnostiche e suggerimenti personalizzati per qualsiasi linguaggio, ad esempio includendoli in SDK: le lampadine di Visual Studio compariranno in base a tali regole.

## <a name="icons"></a>Icone

L'icona visualizzata quando è disponibile un'azione rapida indica il tipo di correzione o refactoring disponibile. L'icona a forma di *cacciavite* ![icona cacciavite](media/screwdriver-icon.png) indica semplicemente che sono disponibili azioni per la modifica del codice, ma l'utente può scegliere di non usarle. L'icona a forma di *lampadina gialla* ![icona lampadina](media/light-bulb-icon.png) indica che sono disponibili azioni che si *devono* eseguire per migliorare il codice. L'icona a forma di *lampadina che indica un errore* ![icona lampadina di errore](media/error-light-bulb-icon.png) suggerisce che è disponibile un'azione che corregge un errore nel codice.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Per visualizzare una lampadina o un cacciavite

Se è disponibile una correzione, le lampadine compaiono:

- Quando si passa il puntatore del mouse sulla posizione di un errore

   ![Lampadina con passaggio del puntatore del mouse](../ide/media/vs2015_lightbulb_hover.png)

- Nel margine sinistro dell'editor quando si sposta il punto di inserimento (cursore) sulla riga di codice applicabile

È anche possibile premere **CTRL**+**.** in un punto qualsiasi di una riga per visualizzare un elenco di azioni rapide e refactoring disponibili.

Per vedere le potenziali correzioni, selezionare la freccia GIÙ accanto alla lampadina o il collegamento **Mostra correzioni potenziali**. Viene visualizzato un elenco delle azioni rapide disponibili.

![Lampadina espansa](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Vedere anche

- [Generazione di codice in Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Azioni rapide comuni](../ide/common-quick-actions.md)
- [Stili di codice e azioni rapide](../ide/code-styles-and-quick-actions.md)
- [Codice di scrittura e refactoring (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refactoring (Visual Studio per Mac)](/visualstudio/mac/refactoring)