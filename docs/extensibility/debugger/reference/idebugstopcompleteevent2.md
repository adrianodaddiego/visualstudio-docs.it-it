---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d080b3073ffc13b90870b40a16a353634f4aa0cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352014"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Il motore di debug (DE) può inviare questo evento facoltativo da gestore di sessione di debug (SDM) quando un programma è stato arrestato.

## <a name="syntax"></a>Sintassi

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori

Questa interfaccia è stato introdotto con Visual Studio 2005. Arresto asincrono non supporta le versioni precedenti.

- [Arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato da SDM negli scenari a più processi o multi-programma. Quando un programma invia un evento di arresto per il modello SDM, il modello SDM richiede altri programmi per arrestare, troppo.

Arresto viene utilizzato per indicare in modo asincrono il modello SDM che un programma è stato arrestato. Per informare il modello SDM è utile per un motore di debug dell'interprete, in cui a volte codice non è in esecuzione all'interno in fase di debug del programma, pertanto [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) non può essere eseguita in modo sincrono. Se un motore di debug vuole adottare questa notifica asincrona, deve restituire `S_ASYNC_STOP` dal [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll