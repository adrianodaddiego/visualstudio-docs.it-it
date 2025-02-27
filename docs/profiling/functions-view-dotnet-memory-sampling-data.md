---
title: 'Visualizzazione Funzioni: dati di campionamento di memoria .NET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b0e8c14779f9f7b3f14fab2dfc1022db0319aeb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974059"
---
# <a name="functions-view---net-memory-sampling-data"></a>Visualizzazione Funzioni: dati di campionamento di memoria .NET
La visualizzazione Funzioni dei dati di profilatura sull'allocazione di memoria .NET raccolti tramite il metodo di campionamento elenca le funzioni che hanno allocato memoria durante l'esecuzione della profilatura e indica le dimensione e il numero delle allocazioni.

|Colonna|Description|
|------------|-----------------|
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Nome processo**|Nome del processo.|
|**Nome modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|
|**File di origine**|File di origine che contiene la definizione per questa funzione.|
|**Nome funzione**|Nome completo della funzione.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Indirizzo funzione**|Indirizzo della funzione.|
|**Allocazioni inclusive**|Numero totale di oggetti allocati in questa funzione e funzioni figlio corrispondenti.|
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|
|**Allocazioni esclusive**|Numero di oggetti creati durante l'esecuzione diretta della funzione nella parte superiore dello stack di chiamate. Questo numero non include gli oggetti creati nelle funzioni figlio.|
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive di questa funzione.|
|**Byte inclusivi**|Numero di byte di memoria allocati da questa funzione e dalle funzioni figlio corrispondenti.|
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano byte inclusivi di questa funzione.|
|**Byte esclusivi**|Numero di byte di memoria allocati da questa funzione ma non dalle funzioni figlio corrispondenti.|
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano byte esclusivi di questa funzione.|

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Funzioni: strumentazione](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-sampling-data.md)
- [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)