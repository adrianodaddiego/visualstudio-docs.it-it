---
title: 'DA0024: Tempo di CPU GC eccessivo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d40377c28e0987ac902ab8aa5cf778715eb899cd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435842"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Tempo CPU GC eccessivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id regola | DA0024 |  
| Categoria di |. Utilizzo di NET Framework |  
| Metodo di profilatura | Tutti i |  
| Messaggio | % Time in GC è molto elevata. Indica un sovraccarico di Garbage Collection.|  
| Tipo di regola | Avviso |  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="cause"></a>Causa  
 I dati sulle prestazioni del sistema raccolti durante la profilatura indicano che il tempo impiegato in Garbage Collection è eccessivamente elevato rispetto al tempo di elaborazione totale dell'applicazione.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Common Language Runtime (CLR) di Microsoft .NET offre un meccanismo di gestione automatica della memoria che usa un Garbage Collector per recuperare memoria da oggetti che non vengono più usati dall'applicazione. Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata. Le variabili locali, ad esempio, dovrebbero essere di breve durata. Gli oggetti appena creati vengono avviati in generazione 0 (gen 0), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora usati dall'applicazione.  
  
 Gli oggetti in generazione 0 vengono raccolti frequentemente e in genere in modo molto efficace. Gli oggetti in generazione 1 vengono raccolti meno frequentemente e in modo meno efficace. Infine, gli oggetti di lunga durata in generazione 2 dovrebbero essere raccolti con una frequenza ancora inferiore. La raccolta in generazione 2, che è l'esecuzione di un'operazione di Garbage Collection completa, è anche l'operazione più costosa.  
  
 Questa regola viene attivata quando la quantità di tempo impiegato per l'operazione di Garbage Collection è eccessivamente elevata rispetto al tempo di elaborazione totale dell'applicazione.  
  
> [!NOTE]
> Quando la percentuale di tempo impiegato per l'operazione di Garbage Collection è significativa ma non eccessiva rispetto al tempo di elaborazione totale dell'applicazione, viene attivato l'avviso [DA0023: Tempo CPU GC elevato](../profiling/da0023-high-gc-cpu-time.md) anziché la regola.  
  
## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Contrassegni](../profiling/marks-view.md) dei dati di profilatura. Individuare la colonna **Memoria CLR .NET\\% Time in GC** (% tempo in GC). Determinare se sono presenti fasi specifiche di esecuzione del programma in cui il sovraccarico di Garbage Collection della memoria gestita è maggiore rispetto ad altre fasi. Confrontare i valori di % Time in GC (% tempo in GC) con la frequenza di Garbage Collection indica nei valori **Raccolte di generazione 0**, **Raccolte di generazione 1**, **Raccolte di generazione 2**.  
  
 Il valore % Time in GC (% tempo in GC) tenta di segnalare la quantità di tempo impiegato da un'applicazione di eseguire operazioni di Garbage Collection proporzionale alla quantità totale di elaborazione. Tenere presente che esistono circostanze in cui il valore % Time in GC (% tempo in GC) può segnalare un valore molto elevato, ma non a causa di un numero eccessivo di operazioni di Garbage Collection. Per altre informazioni sul modo in cui viene calcolato il valore % Time in GC (% tempo in GC), vedere [Difference Between Perf Data Reported by Different Tools - 4](http://go.microsoft.com/fwlink/?LinkId=177863) (Differenza tra i dati delle prestazioni indicati da strumenti diversi) in **Maoni's Weblog** (Blog Web di Maoni) in MSDN. Se si verificano errori di pagina o l'applicazione viene superata da altre operazioni con priorità superiore sul computer durante l'operazione di Garbage Collection, il valore di % Time in GC (% tempo in GC) rifletterà tali ritardi aggiuntivi.
