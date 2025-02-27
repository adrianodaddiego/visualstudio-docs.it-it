---
title: IDebugPortSupplier2::AddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 245c14e2aaa6867f964a2beec7bcbc232b5800be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340270"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Aggiunge una porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>Parametri
`pRequest`\
[in] Un' [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta da aggiungere.

`ppPort`\
[out] Restituisce un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) oggetto che rappresenta la porta.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo crea effettivamente la porta richiesta, nonché aggiunta all'elenco interno del fornitore della porta di porte attive. Il [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) metodo può essere chiamato prima di tutto per evitare possibili ritardi che richiedono molto tempo.

## <a name="see-also"></a>Vedere anche
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)