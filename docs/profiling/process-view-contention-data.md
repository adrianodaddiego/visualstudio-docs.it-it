---
title: 'Visualizzazione Processo: dati sui conflitti | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79f9330733a0d32faeb9980813f170f52a6f7121
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965635"
---
# <a name="process-view---contention-data"></a>Visualizzazione Processo: dati sui conflitti
Nella visualizzazione Processo sono riportati i dati sui conflitti per i processi e i thread eseguiti durante l'esecuzione della profilatura.

 Quando sono disponibili i simboli, i processi vengono elencati in base al nome. Quando non sono disponibili i simboli, i processi vengono elencati in base all'indirizzo di memoria in formato esadecimale. I thread vengono elencati come elementi figlio del processo che li ha creati.

 La tabella seguente illustra i valori delle colonne nella tabella della visualizzazione Processo.

|Colonna|Description|
|------------|-----------------|
|**Ora di inizio**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura all'avvio del processo o del thread.|
|**Tempo blocco**|Tempo totale durante il quale è stata impedita l'esecuzione di funzioni del processo o del thread.|
|**% tempo blocco**|Percentuale della durata del processo o del thread in cui è stata impedita l'esecuzione delle funzioni del processo o del thread.|
|**Conflitti**|Numero di volte in cui è stata impedita l'esecuzione delle funzioni del processo o del thread.|
|**% conflitti**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresentano conflitti del processo o del thread.|
|**Ora di fine**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura alla fine del processo o del thread.|
|**ID**|Identificatore generato dal sistema per il processo o il thread.|
|**Durata**|Numero di millisecondi o di cicli del processore dall'inizio del processo o del thread alla fine del processo o del thread o alla fine della profilatura.|
|**Type**|Tipo di riga, ovvero processo o thread.<br /><br /> Solo nei rapporti della riga di comando di **VSReport**. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).|
|**Name**|Nome del processo o del thread.|
|**ID univoco**|Identificatore generato dal profiler univoco per il processo o il thread.|

## <a name="see-also"></a>Vedere anche
- [Procedura: Personalizzare le colonne delle visualizzazioni dei report](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Processo](../profiling/process-view.md)