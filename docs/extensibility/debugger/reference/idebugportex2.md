---
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bed6cd047af4ba57a1880d87e30a990dcf83efac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340437"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Questa interfaccia consente la sessione di debug controllo manager (SDM) i programmi e i processi in esecuzione su una porta.

## <a name="syntax"></a>Sintassi

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia nello stesso oggetto che implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Le chiamate SDM [QueryInterface](/cpp/atl/queryinterface) nel `IDebugPort2` interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugPortEx2`.

|Metodo|Descrizione|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Avvia un file eseguibile.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Riprende l'esecuzione di un processo.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina se un processo può essere terminato.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Termina un processo.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ottiene l'ID del processo della porta di se stesso.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ottiene un programma associato a un nodo di programma.|

## <a name="remarks"></a>Note
 Questa interfaccia è in genere privata tra il modello SDM e il fornitore della porta personalizzata.

 Se si desidera, un motore di debug (DE) può cercare questa interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia passata al [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) allo stesso modo [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) per avviare il programma. Tuttavia, non è un requisito, e un CRI possono eseguire tutte le attività per avviare il programma di richiesta.

## <a name="requirements"></a>Requisiti
 Intestazione: portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)