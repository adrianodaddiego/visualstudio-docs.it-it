---
title: Analisi delle violazioni delle regole di soglia nei test di carico
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a7cd36fcb144eaa098acc30a7da550b1288684a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823089"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analisi delle violazioni delle regole di soglia nei test di carico tramite l'Analizzatore test di carico

Le regole di soglia sono associate a specifici contatori delle prestazioni e le violazioni indicano che un contatore ha superato o non ha raggiunto un valore impostato. Quando si esegue un test di carico, è possibile analizzare le violazioni che si verificano per le regole di soglia configurate in precedenza.

Se si verificano violazioni, sulla barra di stato dell'**Analizzatore test di carico** viene visualizzato il collegamento ipertestuale **violazioni di soglia** e ne viene specificato il numero. Scegliere il collegamento ipertestuale per visualizzare la tabella delle violazioni di soglia. È anche possibile visualizzare tali violazioni di soglia nella finestra **Contatori** e sul grafico.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Visualizzare le violazioni di soglia nella tabella

 Nella tabella vengono visualizzate le prime 1.000 violazioni di soglia. La tabella seguente contiene queste colonne:

|Colonna|Description|Visibile per impostazione predefinita|
|-|-|-|
|Ora|L'ora durante il test di carico in cui si è verificata la violazione.|Sì|
|Computer|Il nome del computer sottoposto a test in cui si è verificata la violazione. **Nota:**  Questo nome è importante quando i test di carico vengono eseguiti in rig.|Sì|
|Category|La categoria del contatore delle prestazioni in cui si è verificata la violazione.|Sì|
|Counter|Il nome del contatore delle prestazioni in cui si è verificata la violazione.|Sì|
|Istanza|L'istanza del contatore delle prestazioni in cui si è verificata la violazione.|Sì|
|Messaggio|Messaggio in cui viene descritta la violazione di soglia, Ad esempio, **Il valore 5 supera il valore soglia critico di 0**.|Sì|

> [!NOTE]
> È possibile ordinare la tabella scegliendo le intestazioni delle colonne.

 Per altre informazioni, vedere [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Visualizzare le violazioni di soglia nel pannello dei contatori

 È possibile visualizzare le violazioni di soglia nel pannello dei **contatori**, nell'albero che elenca i contatori delle prestazioni per il test di carico. Tali violazioni di soglia vengono comunicate tramite icone nel pannello dei **contatori**. e possono essere una delle seguenti:

 e possono essere una delle seguenti:

 ![Nessuna violazione di soglia](../test/media/icon_ltest_1.gif) Nessuna violazione di soglia.

 ![Violazione di soglia critica nell'ultimo intervallo](../test/media/icon_ltest_2.gif) Si è verificata una violazione di soglia critica nell'ultimo intervallo.

 ![Violazione di soglia critica in un intervallo precedente](../test/media/icon_ltest_3.gif) Si è verificata una violazione di soglia critica in un intervallo precedente.

 ![Violazione di soglia con avviso nell'ultimo intervallo](../test/media/icon_ltest_4.gif) Si è verificata una violazione di soglia di avvertenza nell'ultimo intervallo.

 ![Violazione di soglia con avviso in un intervallo precedente](../test/media/icon_ltest_5.gif) Si è verificata una violazione di soglia di avvertenza in un intervallo precedente.

 Se lo si desidera, è possibile visualizzare le violazioni di soglia anche nel grafico. L'icona di soglia viene visualizzata nel grafico accanto al punto dati in cui si è verificata la violazione di soglia.

 Nell'albero dei contatori l'icona relativa a una violazione di soglia viene propagata dal nodo del contatore specifico fino al nodo radice. In questo modo si segnala all'utente una violazione in un contatore che potrebbe non essere visibile nella struttura ad albero, in quanto non è stata espansa.

## <a name="view-threshold-violations-on-the-graph"></a>Visualizzare le violazioni di soglia sul grafico

 È possibile visualizzare le violazioni di soglia sul grafico. In modo analogo a quanto avviene nel pannello dei **contatori**, le icone comunicano le violazioni di soglia sul grafico. Vengono visualizzate accanto al punto dati in cui si è verificata la violazione di soglia. Se si verifica una violazione di soglia in un contatore non presente sul grafico, è possibile aggiungerlo trascinandolo dal pannello dei **contatori**.

 Per altre informazioni, vedere [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Vedere anche

- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)