---
title: Uso della finestra attività | Microsoft Docs
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b32dc6372a6ce4983e9bd11e05a4a662d0ad44ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901593"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Uso della finestra attività (C#, Visual Basic, C++)

La finestra **Attività** è simile alla finestra **Thread**, l'unica differenza è che mostra informazioni sugli oggetti <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class) o [WinJS.Promise](/previous-versions/windows/apps/br211867(v=win.10)) e non su ogni thread. Analogamente ai thread, le attività rappresentano operazioni asincrone eseguibili simultaneamente; tuttavia, più attività possono essere eseguite nello stesso thread.

Nel codice gestito è possibile usare la finestra **Attività** quando si utilizzano gli oggetti <xref:System.Threading.Tasks.Task?displayProperty=fullName> o con le parole chiave **await** e **async** (**Await** e **Async** in Visual Basic). Per altre informazioni sulle attività nel codice gestito, vedere [programmazione parallela](/dotnet/standard/parallel-programming/index).

Nel codice nativo, è possibile usare la finestra **Attività** quando si utilizzano [gruppi di attività](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algoritmi paralleli](/cpp/parallel/concrt/parallel-algorithms), [agenti asincroni](/cpp/parallel/concrt/asynchronous-agents) e [attività leggere](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Per altre informazioni sulle attività nel codice nativo, vedere [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime).

In JavaScript, è possibile utilizzare la finestra attività quando si lavora con promise `.then` codice. Visualizzare [programmazione asincrona in JavaScript (app UWP)](/previous-versions/windows/apps/hh700330(v=win.10)) per altre informazioni.

La finestra **Attività** può essere usata ogni volta che ci si interrompe l'esecuzione nel debugger. È possibile accedere a esso nel menu **Debug** scegliendo **Finestre** e facendo clic su **Attività**. Nell'illustrazione seguente viene mostrata la finestra **Attività** nella modalità predefinita.

![Finestra attività](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> Nel codice gestito, un <xref:System.Threading.Tasks.Task> che ha uno stato [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>), oppure [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) potrebbe non essere visualizzato nei **attività** finestra quando i thread gestiti si trovano nello stato sospensione o join.

## <a name="tasks-column-information"></a>Informazioni nelle colonne della finestra Attività

Nelle colonne della finestra **Attività** vengono visualizzate le informazioni seguenti.

|Nome colonna|Descrizione|
|-----------------|-----------------|
|**Flag**|Mostra quali attività sono contrassegnate e consente di impostare o rimuovere un flag per un'attività.|
|**Icone**|Una freccia gialla indica l'attività corrente. L'attività corrente è l'attività in primo piano nel thread corrente.<br /><br /> Una freccia bianca indica l'attività di interruzione, vale a dire l'attività corrente al momento della chiamata del debugger.<br /><br /> L'icona di sospensione indica un'attività bloccata dall'utente. È possibile bloccare e sbloccare un'attività facendovi clic sopra con il pulsante destro del mouse nell'elenco.|
|**ID**|Numero fornito dal sistema per l'attività. Nel codice nativo, è l'indirizzo dell'attività.|
|**Status**|Stato corrente (pianificato, attivo, bloccato, deadlock, in attesa o completato) dell'attività. Un'attività pianificata è un'attività che non è stata ancora eseguita, pertanto non dispone ancora di uno stack di chiamate, un thread assegnato o informazioni correlate.<br /><br /> Un'attività attiva è un'attività che stava eseguendo codice prima dell'accesso al debugger.<br /><br /> Un'attività in attesa o bloccata è quello che viene bloccata perché è in attesa di un evento venga segnalato, un blocco deve essere rilasciato o fine di un'altra attività.<br /><br /> Un'attività in deadlock è un'attività in attesa il cui thread è in deadlock con un altro thread.<br /><br /> Passare il mouse sul **stato** cella di un'attività in deadlock o in attesa visualizzare altre informazioni sul blocco. **Avviso:**  La finestra **Attività** segnala un deadlock solo per un'attività bloccata che usa una primitiva di sincronizzazione supportata da WCT (Wait Chain Traversal). Ad esempio, per un deadlock <xref:System.Threading.Tasks.Task> oggetto, che utilizza WCT, il debugger viene segnalato **-in deadlock Awaiting**. Per un'attività in deadlock gestita dal runtime di concorrenza, che non utilizza WCT, viene visualizzato il messaggio **In attesa**. Per altre informazioni su WCT, vedere [Wait Chain Traversal](/windows/desktop/Debug/wait-chain-traversal).|
|**Ora di inizio**|Ora in cui l'attività è diventata attiva.|
|**Durata**|Numero di secondi durante i quali l'attività è rimasta attiva.|
|**Tempo di completamento**|Ora in cui l'attività è stata completata.|
|**Posizione**|Percorso corrente nello stack di chiamate dell'attività. Passare il mouse su questa cella per visualizzare l'intero stack di chiamate dell'attività. Le attività pianificate non presentano alcun valore in questa colonna.|
|**Task**|Metodo iniziale ed eventuali argomenti passati all'attività quando è stata creata.|
|**AsyncState**|Per il codice gestito, lo stato dell'attività. Per impostazione predefinita, questa colonna è nascosta. Per visualizzarla, aprire il menu di scelta rapida per una delle intestazioni di colonna. Scegliere **Colonne**, **AsyncState**.|
|**Padre**|ID dell'attività che ha creato questa attività. Se la cella è vuota significa che l'attività non dispone di un'attività padre. Questo dato è applicabile ai soli programmi gestiti.|
|**Assegnazione thread**|ID e nome del thread nel quale viene eseguita l'attività.|
|**AppDomain**|Dominio applicazione nel quale viene eseguita l'attività, in caso di codice gestito.|
|**task_group**|Indirizzo dell'oggetto [task_group](/cpp/parallel/concrt/reference/task-group-class) che ha pianificato l'attività, in caso di codice nativo. Per gli agenti asincroni e le attività leggere, questa colonna viene impostata su 0.|
|**Processo**|ID del processo in cui viene eseguita l'attività.|

 Per aggiungere colonne alla visualizzazione, fare clic con il pulsante destro del mouse su un'intestazione di colonna e selezionare le colonne desiderate. Per rimuovere le colonne, annullare le selezioni. È possibile inoltre riordinare le colonne trascinandole a sinistra o a destra. Nell'illustrazione seguente viene mostrato il menu di scelta rapida delle colonne.

 ![Menu di scelta rapida visualizza nella finestra attività](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Ordinamento delle attività
 Per ordinare le attività in base ai criteri delle colonne, fare clic sull'intestazione di colonna. Ad esempio, facendo i **ID** intestazione di colonna, è possibile ordinare le attività da un ID attività: 1,2,3,4,5 e così via. Per invertire l'ordine, fare nuovamente clic sull'intestazione. La colonna di ordinamento e l'ordinamento correnti sono indicati da una freccia nella colonna.

## <a name="grouping-tasks"></a>Raggruppamento delle attività
 È possibile raggruppare le attività in base a una qualsiasi colonna nella visualizzazione elenco. Ad esempio, facendo clic con il pulsante destro del mouse sull'intestazione di colonna **Stato** e scegliendo **Raggruppa per** > **[*stato*]**, è possibile raggruppare tutte le attività con lo stesso stato. Ad esempio, è possibile visualizzare rapidamente in attesa di attività in modo che è possibile concentrarsi sul motivo del blocco. È possibile inoltre comprimere un gruppo di poco interesse durante la sessione di debug. Allo stesso modo, è possibile raggruppare in base alle altre colonne. Per contrassegnare o rimuovere il contrassegno di un gruppo, è sufficiente fare clic sul pulsante accanto all'intestazione del gruppo. Nell'illustrazione seguente viene mostrata la finestra **Attività** nella modalità raggruppata.

 ![Modalità raggruppata nella finestra attività](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Visualizzazione padre/figlio
 (Questa visualizzazione è disponibile solo per codice gestito). Facendo clic con il **lo stato** intestazione di colonna e scegliendo **Raggruppa** > **padre**, è possibile modificare l'elenco di attività per una visualizzazione gerarchica, in cui ogni attività figlio è un nodo secondario che può essere visualizzato o nascosto sotto il relativo elemento padre.

## <a name="flagging-tasks"></a>Contrassegno delle attività
 È possibile contrassegnare il thread di attività in cui viene eseguita un'attività selezionando l'attività elenco elemento e scegliendo **imposta Flag del Thread assegnato** dal menu di scelta rapida oppure facendo clic sull'icona del flag nella prima colonna. Se si contrassegnano diverse attività, sarà successivamente possibile ordinare in base alla colonna del contrassegno in modo da portare tutte le attività contrassegnate in cima e potersi concentrare su di esse. È inoltre possibile usare la finestra **Stack in parallelo** per visualizzare solo le attività con contrassegno. In questo modo si possono filtrare le attività di poco interesse per il debug. I contrassegni non vengono salvati in modo permanente tra una sessione di debug e l'altra.

## <a name="freezing-and-thawing-tasks"></a>Blocco e sblocco delle attività
 Per bloccare il thread nel quale viene eseguita un'attività, fare clic con il pulsante destro del mouse sull'elemento dell'elenco di attività e scegliere **Blocca thread assegnato**. Se un'attività è già bloccata, il comando è **Sblocca thread assegnato**. Quando si blocca un thread, questo non verrà eseguito nel momento in cui si proseguirà con l'esecuzione del codice dopo il punto di interruzione corrente. Il **bloccare tutti i thread, ma questo uno** comando Blocca tutti i thread ad eccezione di quello che è in esecuzione l'elemento elenco attività.

 Nell'illustrazione seguente vengono mostrate le altre voci di menu per ogni attività.

 ![Menu thread collegamenti nella finestra attività](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Passare l'attività attiva o il Frame

Il **passa all'attività** comando sospende l'attività corrente di attività attiva. Il **passa al Frame** comando rende lo stack selezionato frame lo stack frame attivo. Il contesto di debug attiva dell'attività corrente o il frame dello stack selezionate.

## <a name="see-also"></a>Vedere anche

- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Debug di codice gestito](../debugger/debugging-managed-code.md)
- [Programmazione parallela](/dotnet/standard/parallel-programming/index)
- [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime)
- [Uso della finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)
- [Procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)