---
title: 'Passaggio 6: Aggiungere un Timer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d6833e9735aa6a360ce0642e991bd019df347d16
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442500"
---
# <a name="step-6-add-a-timer"></a>Passaggio 6: Aggiungere un timer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aggiungere ora un controllo **Timer** al gioco delle coppie. Un timer resta in attesa per un determinato numero di millisecondi prima di generare un evento, detto *tick*. Si tratta di una condizione utile per avviare un'azione o ripeterne una a intervalli regolari. In questo caso, verrà utilizzato un timer per consentire ai giocatori di scegliere due icone e, se non corrispondono, nasconderle di nuovo dopo un breve periodo di tempo.  
  
### <a name="to-add-a-timer"></a>Per aggiungere un timer  
  
1. Nella casella degli strumenti in Progettazione Windows Form scegliere **Timer** (nella categoria **Componenti**) e quindi premere INVIO oppure fare doppio clic sul timer per aggiungere un controllo al form. L'icona del timer, denominata **Timer1**, verrà visualizzata nella parte inferiore del form, come illustrato nell'immagine seguente.  
  
     ![Timer](../ide/media/express-timer.png "Express_Timer")  
Timer  
  
    > [!NOTE]
    > Se la casella degli strumenti è vuota, assicurarsi di selezionare la finestra di progettazione del form e non il codice retrostante prima di aprire la casella degli strumenti.  
  
2. Scegliere l'icona **Timer1** per selezionare il timer. Nella finestra **Proprietà** passare dalla visualizzazione degli eventi a quella delle proprietà. Impostare quindi la proprietà **Interval** del timer su **750**, ma lasciare la proprietà **Enabled** impostata su **False**. La proprietà **Interval** indica al timer il periodo di attesa tra *tick* o il momento in cui deve essere generato l'evento Tick. Il valore 750 indica al timer di attendere tre quarti di secondo (750 millisecondi) prima di generare il relativo evento Tick. Il metodo `Start()` per avviare il timer verrà chiamato solo dopo che il giocatore avrà scelto la seconda etichetta.  
  
3. Scegliere l'icona del controllo Timer in Progettazione Windows Form e quindi premere INVIO o fare doppio clic sul timer per aggiungere un gestore eventi **Tick** vuoto. Sostituire il codice con quello indicato di seguito oppure immettere manualmente il codice seguente nel gestore eventi.  
  
     [!code-csharp[VbExpressTutorial4Step6#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial4Step6#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#7)]  
  
     Il gestore dell'evento Tick effettua tre operazioni: in primo luogo verifica che il timer non sia in esecuzione chiamando il metodo `Stop()`. In seconda istanza, utilizza le due variabili di riferimento, `firstClicked` e `secondClicked`, per rendere nuovamente invisibili le due etichette scelte dal giocatore. Infine, reimposta le variabili di riferimento `firstClicked` e `secondClicked` su `null` in Visual C# e su `Nothing` in Visual Basic. Questo passaggio è importante, poiché è così che il programma si reimposta. Ora non sta tenendo traccia di alcun controllo `Label` ed è nuovamente pronto per la scelta di un'etichetta da parte del giocatore.  
  
    > [!NOTE]
    > Un oggetto `Timer` dispone di un metodo `Start()` che avvia il timer e di un metodo `Stop()` che lo arresta. Impostando la proprietà **Enabled** del timer su **True** nella finestra **Proprietà**, il timer inizia a contare tick non appena il programma viene avviato. Se però si lascia questa proprietà impostata su **False**, il timer inizia a contare tick solo quando viene chiamato il metodo `Start()`. Di norma, un timer genera l'evento Tick ripetutamente tramite la proprietà **Interval** per stabilire quanti millisecondi attendere tra un ciclo e l'altro. Quando il metodo `Stop()` del timer viene chiamato nell'evento Tick, il timer passa in modalità *evento unico*: quando viene chiamato il metodo `Start()`, il timer attende l'intervallo specificato, genera un unico evento Tick e quindi si arresta.  
  
4. Per vedere il nuovo timer in azione, andare nell'editor di codice e aggiungere il codice seguente all'inizio e alla fine del metodo del gestore dell'evento `label_Click()`. Si aggiunge l'istruzione `if` all'inizio e tre istruzioni alla fine; la parte rimanente del metodo resta invariata.  
  
     [!code-csharp[VbExpressTutorial4Step6#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial4Step6#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#8)]  
  
     Il codice all'inizio del metodo controlla se il timer è stato avviato controllando il valore della proprietà **Enabled**. In tal modo, se il giocatore sceglie il primo e il secondo controllo `Label` e il timer si avvia, l'eventuale scelta di una terza etichetta non ha alcuna conseguenza.  
  
     Il codice alla fine del metodo imposta la variabile di riferimento `secondClicked` in modo da tenere traccia del secondo controllo `Label` scelto dal giocatore e quindi imposta il colore dell'icona di quell'etichetta su nero per renderla visibile. Quindi avvia il timer in modalità scatto unico, in modo che attenda 750 millisecondi prima di generare un singolo evento Tick. Il gestore eventi Tick del timer nasconde quindi le due icone e reimposta le variabili di riferimento `firstClicked` e `secondClicked`. Il giocatore potrà così scegliere un'altra coppia di icone nel form.  
  
5. Salvare ed eseguire il programma. Scegliere un'icona, che diventerà visibile.  
  
6. Specificare un'altra icona. Questa verrà visualizzata brevemente, quindi entrambe le icone scompariranno. Ripetere più volte. Il form tiene ora traccia della prima e della seconda icona scelta e utilizza il timer per fare una pausa prima di far scomparire le icone.  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 7: Mantenere le coppie visibili](../ide/step-7-keep-pairs-visible.md).  
  
- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 5: Aggiungere riferimenti alle etichette](../ide/step-5-add-label-references.md).
