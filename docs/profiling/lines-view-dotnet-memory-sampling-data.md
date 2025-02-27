---
title: 'Visualizzazione Righe: dati di campionamento di memoria .NET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c654bbcc9db696d78e651414bfa89d6ad1e2f3e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000065"
---
# <a name="lines-view---net-memory-sampling-data"></a>Visualizzazione Righe: dati di campionamento di memoria .NET
La visualizzazione Righe dei dati di profilatura sull'allocazione di memoria .NET che usa il metodo di campionamento elenca le istruzioni per l'allocazione della memoria durante l'esecuzione della profilatura. Nelle colonne vengono inoltre inclusi la dimensione e il numero delle allocazioni.

 In un file di origine un'istruzione può occupare più di una riga in un file di origine e una singola riga può includere più di un'istruzione.

 Un'istruzione viene identificata in base agli elementi seguenti:

- File di origine che contiene l'istruzione della funzione.

- Funzione che contiene l'istruzione.

- Riga di origine in cui inizia l'istruzione.

- Carattere nella riga di origine in cui inizia l'istruzione.

- Riga di origine in cui termina l'istruzione.

- Carattere nella riga di origine in cui termina l'istruzione.

  Nella colonna Nome riga è disponibile una concatenazione ordinabile dei dati dell'identificatore.

  Per definizione, un'istruzione non chiama altre funzioni. Vengono quindi elencati solo valori esclusivi.

|Colonna|Description|
|------------|-----------------|
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Nome processo**|Nome del processo.|
|**Nome modulo**|Nome del modulo che contiene l'istruzione.|
|**Percorso modulo**|Percorso del modulo che contiene l'istruzione.|
|**File di origine**|File di origine che contiene l'istruzione.|
|**Nome funzione**|Nome della funzione che contiene l'istruzione.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Indirizzo funzione**|Indirizzo iniziale della funzione.|
|**Inizio riga di origine**|Numero di riga iniziale nel file di origine in corrispondenza del quale si è verificata l'allocazione.|
|**Fine riga di origine**|Numero di riga finale nel file di origine in corrispondenza del quale si è verificata l'allocazione.|
|**Inizio carattere di origine**|Offset del carattere iniziale nella riga del file di origine in corrispondenza del quale si è verificata l'allocazione.|
|**Fine carattere di origine**|Offset del carattere finale nella riga del file di origine in corrispondenza del quale si è verificata l'allocazione.|
|**Nome riga**|Identificatore generato dal profiler della riga con la sintassi seguente:`Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number Start,Character Start`**]**|
|**Allocazioni esclusive**|Numero totale di oggetti creati in questa riga.|
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che sono stati allocati in questa riga.|
|**Byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che sono stati allocati in questa riga.|
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che sono stati allocati in questa riga.|

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Righe](../profiling/lines-view-sampling-data.md)