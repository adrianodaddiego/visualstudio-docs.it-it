---
title: IDebugEvent2::GetAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f85cccb01a31232cccc39e44fae7accbfa4f954
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327593"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Ottiene gli attributi per questo evento di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>Parametri
`pdwAttrib`\
[out] Una combinazione di flag dal [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia è comune a tutti gli eventi. Questo metodo viene descritto il tipo di evento. ad esempio, è l'evento sincrono o asincrono e si tratta di un evento di arresto.

## <a name="see-also"></a>Vedere anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)