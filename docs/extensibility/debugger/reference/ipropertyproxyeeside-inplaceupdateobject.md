---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ce2826aa0bd75638d6f5ee8086cbcce96517ce7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329415"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aggiorna i dati dell'oggetto con l'oggetto dati specificato e restituisce un nuovo oggetto dati che rappresenta i dati dell'oggetto nuovo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametri
`dataIn`\
[in] Un' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto contenente i nuovi dati.

`dataOut`\
[out] Restituisce un nuovo `IEEDataStorage` oggetto contenente i dati sostituiti.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo aggiorna effettivamente i dati dell'oggetto. I dati nell'oggetto restituito [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto non deve essere quello utilizzato per i dati in ingresso `IEEDataStorage` oggetto, ma l'oggetto restituito deve riflettere il valore della proprietà corrente.

 L'oggetto dati in entrata non è in genere implementato dal motore di esecuzione. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato dal motore di esecuzione, che consente di implementare EE il `IEEDataStorage` interfaccia su qualsiasi classe desiderata.

 Il [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) metodo crea un oggetto dati in base all'oggetto dati in ingresso, ma influisce sui dati originali della proprietà.

## <a name="see-also"></a>Vedere anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)