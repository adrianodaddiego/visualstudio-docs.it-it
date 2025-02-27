---
title: 'Visualizzazione Funzioni: dati sui conflitti | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dcea1097b33c612094c4a7eb35b240c28f8bde0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969745"
---
# <a name="functions-view---contention-data"></a>Visualizzazione Funzioni: dati sui conflitti
La visualizzazione report Funzioni dei dati sui conflitti elenca le funzioni nell'esecuzione della profilatura la cui esecuzione è stata bloccata durante l'esecuzione della profilatura stessa.

 La tabella seguente descrive i valori presenti nella visualizzazione Funzioni di un file di dati di profilatura raccolti tramite il metodo di concorrenza.

|Colonna|Description|
|------------|-----------------|
|**Tempo blocco esclusivo**|La quantità di tempo durante la quale è stata impedita l'esecuzione di codice nel corpo della funzione. È escluso il tempo di blocco nelle funzioni chiamate dalla funzione.|
|**% tempo blocco esclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco esclusivo per questa funzione.|
|**Conflitti esclusivi**|Il numero di volte che è stata impedita l'esecuzione di codice nel corpo della funzione. Non sono inclusi i conflitti in funzioni chiamate dalla funzione.|
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresentano conflitti esclusivi di questa funzione.|
|**Indirizzo funzione**|Indirizzo della funzione.|
|**Nome funzione**|Nome completo della funzione.|
|**Tempo blocco inclusivo**|Ora in cui l'esecuzione di questa funzione o di una funzione chiamata da questa è stata bloccata.|
|**% tempo blocco inclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco inclusivo per questa funzione o per questo modulo.|
|**Conflitti inclusivi**|Numero di volte in cui l'esecuzione di questa funzione o di una funzione chiamata da questa è stata bloccata.|
|**% conflitti inclusivi**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresentano conflitti inclusivi di questa funzione o di questo modulo.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Nome modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|
|**ID processo**|ID del processo (PID) del processo in cui era in esecuzione la funzione.|
|**Nome processo**|Nome del processo.|
|**File di origine**|File di origine che contiene la definizione per questa funzione.|

## <a name="see-also"></a>Vedere anche
- [Procedura: Personalizzare le colonne delle visualizzazioni dei report](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Funzioni](../profiling/functions-view.md)
- [Visualizzazione Funzioni: strumentazione](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Visualizzazione Funzioni: campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-sampling-data.md)