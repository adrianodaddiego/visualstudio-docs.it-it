---
title: Segnalare un problema
description: Offre una panoramica dello strumento Segnala un problema e include stati e definizioni dei problemi
ms.date: 11/15/2018
ms.custom: seodec18
ms.topic: conceptual
author: seaniyer
ms.author: seiyer
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23ed63846eb11fd8eba95219aecaae3210e161fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62980143"
---
# <a name="overview-report-a-problem"></a>Panoramica: Segnalare un problema

Lo strumento Segnala un problema consente alla community degli sviluppatori di Visual Studio di segnalare i problemi. Ogni segnalazione diventa un elemento di lavoro nel sistema di progettazione Microsoft e consente all'utente di interagire direttamente con i team dei prodotti per contribuire a identificare e risolvere problemi importanti. Il feedback inviato con informazioni di diagnostica dettagliate è fondamentale per migliorare la famiglia di prodotti Visual Studio. La segnalazione dei problemi da parte degli utenti è estremamente apprezzata.

È anche possibile votare il feedback di altri membri della community per attirare maggiore attenzione su un problema e contribuire a risolverlo più velocemente.

## <a name="problem-status"></a>Stato del problema

Dopo la segnalazione di un problema, gli stati indicano la fase in cui si trovano le informazioni inviate nel proprio ciclo di vita. Durante l'esame del feedback, i team Microsoft ne impostano lo stato appropriato.  È possibile monitorare lo stato delle segnalazioni facendo riferimento agli stati indicati di seguito, insieme ai relativi indicatori di significato e colore.

![Stato Nuovo per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/New.jpg)

**Nuovo** indica che il bug o il problema è stato appena segnalato e non è stata ancora intrapresa alcuna azione.

- - -

![Stato Valutato per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/Triaged.jpg)

**Valutato** indica che i passaggi preliminari, ad esempio moderazione, traduzione e verifica iniziale dell'eventuale presenza di duplicati sono stati completati. Il ticket è stato inviato al team tecnico appropriato per l'esame.

- - -

![Stato In esame per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/UnderConsideration.jpg)

**In esame** indica che Microsoft sta esaminando il problema in termini di impatto sulla community e ne definirà la priorità di conseguenza. Se l'impatto sulla community non è ancora chiaro o significativo, Microsoft continuerà a monitorare il problema in questo stato.

- - -

![Stato Analisi in corso per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/UnderInvestigation.jpg)

**Analisi in corso** indica che i tecnici stanno analizzando attivamente il problema per trovare una soluzione.

- - -

![Stato Servono altre info per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/NeedMoreInfo.jpg)

**Servono altre info** indica che sono necessarie altre informazioni di diagnostica per continuare l'analisi.  [Informazioni su come rispondere alle richieste di altre informazioni](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed-need-more-info).

- - -

![Stato Risolto - Versione in sospeso per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/FixedPendingRelease.jpg)

**Risolto - Versione in sospeso** indica che è stata trovata una correzione per il problema e che questa sarà disponibile in una prossima anteprima o versione.  Quando la correzione viene resa disponibile in un'anteprima, il problema viene contrassegnato con un tag "corretto in" che specifica la versione dell'anteprima.

- - -

![Stato Chiuso - Risolto per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/ClosedFixed.jpg)

**Chiuso - Risolto** indica che è stata rilasciata una correzione per il problema. Il problema ora è anche contrassegnato con un tag "corretto in:" che specifica la versione di rilascio.

- - -

![Stato Chiuso - Duplicato per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/ClosedDuplicate.jpg)

**Chiuso - Duplicato** indica che il problema è già stato segnalato tramite un altro feedback. Verrà indicato il collegamento per visualizzare la segnalazione originale.

- - -

