---
title: Refactoring del codice
description: Ridefinizione del codice usando Visual Studio per Mac e le azioni rapide.
author: conceptdev
ms.author: crdun
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 48e290fddd1c4b7c95ac5e76cb6cf5908247e6f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62937852"
---
# <a name="refactoring"></a>Refactoring

Il refactoring del codice è un modo per riorganizzare, ristrutturare e rendere più chiaro il codice esistente garantendo che il comportamento complessivo del codice non cambi.

Il refactoring produce una codebase più integra e quindi più facile da usare, leggere e gestire per qualsiasi sviluppatore o utente che fa riferimento al codice.

L'integrazione di Visual Studio per Mac con Roslyn, la piattaforma di compilazione .NET open source Microsoft, consente più operazioni di refactoring.

## <a name="renaming"></a>Ridenominazione

Il comando di refactoring *Rinomina* può essere usato su qualsiasi identificatore del codice (ad esempio un nome di classe, un nome di proprietà e così via) per trovare tutte le occorrenze di tale identificatore e modificarle. Per rinominare un simbolo, fare clic con il pulsante destro del mouse su di esso e scegliere **Rinomina...** oppure usare il tasto di scelta rapida **Cmd (⌘) + R**:

![Voce di menu Rinomina](media/refactoring-renaming1.png)

Viene evidenziato il simbolo e tutti i relativi riferimenti. Quando si inizia a digitare un nuovo nome, verranno modificati automaticamente tutti i riferimenti nel codice. È possibile eseguire il commit delle modifiche premendo **INVIO**:

![Ridenominazione e identificatore](media/refactoring-renaming2.png)

## <a name="quick-actions"></a>Azioni rapide

Le azioni rapide consentono di generare codice, effettuarne il refactoring o modificarlo in altro modo con facilità tramite un'unica azione.

È possibile usare le azioni rapide per:

* Applicare una correzione del codice per la violazione di una regola dell'analizzatore del codice
* Eliminare la violazione di una regola dell'analizzatore del codice
* Effettuare un refactoring (ad esempio impostare come inline una variabile temporanea)
* Generare codice (ad esempio introdurre una variabile locale)

È possibile applicare le azioni rapide usando le icone a forma di lampadina ![icona lampadina](media/quick-actions-light-bulb-icon.png) o di cacciavite ![icona cacciavite](media/quick-actions-screwdriver-icon.png) oppure premendo **Opzione (⌥)**+**Invio** quando il cursore si trova su una riga di codice per il quale è disponibile un'azione. Si noterà una lampadina di errore ![icona lampadina errore](media/quick-actions-error-light-bulb-icon.png) se è presente una sottolineatura ondulata rossa che indica un errore e in Visual Studio è disponibile una correzione per tale errore.

È possibile che fornitori terzi offrano diagnostiche e suggerimenti personalizzati per qualsiasi linguaggio, ad esempio includendoli in SDK: le lampadine di Visual Studio si illumineranno in base a tali regole.

### <a name="quick-action-icons"></a>Icone azione rapida
L'icona visualizzata quando è disponibile un'azione rapida indica il tipo di correzione o refactoring disponibile. L'icona a forma di *cacciavite* ![icona cacciavite](media/quick-actions-screwdriver-icon.png) indica semplicemente che sono disponibili azioni per la modifica del codice, ma l'utente può scegliere di non usarle. L'icona a forma di *lampadina gialla* ![icona lampadina](media/quick-actions-light-bulb-icon.png) indica che sono disponibili azioni che si *devono* eseguire per migliorare il codice. L'icona a forma di *lampadina che indica un errore* ![icona lampadina di errore](media/quick-actions-error-light-bulb-icon.png) suggerisce che è disponibile un'azione che corregge un errore nel codice.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Per visualizzare una lampadina o un cacciavite

- Se è disponibile una correzione, le lampadine vengono visualizzate spontaneamente quando si passa il mouse sulla posizione di un errore.

   ![Lampadina con passaggio del puntatore del mouse](media/refactoring-lightbulb-hover.png)

- Le lampadine e i cacciavite vengono visualizzati nel margine sinistro dell'editor quando si sposta il punto di inserimento in una riga di codice per cui è disponibile un'azione rapida.

- Premere **Opzione (⌥)**+**Invio** in un punto qualsiasi di una riga per visualizzare un elenco di azioni rapide e refactoring disponibili.

![Visualizzare le voci di contesto](media/refactoring-context-action.png)

Passando il puntatore su una delle azioni di contesto, viene visualizzata un'anteprima di ciò che verrà aggiunto o rimosso dal codice.

![Voci di contesto visualizzate con Opzione+INVIO](media/refactoring-image2a.png)

Per abilitare queste opzioni, è necessario selezionare *Abilita l'analisi dell'origine dei file aperti* nelle opzioni **Visual Studio per Mac > Preferenze > Editor di testo > Analisi origine**:

![Abilitazione dell'analisi dell'origine](media/refactoring-options.png)

Ci sono più di 100 azioni che possono essere suggerite, che è possibile abilitare o disabilitare passando a **Visual Studio per Mac > Preferenze > Analisi origine > C# > Azioni codice** e selezionando o deselezionando la casella accanto all'azione:

![Azioni di analisi dell'origine C#](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Azioni rapide comuni

Altre informazioni sulle azioni rapide comuni sono disponibili nell'articolo sulle [azioni rapide comuni](/visualstudio/ide/common-quick-actions).

## <a name="source-analysis"></a>Analisi dell'origine

L'analisi dell'origine analizza il codice in tempo reale, sottolineando potenziali errori e violazioni di stile e offrendo correzioni automatiche come azioni di contesto.

È possibile visualizzare tutti i risultati dell'analisi dell'origine per qualsiasi file, in qualsiasi momento, visualizzando la barra di scorrimento sul lato destro dell'editor di testo:

![Barra laterale di analisi dell'origine](media/refactoring-image4a.png)

Se si fa clic sul cerchio nella parte superiore, è possibile scorrere ogni suggerimento, con i problemi più gravi visualizzati per primi. Passando il puntatore su un singolo risultato o una singola riga viene visualizzato il problema, che può essere risolto tramite azioni di contesto:

![Elemento di analisi dell'origine](media/refactoring-image5.png)

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Vedere anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)