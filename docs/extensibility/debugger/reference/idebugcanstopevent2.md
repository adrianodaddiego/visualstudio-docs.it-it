---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab364b426005c838072fabc1a3c7ed2f7d64ac6a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337337"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Questa interfaccia viene utilizzata per la gestione del debug sessione (SDM) viene richiesto se arrestare nella posizione corrente del codice.

## <a name="syntax"></a>Sintassi

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per supportare l'esecuzione di istruzioni nel codice sorgente. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia (Usa il modello SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso il `IDebugEvent2` interface).

 L'implementazione di questa interfaccia deve comunicare chiamata di SDM [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) al motore di debug. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al thread di gestione dei messaggi del motore di debug o l'oggetto che implementa questa interfaccia può contenere un riferimento al motore di debug e richiamare il motore di debug con il flag passato `IDebugCanStopEvent2::CanStop`.

## <a name="notes-for-callers"></a>Note per i chiamanti
 La Germania può inviare questo metodo ogni volta che la Germania viene richiesto di continuare l'esecuzione e il DE è avanzamento tramite codice. Questo evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback fornita dal modello SDM quando associato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugCanStopEvent2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ottiene il motivo per questo evento.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Specifica se il programma sottoposto a debug deve essere arrestato in corrispondenza della posizione di questo evento (e invia un evento che descrive il motivo dell'arresto) o semplicemente continuare l'esecuzione.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ottiene il contesto del documento che descrive la posizione di questo evento.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ottiene il contesto di codice che descrive la posizione di questo evento.|

## <a name="remarks"></a>Note
 La Germania invia questa interfaccia se i passaggi di utente in una funzione e il DE rileva che non esiste alcuna informazione di debug o le informazioni di debug esistono ma la Germania non sa se è possibile visualizzare il codice sorgente per quel percorso.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)