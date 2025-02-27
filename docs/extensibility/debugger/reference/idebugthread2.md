---
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df63bc6484905249adc1756ce701b3ee91f45015
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319972"
---
# <a name="idebugthread2"></a>IDebugThread2
Questa interfaccia rappresenta un thread in esecuzione in un programma.

## <a name="syntax"></a>Sintassi

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un thread di esecuzione in un unico programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) per ottenere questa interfaccia che rappresenta il thread attualmente attivo.

 Questa interfaccia viene inoltre usata nella creazione di una richiesta di punto di interruzione (vedere [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Questa interfaccia viene restituita anche durante la risoluzione di un punto di interruzione di limite o di errore (vedere [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) e [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugThread2`.

|Metodo|Descrizione|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Recupera un elenco degli stack frame per questo thread.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Ottiene il nome del thread.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Imposta il nome del thread.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Ottiene il programma in cui un thread è in esecuzione.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Determina se l'istruzione successiva può essere impostata nel contesto del determinato stack frame e il codice.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Imposta istruzione successiva nel contesto del determinato stack frame e il codice.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Ottiene l'identificatore di thread di sistema.|
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Sospende un thread.|
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Riprende un thread.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Ottiene le proprietà che descrivono un thread.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Ottiene il thread logico associato a questo thread fisico.|

## <a name="remarks"></a>Note
 Poiché un singolo thread fisici possono essere eseguiti in più programmi, maggiore di 1 `IDebugThread2` da più di un programma può rappresentare lo stesso thread fisico.

 Quando si verifica un punto di interruzione o eccezione, viene inviato un evento chiamando [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Uno degli argomenti di questo metodo è un `IDebugThread2` interfaccia che rappresenta il thread corrente. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) viene usato per ottenere il [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia per lo stack frame corrente.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)