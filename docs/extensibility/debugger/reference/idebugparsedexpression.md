---
title: IDebugParsedExpression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c56c0547d348c4fb3de387ac0ffce465b7bf5e90
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311784"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia rappresenta un'espressione analizzata pronta per essere valutata.

## <a name="syntax"></a>Sintassi

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un'espressione analizzata che è pronta per la valutazione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [analizzare](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente illustra il metodo di `IDebugParsedExpression`.

|Metodo|Descrizione|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Valuta l'espressione analizzata.|

## <a name="remarks"></a>Note
 Quando il chiamante è pronto per la valutazione dell'espressione, viene chiamato [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per restituire una [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che contiene il risultato della valutazione. Questo approccio due parti per la valutazione, l'analisi, la valutazione, consente l'espressione analizzata di essere valutati più volte, ignorando il lungo processo di analisi dell'espressione.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Analisi](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)