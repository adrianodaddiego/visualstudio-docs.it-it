---
title: IDebugClassField::GetDefaultIndexer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95387f65382c970ec2e9847e95ff49e139cf69b8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350750"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Ottiene il nome dell'indicizzatore predefinita.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>Parametri
`pbstrIndexer` [out] Restituisce una stringa contenente il nome dell'indicizzatore predefinita.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non esiste alcun indicizzatore predefinito. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 L'indicizzatore predefinito di una classe è la proprietà che è contrassegnata come il `Default` proprietà per gli accessi alla matrice. Questo è specifico di [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]. Di seguito è riportato un esempio di un indicizzatore predefinito dichiarato in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] e modalità di utilizzo.

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>Vedere anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)