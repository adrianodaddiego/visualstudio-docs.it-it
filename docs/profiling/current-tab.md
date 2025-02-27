---
title: Scheda corrente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f48ba44d41286f1cf5eda6ececb68d21d39abd14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552788"
---
# <a name="current-tab"></a>Scheda Corrente
Facendo clic sulla scheda **Corrente**, è possibile visualizzare uno stack di chiamate (se disponibile) che è più vicino al punto di selezione corrente nella sequenza temporale se è selezionato un segmento di thread della CPU.  In questo caso, il punto di selezione è rappresentato da una freccia nera (o punto di inserimento) sopra la sequenza temporale. Quando viene selezionato un segmento di blocco, il punto di inserimento non viene visualizzato perché non è in esecuzione. Tuttavia, il segmento è ancora evidenziato e viene visualizzato uno stack di chiamate.

 La scheda **Corrente** visualizza anche informazioni sui segmenti di attività di DirectX, marcatori e accesso I/O.  Per i segmenti di attività di DirectX, vengono visualizzate le informazioni sul modo in cui vengono elaborati i pacchetti DMA dalla coda di hardware.  Per i marcatori, vengono visualizzate informazioni sul tipo di marcatore e descrizione.  Per l'accesso I/O, vengono visualizzate informazioni sui file e sul numero di byte letti o scritti.

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)