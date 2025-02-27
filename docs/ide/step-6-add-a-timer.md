---
title: 'Passaggio 6: Aggiungere un timer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fcbf5c7361fe2035730f52807073092f3433e5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442045"
---
# <a name="step-6-add-a-timer"></a>Passaggio 6: Aggiungere un timer
Aggiungere ora un controllo <xref:System.Windows.Forms.Timer> al gioco di abbinamenti. Un timer resta in attesa per un determinato numero di millisecondi prima di generare un evento, detto *tick*. Si tratta di una condizione utile per avviare un'azione o ripeterne una a intervalli regolari. In questo caso, verrà utilizzato un timer per consentire ai giocatori di scegliere due icone e, se non corrispondono, nasconderle di nuovo dopo un breve periodo di tempo.

## <a name="to-add-a-timer"></a>Per aggiungere un timer

1. Nella casella degli strumenti in **Progettazione Windows Form** scegliere **Timer** (nella categoria **Componenti**) e quindi premere **INVIO** oppure fare doppio clic sul timer per aggiungere un controllo timer al modulo. L'icona del timer, denominata **Timer1**, verrà visualizzata nella parte inferiore del form, come illustrato nell'immagine seguente.

     ![Timer](../ide/media/express_timer.png)
**Timer**

    > [!NOTE]
    > Se la casella degli strumenti è vuota, assicurarsi di selezionare la finestra di progettazione del form e non il codice retrostante prima di aprire la casella degli strumenti.

2. Scegliere l'icona **Timer1** per selezionare il timer. Nella finestra **Proprietà** passare dalla visualizzazione degli eventi a quella delle proprietà. Impostare quindi la proprietà **Interval** del timer su **750**, ma lasciare la proprietà **Enabled** impostata su **False**. La proprietà **Interval** indica al timer il tempo di attesa tra eventi *tick* o il momento in cui viene attivato l'evento <xref:System.Windows.Forms.Timer.Tick>. Il valore 750 indica al timer di attendere tre quarti di secondo (750 millisecondi) prima di generare il relativo evento Tick. Il metodo <xref:System.Windows.Forms.Timer.Start> per avviare il timer verrà chiamato solo dopo che il giocatore avrà scelto la seconda etichetta.

3. Scegliere l'icona del controllo timer in **Progettazione Windows Form** e quindi premere **INVIO** o fare doppio clic sul timer per aggiungere un gestore dell'evento Tick vuoto. Sostituire il codice con quello indicato di seguito oppure immettere manualmente il codice seguente nel gestore eventi.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

     Il gestore dell'evento Tick effettua tre operazioni: in primo luogo verifica che il timer non sia in esecuzione chiamando il metodo <xref:System.Windows.Forms.Timer.Stop>. In seconda istanza, utilizza le due variabili di riferimento, `firstClicked` e `secondClicked`, per rendere nuovamente invisibili le due etichette scelte dal giocatore. Infine, reimposta le variabili di riferimento `firstClicked` e `secondClicked` su `null` in Visual C# e su `Nothing` in Visual Basic. Questo passaggio è importante, poiché è così che il programma si reimposta. Ora non sta tenendo traccia di alcun controllo <xref:System.Windows.Forms.Label> ed è nuovamente pronto per la scelta di un'etichetta da parte del giocatore.

    > [!NOTE]
    > Un oggetto Timer ha un metodo `Start()` che avvia il timer e un metodo `Stop()` che lo arresta. Impostando la proprietà **Enabled** del timer su **True** nella finestra **Proprietà**, il timer inizia a contare tick non appena il programma viene avviato. Se però si lascia questa proprietà impostata su **False**, il timer inizia a contare tick solo quando viene chiamato il metodo `Start()`. Di norma, un timer genera l'evento Tick ripetutamente tramite la proprietà **Interval** per stabilire quanti millisecondi attendere tra un ciclo e l'altro. Quando il metodo `Stop()` del timer viene chiamato nell'evento Tick, il timer passa in modalità *evento unico*: quando viene chiamato il metodo `Start()`, il timer attende l'intervallo specificato, genera un unico evento Tick e quindi si arresta.

4. Per vedere il nuovo timer in azione, andare nell'editor di codice e aggiungere il codice seguente all'inizio e alla fine del metodo del gestore dell'evento `label_Click()`. Si aggiunge l'istruzione `if` all'inizio e tre istruzioni alla fine; la parte rimanente del metodo resta invariata.

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Il codice all'inizio del metodo controlla se il timer è stato avviato controllando il valore della proprietà **Enabled**. In questo modo, se il giocatore sceglie il primo e il secondo controllo Label e il timer si avvia, l'eventuale scelta di una terza etichetta non genera alcuna azione.

     Il codice alla fine del metodo imposta la variabile di riferimento `secondClicked` in modo da tenere traccia del secondo controllo Label scelto dal giocatore e quindi imposta il colore dell'icona di tale etichetta su nero per renderla visibile. Quindi avvia il timer in modalità scatto unico, in modo che attenda 750 millisecondi prima di generare un singolo evento Tick. Il gestore dell'evento Tick del timer nasconde le due icone e reimposta le variabili di riferimento `firstClicked` e `secondClicked`. Il giocatore potrà così scegliere un'altra coppia di icone nel form.

5. Salvare ed eseguire il programma. Scegliere un'icona, che diventerà visibile.

6. Specificare un'altra icona. Questa verrà visualizzata brevemente, quindi entrambe le icone scompariranno. Ripetere più volte. Il form tiene ora traccia della prima e della seconda icona scelta e utilizza il timer per fare una pausa prima di far scomparire le icone.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 7: Mantenere le coppie visibili](../ide/step-7-keep-pairs-visible.md).

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 5: Aggiungere riferimenti alle etichette](../ide/step-5-add-label-references.md).
