---
title: 'Visualizzazione Riepilogo: dati di strumentazione | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91d53eef12c1c2dc59d8c442a040f721af75e7b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557050"
---
# <a name="summary-view---instrumentation-data"></a>Visualizzazione Riepilogo: dati di strumentazione
La visualizzazione Riepilogo mostra informazioni sulle funzioni che influiscono maggiormente sulle prestazioni in un'esecuzione della profilatura. Per altre informazioni, inclusa una descrizione dei collegamenti di notifica e degli elenchi di report, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Grafico della sequenza temporale
 Il grafico della sequenza temporale nella visualizzazione Riepilogo mostra l'utilizzo del processore (CPU) per l'applicazione profilata nel periodo di profilatura. È possibile usare il grafico della sequenza temporale per filtrare la visualizzazione in base a un intervallo di tempo selezionato. Per altre informazioni, vedere [Procedura: Filtrare le visualizzazioni report dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Percorso critico
 In **Percorso critico** viene visualizzato il percorso di esecuzione che ha richiesto la quantità di tempo maggiore. È possibile fare clic su una funzione per attivare la visualizzazione Dettagli funzione per la funzione. Per visualizzare altre visualizzazioni per la funzione, fare clic con il pulsante destro del mouse sulla funzione e scegliere una visualizzazione nell'elenco.

 Il **Percorso critico** include i dati seguenti per ogni funzione:

|Colonna|Description|
|------------|-----------------|
|**Name**|Nome della funzione.|
|**% tempo inclusivo trascorso**|Percentuale del tempo totale nei dati di profilatura dedicato dalla funzione all'esecuzione del codice nel corpo della funzione e nelle funzioni chiamate dalla funzione stessa.|
|**% tempo esclusivo trascorso**|Percentuale del tempo totale nei dati di profilatura dedicato dalla funzione all'esecuzione del codice nel corpo della funzione. Il tempo dedicato a funzioni chiamate dalla funzione non è incluso.|

## <a name="functions-with-most-individual-work"></a>Funzioni con più lavoro individuale
 Elenco delle funzioni che hanno richiesto la quantità di tempo maggiore per l'esecuzione del codice nel corpo della funzione e non nelle funzioni da essa chiamate.

 L'opzione **Funzioni con più lavoro individuale** include i dati seguenti per ogni funzione:

|Colonna|Description|
|------------|-----------------|
|**Name**|Nome della funzione.|
|**% tempo esclusivo**|Percentuale del tempo totale nei dati di profilatura dedicato dalla funzione all'esecuzione del codice nel corpo della funzione. Il tempo dedicato a funzioni chiamate dalla funzione non è incluso.|

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Riepilogo: dati di campionamento](../profiling/summary-view-sampling-data.md)
- [Visualizzazione Riepilogo: dati di memoria .NET](../profiling/summary-view-dotnet-memory-data.md)