![Stato Chiuso - Priorità inferiore per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**Chiuso - Priorità inferiore** Per offrire il miglior valore a ogni sviluppatore della community, viene data priorità ai problemi con impatto più elevato sui clienti. Anche se al momento non è possibile risolvere questo particolare problema, tutto il feedback è prezioso e contribuisce a migliorare Visual Studio.

- - -

![Stato Chiuso - Non è un bug per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/ClosedNotaBug.jpg)

**Chiuso - Non è un bug** indica che è stato stabilito che la funzionalità segnalata al momento opera intenzionalmente nel modo segnalato.

- - -

![Stato Chiuso - Informazioni insufficienti per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

**Chiuso - Informazioni insufficienti** indica che le informazioni inviate non sono sufficienti per analizzare il problema. Quando le informazioni necessarie saranno disponibili, il feedback verrà di nuovo esaminato.

- - -

![Stato Chiuso - Altro prodotto per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

**Chiuso - Altro prodotto** indica è stato determinato che il problema è relativo a un altro prodotto. Vedere il commento di Microsoft per conoscere il prodotto esterno ed eventuali collegamenti correlati.

- - -

![Stato Chiuso - Da non correggere per la segnalazione di problemi nella community degli sviluppatori](../ide/media/ProblemStates/ClosedWontFix.jpg)

**Chiuso - Da non correggere** indica che il problema non verrà affrontato a causa di fattori quali la mancanza di allineamento con la direzione futura del prodotto o l'impatto sulla community. Per altre informazioni, vedere il commento di Microsoft.  Anche se non è possibile risolvere questo particolare problema, tutto il feedback è prezioso e contribuisce a migliorare Visual Studio.

- - -

## <a name="faq"></a>Domande frequenti

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>Come si può contribuire alla veloce risoluzione del problema?

È consigliabile usare la ricerca per assicurarsi che il problema che si sta per segnalare non sia già stato segnalato. Nel caso esista un elemento che corrisponde al problema, seguire e votare il ticket del problema.

 Inviare tutte le informazioni possibili per aiutare i team a riprodurre la propria esperienza.  Queste informazioni includono la procedura necessaria per riprodurre il problema, frammenti di codice, screenshot, registrazioni per la riproduzione del problema, file di log e altri elementi.  Vedere [come segnalare un problema in Visual Studio](./how-to-report-a-problem-with-visual-studio.md).

### <a name="how-is-my-feedback-prioritized"></a>Come viene definita la priorità del feedback?

Microsoft riceve dai clienti un numero elevato di problemi importanti. Per offrire il miglior valore a ogni sviluppatore della community, viene data priorità al feedback con l'impatto più elevato sulla community.

Nel caso in cui i membri del team non riuscissero a rispondere personalmente al feedback, è importante che l'utente sappia che le segnalazioni ricevute sono estremamente apprezzate. Tutto il feedback viene inviato al team appropriato.

Il tempo investito dall'utente per migliorare Visual Studio è realmente apprezzato.

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>Quali azioni è possibile intraprendere se la soluzione indicata non è soddisfacente?

I team fanno del loro meglio per diagnosticare e risolvere i problemi riscontrati dagli utenti. È possibile, tuttavia, che a volte l'utente non sia totalmente soddisfatto delle indicazioni fornite. Commentare il feedback e comunicare quali sono esattamente gli elementi non soddisfacenti. Il team cercherà in ogni modo di soddisfare le esigenze dell'utente.

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>Come viene comunicato lo stato di avanzamento del feedback inviato?

I team tecnici di Microsoft comunicano con l'utente aggiungendo commenti al ticket del feedback e modificandone lo stato. Quando cambia lo stato del ticket o viene pubblicato un commento verranno inviate notifiche tramite posta elettronica.  È possibile gestire la frequenza delle notifiche nelle impostazioni del profilo e delle preferenze nel sito della community degli sviluppatori.

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>Perché non è possibile aggiungere un problema relativo all'IDE di Visual Studio nel sito Web della community degli sviluppatori?

La segnalazione di un problema tramite Visual Studio consente di includere automaticamente le informazioni di diagnostica nella segnalazione. Queste informazioni sono essenziali perché offrono ai tecnici il contesto necessario per comprendere esattamente il problema e lavorare per risolverlo.

Nella segnalazione tramite Visual Studio è possibile condividere facilmente informazioni di diagnostica dettagliate, ad esempio file di log di grandi dimensioni, informazioni relative a un arresto anomalo, screenshot, registrazione per la riproduzione del problema e altri elementi che consentono di offrire soluzioni di alta qualità più velocemente.