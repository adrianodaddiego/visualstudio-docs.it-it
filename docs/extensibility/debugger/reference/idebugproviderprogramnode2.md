---
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33c4a4914e15a8ecbea0d4f28c2325a952a042de
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353810"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Questa interfaccia effettua il marshalling di interfacce relative al programma attraverso i limiti di processo.

## <a name="syntax"></a>Sintassi

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia nello stesso oggetto che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per supportare le interfacce di marshalling tra i limiti dei processi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProgramNode2` interfaccia per ottenere questa interfaccia. Se non è possibile ottenere questa interfaccia, la Germania non supporta il marshalling delle interfacce.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ottiene un'interfaccia specificata attraverso i limiti dei processi.|

## <a name="remarks"></a>Note
 Questa interfaccia viene implementata quando viene eseguita la Germania in uno spazio processi distinto dal programma in fase di debug: ad esempio, quando la Germania è in esecuzione nello spazio di processo Visual Studio anziché lo spazio di processo del programma in fase di debug.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)