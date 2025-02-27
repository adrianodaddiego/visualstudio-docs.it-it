---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5fea99994b891250dad85cfc43320848df98f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555104"
---
# <a name="cvcalle"></a>CV_call_e
Specifica la convenzione di chiamata per una funzione.

> [!NOTE]
> Solo i valori di enumerazione più comuni sono documentati qui. L'enumerazione completo è disponibile nel file di intestazione cvconst.h.

## <a name="syntax"></a>Sintassi

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>Elementi
CV_CALL_NEAR_C specifica una convenzione di chiamata di funzioni con un push quasi di destra a sinistra. La funzione chiamante Cancella lo stack.

Una convenzione di chiamata di funzione con un breve da sinistra a destra push con registra CV_CALL_NEAR_FAST specifica. La funzione chiamata viene utilizzata la somma dei byte di parametro per cancellare lo stack.

CV_CALL_NEAR_STD specifica una convenzione di chiamata di funzione tramite una chiamata standard quasi (right-to-left push).

Una convenzione di chiamata di funzioni usando un sistema quasi CV_CALL_NEAR_SYS specifica chiamata.

CV_CALL_THISCALL specifica utilizzando una convenzione di chiamata di funzioni `this` chiamare (`this` puntatore passati nel registro).

Specifica CV_CALL_CLRCALL una convenzione di chiamata di funzioni usata da Common Language Runtime (CLR) (noto anche come un codice gestito convenzione di chiamata).

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono restituiti da una chiamata per il [Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
