---
title: Valutazione dell'espressione in modalità di interruzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116225"
---
# <a name="expression-evaluation-in-break-mode"></a>Valutazione delle espressioni in modalità di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire la valutazione dell'espressione.  
  
## <a name="expression-evaluation-process"></a>Processo di valutazione di espressioni  
 Questi sono i passaggi fondamentali nella valutazione di un'espressione:  
  
1. Gestore di sessione di debug (SDM) chiama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere un'interfaccia di contesto, espressione [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2. Chiama quindi il modello SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la stringa da analizzare.  
  
3. Se ParseText non restituisce S_OK, viene restituito il motivo dell'errore.  
  
     -otherwise-  
  
     Se ParseText restituisce S_OK, il modello SDM può quindi chiamare [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oppure [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere un valore finale dall'espressione analizzata.  
  
    - In caso di utilizzo `IDebugExpression2::EvaluateSync`, l'interfaccia di callback specificato viene utilizzato per comunicare il processo continuo di valutazione. Viene restituito il valore finale un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.  
  
    - In caso di utilizzo `IDebugExpression2::EvaluateAsync`, l'interfaccia di callback specificato viene utilizzato per comunicare il processo continuo di valutazione. Una volta completata la valutazione, EvaluateAsync invia un' [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaccia tramite il callback. Con questa interfaccia, è possibile ottenere il valore finale con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
