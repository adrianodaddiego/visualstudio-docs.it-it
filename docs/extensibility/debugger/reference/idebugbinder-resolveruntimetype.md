---
title: IDebugBinder::ResolveRuntimeType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2954b5f2a1ac4dd14485a1b924423ba53fddcb7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315171"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Questo metodo determina il tipo di fase di esecuzione di un oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>Parametri
`pObject`\
[in] Il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) da risolvere.

`ppResolved`\
[out] Restituisce il tipo dell'oggetto come un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il tipo di fase di esecuzione di un oggetto non è sempre noto in fase di compilazione. Ad esempio, utilizza il polimorfismo, un argomento può essere passato a una funzione come classe di base, ad esempio una classe di pulsanti. L'argomento effettivo potrebbe essere una classe derivata, ad esempio una classe di pulsante di opzione.

## <a name="see-also"></a>Vedere anche
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)