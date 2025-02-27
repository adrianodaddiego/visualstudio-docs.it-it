---
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c667ffa597481121de0467c9ab4b07e4bf4d607
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333380"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera l'intervallo per la posizione corrente del documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Parametri
`pdwBegOffset`\
[in, out] Offset per la posizione iniziale dell'intervallo. Impostare questo parametro su un valore null se questa informazione non è necessaria.

`pdwEndOffset`\
[in, out] Offset per la posizione finale dell'intervallo. Impostare questo parametro su un valore null se questa informazione non è necessaria.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'intervallo specificato in una posizione di documento per un punto di interruzione di posizione viene utilizzato dal motore di debug (DE) per la ricerca con un'istruzione che effettivamente contribuisce codice. Si consideri il codice di esempio seguente:

```
Line 5: // comment
Line 6: x = 1;
```

 Riga 5 non contribuisce alcun codice per il programma sottoposto a debug. Se il debugger che consente di impostare il punto di interruzione alla riga 5 desidera DE per eseguire la ricerca di un determinato periodo per la prima riga che ha reso disponibile codice, il debugger di specificare un intervallo che include le righe aggiuntive candidato in cui un punto di interruzione potrebbe essere correttamente posizionato. La Germania verrebbe quindi eseguita una ricerca in avanti tramite queste righe fino a quando non trovata una riga che può accettare un punto di interruzione.

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)