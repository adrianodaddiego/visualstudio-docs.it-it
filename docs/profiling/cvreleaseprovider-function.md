---
title: Funzione CvReleaseProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0008b7476290558c098b2241fde5c9b209933a0a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974046"
---
# <a name="cvreleaseprovider-function"></a>Funzione CvReleaseProvider
Rilascia un provider di marcatori. Il rilascio del provider di marcatori non influisce sulle serie di marcatori del provider create in precedenza. Le serie di marcatori devono essere rilasciate separatamente dalla chiamata CvReleaseMarkerSeries. Il mancato rilascio del provider di marcatori causa una perdita di memoria.

## <a name="syntax"></a>Sintassi

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parametri
 `pProvider` Contesto del provider. Non può essere NULL.

## <a name="return-value"></a>Valore restituito
 S_OK quando il provider è stato rilasciato correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkers.h*

## <a name="see-also"></a>Vedere anche
- [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)