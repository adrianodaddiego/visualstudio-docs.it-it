---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3dc51691d4d424ee4d1c1a450f1e4e32b78e0e6e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319302"
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Specifica il tipo di errore di un punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Campi
`BPET_NONE`\
Non specifica di nessun errore punto di interruzione.

`BPET_TYPE_WARNING`\
Specifica un errore di tipo avviso punto di interruzione.

`BPET_TYPE_ERROR`\
Specifica un errore di punto di interruzione di stile di errore.

`BPET_SEV_HIGH`\
Specifica un punto di interruzione di elevata gravità errore.

`BPET_SEV_GENERAL`\
Specifica un punto di interruzione di media gravità errore.

`BPET_SEV_LOW`\
Specifica un punto di interruzione di bassa gravità errore.

`BPET_TYPE_MASK`\
Specifica un errore di punto di interruzione stile maschera.

`BPET_SEV_MASK`\
Specifica un punto di interruzione di tipo di maschera di gravità errore.

`BPET_GENERAL_WARNING`\
Specifica un errore generale-avviso-style punto di interruzione.

`BPET_GENERAL_ERROR`\
Specifica un errore generale-errore-style punto di interruzione.

`BPET_ALL`\
Specifica tutti i tipi di errore di punto di interruzione.

## <a name="remarks"></a>Note
Questi valori possono essere combinati con un bit per bit `OR` e vengono utilizzate per il `dwType` membro delle [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura. Passato come parametro per il [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) (metodo).

Un tipo di errore del punto di interruzione è costituito da un tipo e un livello di gravità. Ciò significa che un tipo di errore del punto di interruzione non è mai semplicemente un tipo (ad esempio, `BPET_TYPE_ERROR`,) o un livello di gravità (ad esempio, `BPET_SEV_GENERAL`) da solo. `BPET_GENERAL_WARNING` e `BPET_GENERAL_ERROR` fornire i valori predefiniti dei punti di interruzione di avviso ed errore generale.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
