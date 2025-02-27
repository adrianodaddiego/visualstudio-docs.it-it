---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd5c0c6c056dc72f3db49a9d666d6f2ba6295791
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326012"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Questo metodo valuta l'espressione in modo asincrono.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EvaluateAsync (
    EVALFLAGS             dwFlags,
    IDebugEventCallback2* pExprCallback
);
```

```csharp
int EvaluateAsync(
    enum_EVALFLAGS       dwFlags,
    IDebugEventCallback2 pExprCallback
);
```

## <a name="parameters"></a>Parametri
`dwFlags`\
[in] Una combinazione di flag dal [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumerazione che controllano la valutazione dell'espressione.

`pExprCallback`\
[in] Questo parametro è sempre un valore null.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Un codice di errore tipico è:

|Error|Descrizione|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Un'altra espressione in fase di valutazione e la valutazione dell'espressione simultanee non è supportata.|

## <a name="remarks"></a>Note
Questo metodo deve restituire immediatamente dopo l'avvio della valutazione dell'espressione. Quando l'espressione viene valutata correttamente, un' [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) devono essere inviati al [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback di evento forniti tramite [Attach ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) oppure [collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un semplice `CExpression` oggetto che implementa le [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaccia.

```cpp
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,
                                   IDebugEventCallback2* pExprCallback)
{
    // Set the aborted state to FALSE
    // in case the user tries to redo the evaluation after aborting.
    m_bAborted = FALSE;
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.
    // This starts the expression evaluation on a background thread.
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);
    return S_OK;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
