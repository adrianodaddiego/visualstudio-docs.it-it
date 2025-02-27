---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03e82a8c17b33aa085b4ed64b9ba609bee183e1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829732"
---
# <a name="basictype"></a>BasicType
Specifica tipo di base del simbolo.

## <a name="syntax"></a>Sintassi

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Elementi
btNoType che viene specificato alcun tipo di base.

è di tipo base btVoid un `void`.

btChar tipo di base è un `char` (C /C++ tipo).

tipo di base btWChar è un carattere wide (Unicode) (`WCHAR`).

è di tipo base btInt `signed int` (C /C++ tipo).

è di tipo base btUInt `unsigned int` (C /C++ tipo).

btFloat tipo di base è un numero a virgola mobile (`FLOAT`).

btBCD tipo di base è un valore decimale a livello di codice binario (`BCD`).

tipo di base btBool è un valore booleano (`BOOL`).

btLong tipo di base è un `long int` (C /C++ tipo).

tipo base btULong è un' `unsigned long int` (C /C++ tipo).

tipo di base btCurrency è currency.

tipo di base btDate è data/ora (`DATE`).

btVariant tipo di base è una struttura di tipo di variabile (`VARIANT`).

tipo di base btComplex è un numero complesso.

tipo di base btBit è un po'.

btBSTR tipo di base è una stringa di base o binary (`BSTR`).

è di tipo base btHresult un `HRESULT`.

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono restituiti per il [Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
