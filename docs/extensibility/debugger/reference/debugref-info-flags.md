---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1adab87ed09ca2ff16d837da084d8cc0b76956fe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318361"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Specifica le informazioni da recuperare un oggetto di riferimento di debug.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Campi
`DEBUGREF_INFO_NAME`\
Initialize/usare la `bstrName` campo nella struttura.

`DEBUGREF_INFO_TYPE`\
Initialize/usare la `bstrType` campo nella struttura.

`DEBUGREF_INFO_VALUE`\
Initialize/usare la `bstrValue` campo nella struttura.

`DEBUGREF_INFO_ATTRIB`\
Initialize/usare la `dwAttrib` campo nella struttura.

`DEBUGREF_INFO_REFTYPE`\
Initialize/usare la `dwRefType` campo nella struttura.

`DEBUGREF_INFO_REF`\
Initialize/usare la `pReference` campo nella struttura.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Il campo del valore deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.

`DEBUGREF_INFO_NONE`\
Indica che non sono impostati flag.

`DEBUGREF_INFO_ALL`\
Indica una maschera dei flag.

## <a name="remarks"></a>Note
Questi flag vengono passati per il [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) e [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metodi per indicare quali campi della [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura devono essere inizializzate.

Utilizzato per il `dwFields` membro del `DEBUG_REFERENCE_INFO` struttura per indicare quali campi vengono usati e valido quando la struttura viene restituita.

Questi valori possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
