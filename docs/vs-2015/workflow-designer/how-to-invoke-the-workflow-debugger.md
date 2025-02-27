---
title: 'Procedura: Richiama il Debugger del flusso di lavoro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a3d5033bc9953aa00efb950eabce5e7346952f9d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444149"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Procedura: Richiamare il debugger del flusso di lavoro
Generalmente si esegue il debug dei flussi di lavoro nello stesso modo in cui si esegue il debug di programmi scritti negli altri linguaggi di programmazione di Visual Studio. È possibile avviare il debugger del flusso di lavoro nei modi seguenti:  
  
- Selezionare **Connetti a processo** nel **Debug** menu per selezionare il processo host in esecuzione per l'istanza del flusso di lavoro. La procedura è identica a quella di collegamento a un processo host nel codice gestito.  
  
- Premere **F5** per avviare l'esecuzione di un'istanza del flusso di lavoro o per continuare a eseguire dopo aver raggiunto un punto di interruzione.  
  
- Usare debug remoto. Per informazioni sul debug remoto, vedere [come: Abilitare il debug remoto](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    > Se l'applicazione del flusso di lavoro ha come destinazione x86 architettura ed è ospitato in un computer che eseguono un sistema operativo a 64 bit, il debug remoto non funzionerà a meno che non [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] è installato nel computer remoto o la destinazione dell'applicazione del flusso di lavoro è stata modificata in **Qualsiasi CPU**.  
  
### <a name="stepping-through-code"></a>Esecuzione di codice istruzione per istruzione  
  
- **Passaggio**: È possibile avanzare in un'attività usando **F11**. Il debugger avanza in qualsiasi gestore definito. Se nessun gestore è definito, viene eseguita l'istruzione/routine dell'attività oppure, con CompositeActivity contenenti altre attività, viene eseguita l'istruzione della prima attività in stato di esecuzione.  
  
- **Esci da istruzione:** È possibile uscire un'attività usando **MAIUSC+F11**. Uscendo da un'istruzione/routine di un'attività, l'attività corrente e tutte le relative attività di pari livello vengono eseguite fino al completamento. Il debugger reimposta quindi il padre dell'attività corrente. Uscendo da un gestore del codice, il debugger reimposta l'attività alla quale è associato il gestore.  
  
- **Esegui istruzione/routine**: È possibile passare a un'attività usando **F10**. Quando viene eseguita l'istruzione/routine di un oggetto CompositeActivity, il debugger reimposta il primo figlio eseguibile del CompositeActivity. Quando viene eseguita l'istruzione/routine di un attività diversa da CompositeActivity, ad esempio <xref:System.Activities.Statements.Assign>, il debugger esegue l'attività e i gestori ad essa associati e reimposta l’attività successiva. Se l'attività eseguita è l'ultima attività figlio di un oggetto CompositeActivity, dopo l'esecuzione il debugger reimposterà l'attività padre.  
  
### <a name="debugging-with-f5"></a>Debug con F5  
  
- Se si sta compilando un progetto di applicazione Console flusso di lavoro, è sufficiente premere **F5** per avviare il debug nell'applicazione e del flusso di lavoro. Se si compila una libreria attività autonomamente, è necessario usare come progetto di avvio un'applicazione host eseguibile. Per impostare un progetto di avvio **Esplora soluzioni**, fare clic sul nome del progetto dell'host e selezionare **imposta come progetto di avvio**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)