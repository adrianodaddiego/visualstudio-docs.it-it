---
title: "Visualizzazione Puntatore all'istruzione: dati sui conflitti | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d41f48594e50e9d5ae0c6f67aabab673a9f112a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62995399"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Visualizzazione dei puntatori all'istruzione: dati sui conflitti
Nella visualizzazione Puntatore all'istruzione dei dati sui conflitti sono elencati i dati per le istruzioni dell'assembly di cui è stata impedita l'esecuzione durante la profilatura.

 La tabella seguente illustra i valori delle colonne nella visualizzazione Puntatore all'istruzione.

|Colonna|Description|
|------------|-----------------|
|**Tempo blocco esclusivo**|Tempo di blocco in questa funzione.|
|**% tempo blocco esclusivo**|Percentuale di tempo di blocco durante l'esecuzione dell'istruzione.|
|**Conflitti esclusivi**|Numero di conflitti che si sono verificati durante l'esecuzione dell'istruzione.|
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che si sono verificati durante l'esecuzione dell'istruzione.|
|**Indirizzo funzione**|Indirizzo di memoria iniziale della funzione nel file binario caricato.|
|**Nome funzione**|Nome della funzione contenente l'istruzione.|
|**Indirizzo istruzione**|Indirizzo di memoria dell'istruzione nel file binario caricato.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Nome modulo**|Nome del modulo contenente l'istruzione.|
|**Percorso modulo**|Percorso del modulo contenente l'istruzione.|
|**ID processo**|ID di processo (PID) del processo profilato.|
|**Nome processo**|Nome del processo.|
|**Inizio carattere di origine**|Offset del carattere nella riga del file di origine in corrispondenza del quale inizia questa istruzione.|
|**Fine carattere di origine**|Offset del carattere nella riga del file di origine in corrispondenza del quale termina questa istruzione.|
|**File di origine**|File di origine che contiene l'istruzione.|
|**Inizio riga di origine**|Numero di riga del file di origine dove inizia questa istruzione.|
|**Fine riga di origine**|Numero di riga del file di origine dove termina questa istruzione.|

## <a name="see-also"></a>Vedere anche
- [Procedura: Personalizzare le colonne delle visualizzazioni dei report](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Puntatore all'istruzione](../profiling/instruction-pointers-ips-view.md)
- [Visualizzazione dei puntatori all'istruzione: campionamento](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Puntatore all'istruzione](../profiling/instruction-pointers-ips-view-sampling-data.md)