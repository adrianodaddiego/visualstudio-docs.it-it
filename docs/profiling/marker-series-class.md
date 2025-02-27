---
title: Classe marker_series | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155d47f6764e754a1093cbcf884368c80d709a2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575917"
---
# <a name="markerseries-class"></a>Classe marker_series
Rappresenta un canale seriale di eventi generati da un singolo provider.

## <a name="syntax"></a>Sintassi

```cpp
class marker_series;
```

## <a name="members"></a>Membri

### <a name="public-constructors"></a>Costruttori pubblici

|nome|Description|
|----------|-----------------|
|[Costruttore marker_series::marker_series](../profiling/marker-series-marker-series-constructor.md)|Inizializza una nuova istanza della classe `marker_series`.|
|[Distruttore marker_series::~marker_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Elimina l'oggetto marker_series e rilascia tutte le risorse allocate.|

### <a name="public-methods"></a>Metodi pubblici

|nome|Description|
|----------|-----------------|
|[Metodo marker_series::is_enabled](../profiling/marker-series-is-enabled-method.md)|Determina se il provider è stato abilitato da una sessione.|
|[Metodo marker_series::write_alert](../profiling/marker-series-write-alert-method.md)|Scrive un avviso nel file di traccia del visualizzatore di concorrenza.|
|[Metodo marker_series::write_flag](../profiling/marker-series-write-flag-method.md)|Scrive un flag nel file di traccia del visualizzatore di concorrenza.|
|[Metodo marker_series::write_message](../profiling/marker-series-write-message-method.md)|Scrive un messaggio nel file di traccia del visualizzatore di concorrenza.|

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà
 `marker_series`

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkersobj.h*

 **Spazio dei nomi:** Concurrency::diagnostic

## <a name="see-also"></a>Vedere anche
- [Spazio dei nomi diagnostic](../profiling/diagnostic-namespace.md)