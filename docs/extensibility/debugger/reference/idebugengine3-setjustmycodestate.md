---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f53b0eb95a2a91f34917b05cadffda2f4aa9a8b1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322320"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Le informazioni di stato JustMyCode, questo metodo indica al motore di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parametri
`fUpdate`\
[in] Diverso da zero (`TRUE`) per aggiornare le informazioni correnti, zero (`FALSE`) per reimpostare tutte le informazioni (ignorando qualsiasi tipo impostato in precedenza).

`dwModules`\
[in] Numero di strutture di informazioni in `rgJMCSpec.`

`rgJMCSpec`\
[in] Matrice di [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) strutture da usare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Note
 JustMyCode è il concetto di debug solo del codice a cui appartiene un utente e ignorare tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per tale codice di sistema.

## <a name="see-also"></a>Vedere anche
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)