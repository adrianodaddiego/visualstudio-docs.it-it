---
title: Valutazione di un'espressione di finestra Espressioni di controllo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f13573cfecbd81f36e3b77e9b23beeaa558c08dc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444795"
---
# <a name="evaluating-a-watch-window-expression"></a>Valutazione di un'espressione della finestra Espressioni di controllo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando l'esecuzione viene sospesa, Visual Studio chiama il motore di debug (DE) per determinare il valore corrente di ogni espressione nel proprio elenco di espressioni di controllo. La Germania valuta ogni espressione utilizzando un analizzatore di espressioni (EE) e viene visualizzato il relativo valore in Visual Studio il **Watch** finestra.  
  
 Di seguito viene fornita una panoramica del modo in cui viene valutata un'espressione di elenco di controllo:  
  
1. Visual Studio chiama il DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il contesto di un'espressione che può essere utilizzato per valutare le espressioni.  
  
2. Per ogni espressione nell'elenco di espressioni di controllo, Visual Studio chiama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per convertire il testo dell'espressione in un'espressione analizzata.  
  
3. `IDebugExpressionContext2::ParseText` le chiamate [analizzare](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per svolgere il lavoro effettivo dell'analisi di testo e producono un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto.  
  
4. `IDebugExpressionContext2::ParseText` Crea un' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto e vi inserisce le `IDebugParsedExpression` oggetti al suo interno. Questo si`DebugExpression2` oggetto viene quindi restituito a Visual Studio.  
  
5. Le chiamate di Visual Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per valutare l'espressione analizzata.  
  
6. `IDebugExpression2::EvaluateSync` passa la chiamata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per eseguire la valutazione effettiva e produrre un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto restituito a Visual Studio.  
  
7. Le chiamate di Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ottenere il valore dell'espressione che viene quindi visualizzato nell'elenco di espressioni di controllo.  
  
## <a name="parse-then-evaluate"></a>Analizzare e valutare  
 Poiché l'analisi di un'espressione complessa può richiedere molto più lunga della valutazione, il processo di valutazione di un'espressione è suddiviso in due passaggi: 1) analisi l'espressione e 2) valuta l'espressione analizzata. In questo modo, la valutazione può verificarsi più volte, ma l'espressione deve essere analizzata una sola volta. L'espressione analizzata intermedia viene restituito dal motore di esecuzione in un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) che a sua volta è incapsulato e restituito dal DE come un' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto. Il `IDebugExpression` oggetto rinvia valutazione di tutti i `IDebugParsedExpression` oggetto.  
  
> [!NOTE]
> Non è necessario per un EE essere conformi a questo processo in due passaggi anche se Visual Studio presuppone che questa classe. l'analizzatore di Espressioni può analizzare e valutare nello stesso passaggio quando [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) viene chiamato (si tratta MyCEE funzionamento del campione, ad esempio). Se la lingua può formare espressioni complesse, è possibile separare la fase di analisi del passaggio di valutazione. Ciò può migliorare le prestazioni nel debugger di Visual Studio quando molte espressioni di controllo vengono riprodotti.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di esempio di valutazione delle espressioni](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Usa l'esempio MyCEE per eseguire passo passo il processo di valutazione dell'espressione.  
  
 [Valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Viene illustrato cosa accade dopo un'analisi dell'espressione ha esito positivo.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti passati quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE).  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
