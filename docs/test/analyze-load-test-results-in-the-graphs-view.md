---
title: Analisi dei risultati dei test di carico nella visualizzazione Grafici dell'Analizzatore test di carico
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c48fe67c8d52f962589c9f8628ff49f12f7770c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823002"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analizzare i risultati dei test di carico nella visualizzazione Grafici dell'Analizzatore test di carico

I risultati di un test di carico vengono visualizzati come dati in diversi pannelli.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Per visualizzare i risultati del test in forma grafica, fare clic su **Grafici** sulla barra degli strumenti del **test di carico**. Ogni singolo grafico viene visualizzato in un pannello con il nome del grafico riportato all'inizio di un elenco a discesa. Per visualizzare un grafico diverso nel pannello, scegliere dall'elenco il nome di un altro grafico.

È possibile visualizzare fino a quattro pannelli di grafici alla volta. È possibile passare da un layout del pannello all'altro mediante il pulsante della barra degli strumenti per il **layout dei pannelli**.

Vengono forniti molti grafici incorporati. È possibile usare i grafici incorporati così come sono o è possibile personalizzarli. Inoltre, è possibile creare grafici personalizzati. Per altre informazioni, vedere [Procedura: Aggiungere ed eliminare contatori nei grafici](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) e [Procedura: Creare grafici personalizzati](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Grafici incorporati

Nella tabella seguente sono riportati i grafici incorporati disponibili per l'analisi dei risultati dei test di carico.

|Nome grafico|Description|
|-|-|
|Indicatori chiave|Contatori che descrivono gli aspetti di base delle prestazioni del test, ad esempio carico utente, velocità effettiva e tempo di risposta.|
|Tempo di risposta per test|Dati relativi alla quantità di tempo richiesta per l'esecuzione dei test.|
|Tempo di risposta per pagina|Tempo di risposta medio per le pagine Web a cui si accede durante il test di carico.|
|Sistema sotto test|Informazioni sui computer in cui viene eseguita l'applicazione da sottoporre a test, ovvero i dati relativi a utilizzo della memoria, processore, disco fisico e processi.<br /><br /> Per impostazione predefinita, vengono raccolti solo i contatori per i MB disponibili e il tempo processore.|
|Controller e agente|Informazioni sui computer in cui vengono eseguiti i test di carico, ovvero i dati relativi a utilizzo della memoria, processore, disco fisico e processi.<br /><br /> Per impostazione predefinita, vengono raccolti solo i contatori per i MB disponibili e il tempo processore.|
|Tempo di risposta per transazione|Tempo di risposta medio per le transazioni che si verificano durante il test di carico.|

 Sul grafico è possibile visualizzare diversi contatori sia durante il runtime che dopo l'esecuzione di un test.

> [!NOTE]
> Solo i contatori di prestazioni relativi ai tempi di risposta possono essere aggiunti in un grafico dei tempi di risposta generato automaticamente.

 Le informazioni del contatore vengono visualizzate sia nel grafico che nella legenda sotto il grafico. Inoltre, è possibile ingrandire un'area del grafico. Per altre informazioni, vedere [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Contatori visualizzati nei grafici

 Nei grafici vengono visualizzati *contatori*. che fanno riferimento ai dati raccolti durante un test di carico, ad esempio test al secondo o tempo medio test. Per altre informazioni sui contatori, vedere [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

 La legenda per i contatori visualizzati nei grafici mostra diverse colonne di dati utili sull'esecuzione del test di carico. Per disattivare la visualizzazione dei dati nel grafico, deselezionare la casella di controllo nella riga della legenda.

 Nella legenda sono presenti le seguenti colonne:

|Counter|Nome del contatore|
|-|-|
|Istanza|Il nome dell'istanza del contatore.|
|Category|Il nome della categoria del contatore.|
|Computer|Il nome del computer in cui viene raccolto il contatore.|
|Colore|Il colore della riga nel grafico.|
|Intervallo|Indica il numero rappresentato da 100 nel grafico per quel contatore. Ad esempio, per un intervallo il cui valore superiore è 10.000, l'etichetta 100 all'inizio del grafico rappresenta 10.000.|
|Min|Indica il valore minimo in millisecondi per il contatore.|
|Max|Indica il valore massimo in millisecondi per il contatore.|
|Avg|Indica il valore medio in millisecondi per il contatore.|
|Ultimo|Mostra il valore in millisecondi del contatore durante l'intervallo di campionamento più recente.|

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-|-|
|**Personalizzare i grafici tramite la legenda:** la legenda della visualizzazione Grafici visualizza le informazioni per ogni contatore delle prestazioni associato a un grafico. È possibile usare la legenda per rimuovere ed evidenziare contatori delle prestazioni nel grafico e personalizzare le opzioni relative ai tracciati.|-   [Uso della legenda della visualizzazione Grafici per analizzare i test di carico](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Visualizzare i contatori nei grafici:** è possibile aggiungere diversi tipi di dati in un grafico dei risultati dei test di carico inserendo contatori nel grafico.|-   [Procedura: Aggiungere ed eliminare contatori nei grafici](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Fare zoom avanti nei grafici:** Al termine di un test di carico, è possibile utilizzare le barre dello zoom per eseguire lo zoom avanti e scorrere un'area del grafico. Lo zoom avanti consente di analizzare i dettagli anche minuti dei dati generati durante l'esecuzione di un test di carico.|-   [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Affiancare i grafici:** È possibile disporre i grafici dei risultati del test di carico adottando diversi modelli. È possibile affiancare fino a quattro grafici.||
|**Creare grafici personalizzati:** È possibile progettare grafici che visualizzano specifiche informazioni sui risultati dei test di carico. Per progettare un grafico personalizzato, specificare i contatori del test di carico che verranno visualizzati sul grafico.|-   [Procedura: Creare grafici personalizzati](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Esportare i dati dei contatori delle prestazioni nel grafico:** È possibile esportare i dati del grafico in Microsoft Excel tramite il pulsante **Esporta dati del grafico in Excel** disponibile sulla barra degli strumenti **Analizzatore test di carico** nella visualizzazione **Grafici**.||

## <a name="related-tasks"></a>Attività correlate

 [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

 [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md)

 [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Vedere anche

- [Procedura: Aggiungere ed eliminare contatori nei grafici](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Procedura: Creare grafici personalizzati](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)