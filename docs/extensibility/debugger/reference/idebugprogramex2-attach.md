---
title: IDebugProgramEx2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db27f29b37480081d29e452d74a6da0c5cea59a6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325177"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Connettere una sessione a un programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Parametri
`pCallback`\
[in] Un' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto che rappresenta la funzione di callback che il motore di debug collegati invia eventi.

`dwReason`\
[in] Un valore compreso il [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumerazione che descrive il motivo per l'operazione di collegamento.

`pSession`\
[in] Un valore che identifica in modo univoco la sessione che si sta connettendo al programma.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Questo metodo deve restituire `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` se il programma è già collegato.

## <a name="remarks"></a>Note
 La porta che contiene il programma può usare il valore in `pSession` per determinare quale sessione sta tentando di collegare al programma. Ad esempio, se una porta consente di sessione di debug solo una per connettersi a un processo alla volta, la porta possibile determinare se la stessa sessione è già collegata ad altri programmi nel processo.

> [!NOTE]
> L'interfaccia passato `pSession` deve essere considerata solo come un cookie, un valore che identifica in modo univoco la gestione del debug sessione la connessione a questo programma; nessuno dei metodi nell'interfaccia specificata sono funzionali.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)