---
title: 'Passaggio 3: Aggiungere un Timer del conto alla rovescia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d95708f940bfb12f67903f41d9f030a77877008d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442614"
---
# <a name="step-3-add-a-countdown-timer"></a>Passaggio 3: Aggiungere un timer per il conto alla rovescia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella terza parte di questa esercitazione si aggiungerà un timer per il conto alla rovescia per tenere traccia del numero di secondi che rimangono all'esecutore del quiz per completare l'operazione.  
  
> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-add-a-countdown-timer"></a>Per aggiungere un timer per il conto alla rovescia  
  
1. Aggiungere una variabile Integer denominata **timeLeft**, come nella procedura precedente. Il codice dovrebbe essere analogo al seguente.  
  
     [!code-csharp[VbExpressTutorial3Step3#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial3Step3#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#5)]  
  
     A questo punto è necessario un metodo che conti effettivamente i secondi, ad esempio un timer, e generi un evento dopo il periodo di tempo specificato.  
  
2. Nella finestra di progettazione spostare un controllo `Timer` dalla categoria **Componenti** della casella degli strumenti nel form.  
  
     Il controllo viene visualizzato nell'area grigia nella parte inferiore della finestra di progettazione.  
  
3. Nel form scegliere l'icona **timer1** appena aggiunta e impostarne la proprietà **Interval** su **1000**.  
  
     Poiché il valore di intervallo è espresso in millisecondi, un valore pari a 1000 fa sì che l'evento Tick venga generato ogni secondo.  
  
4. Nel form fare doppio clic sul controllo Timer o sceglierlo e premere INVIO.  
  
     Viene visualizzato l'editor di codice contenente il metodo per il gestore dell'evento Tick appena aggiunto.  
  
5. Aggiungere le istruzioni seguenti al metodo del nuovo gestore eventi.  
  
     [!code-csharp[VbExpressTutorial3Step3#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial3Step3#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#6)]  
  
     In base all'elemento aggiunto, ogni secondo il timer controlla se il tempo è scaduto determinando se la variabile Integer **timeLeft** è maggiore di 0. In caso positivo, rimane ancora tempo. Il timer sottrae prima 1 da timeLeft, quindi aggiorna la proprietà **Text** del controllo `timeLabel` per mostrare all'esecutore del quiz quanti secondi rimangono.  
  
     Se non rimane tempo, il timer si arresta e il testo del controllo `timeLabel` viene modificato in modo da visualizzare **Tempo scaduto**. Una finestra di messaggio informa che il quiz è terminato e viene rivelata la risposta, in questo caso mediante l'aggiunta di addend1 e addend2. La proprietà **Enabled** del controllo `startButton` è impostata su `true` per consentire all'esecutore del quiz di avviare un altro quiz.  
  
     Si è appena aggiunta un'istruzione `if else`, che rappresenta il modo in cui si comunica ai programmi di prendere decisioni. Di seguito è riportato un esempio di istruzione `if else`.  
  
    > [!NOTE]
    > L'esempio seguente viene fornito a scopo illustrativo; non aggiungerlo al progetto.  
  
    ```vb  
    If (something that your program will check) Then  
        ' One or more statements that will run  
        ' if what the program checked is true.   
    Else  
        ' One or more statements that will run  
        ' if what the program checked is false.  
    End If  
    ```  
  
    ```csharp  
    if (something that your program will check)  
    {  
        // One or more statements that will run  
        // if what the program checked is true.   
    }  
    else  
    {  
        // One or more statements that will run  
        // if what the program checked is false.  
    }  
    ```  
  
     Esaminare attentamente l'istruzione aggiunta al blocco `else` per visualizzare la risposta al problema di addizione.  
  
     [!code-csharp[VbExpressTutorial3Step3#24](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#24)]
     [!code-vb[VbExpressTutorial3Step3#24](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#24)]  
  
     L'istruzione `addend1 + addend2` somma i valori delle due variabili. La prima parte (`sum.Value`) utilizza la proprietà **Value** del controllo `NumericUpDown` della somma per visualizzare la risposta corretta. La stessa proprietà verrà utilizzata successivamente per controllare le risposte al quiz.  
  
     Un controllo `NumericUpDown` facilita l'immissione di numeri da parte degli esecutori del quiz ed è per questo motivo che si usa il controllo per le risposte ai problemi matematici. Tutte le risposte potenziali sono numeri interi compresi tra 0 e 100. Mantenendo i valori predefiniti per le proprietà **Minimum**, **Maximum** e **DecimalPlaces**, si evita che gli esecutori del quiz immettano numeri decimali, negativi o troppo alti. Se si desidera consentire agli esecutori del quiz di immettere 3,141 ma non 3,1415, è possibile impostare la proprietà **DecimalPlaces** su 3.  
  
6. Aggiungere tre righe alla fine del metodo `StartTheQuiz()`, in modo che il codice sia analogo al seguente.  
  
     [!code-csharp[VbExpressTutorial3Step3#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial3Step3#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#7)]  
  
     A questo punto, all'avvio del quiz la variabile **timeLeft** è impostata su 30 e la proprietà **Text** del controllo `timeLabel` è impostata su 30 secondi. Il metodo `Start()` del controllo `Timer` avvia il conto alla rovescia. La risposta non viene ancora controllata. Ciò avverrà in seguito.  
  
7. Salvare il programma, eseguirlo e scegliere il pulsante **Avvio** del form.  
  
     Il timer avvia il conto alla rovescia. Quando il tempo è scaduto, il quiz termina e viene visualizzata la risposta. Nella figura seguente viene illustrato il quiz in corso.  
  
     ![Quiz matematico in corso](../ide/media/express-addcountdown.png "Express_AddCountdown")  
Quiz matematico in corso  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 4: Aggiungere il metodo CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md).  
  
- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 2: Creare un problema con addizione casuale](../ide/step-2-create-a-random-addition-problem.md).
