---
title: La scrittura di un analizzatore di espressioni di Common Language Runtime | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c295fcd881ed5348842355846c37af95b725f17e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348242"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>La scrittura di un analizzatore di espressioni di common language runtime
> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'analizzatore di espressioni (EE) è la parte di un motore di debug (DE) che gestisce la sintassi e semantica del linguaggio di programmazione che ha generato il codice in fase di debug. Le espressioni devono essere valutate nel contesto di un linguaggio di programmazione. In alcuni linguaggi, ad esempio, l'espressione "A + B" significa "la somma di A e b." In altre lingue, la stessa espressione potrebbe significare "A o B." Di conseguenza, un oggetto separato EE deve essere scritta per ogni linguaggio di programmazione che genera il codice oggetto da sottoporre a debug nell'IDE di Visual Studio.

 Alcuni aspetti del pacchetto di debug di Visual Studio devono interpretare il codice nel contesto del linguaggio di programmazione. Ad esempio, quando si interrompe l'esecuzione in un punto di interruzione, tutte le espressioni che l'utente ha digitato in un **Watch** finestra deve essere valutata e visualizzata. L'utente può modificare il valore di una variabile locale, digitare un'espressione in una **Watch** finestra o nel **immediato** finestra.

## <a name="in-this-section"></a>Contenuto della sezione
 [Valutazione di Common language runtime ed espressione](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) illustra che quando si integra il linguaggio di programmazione proprietario nell'IDE di Visual Studio, la scrittura di un EE in grado di valutazione di espressioni all'interno del contesto del linguaggio proprietaria Consente di compilare in Microsoft intermediate language (MSIL) senza dover scrivere un motore di debug.

 [Architettura dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-architecture.md) viene illustrato come implementare le interfacce necessarie EE e chiamare il provider di simboli di common language runtime (SP) e le interfacce dello strumento di associazione.

 [Registrare un analizzatore di espressioni](../../extensibility/debugger/registering-an-expression-evaluator.md) note che l'analizzatore di Espressioni deve registrarsi come una class factory con sia il common language runtime e gli ambienti di runtime di Visual Studio.

 [Implementare un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md) viene descritto come il processo di valutazione di un'espressione include il motore di debug (DE), il provider di simboli (SP), l'oggetto strumento di associazione e l'analizzatore di espressioni (EE).

 [Visualizzare variabili locali](../../extensibility/debugger/displaying-locals.md) descrive come, quando l'esecuzione viene sospesa, il pacchetto di debug chiama il DE per ottenere un elenco di argomenti e variabili locali.

 [Valutare un'espressione di controllo finestra](../../extensibility/debugger/evaluating-a-watch-window-expression.md) documenta come pacchetto di debug di Visual Studio chiama il DE per determinare il valore corrente di ogni espressione nel proprio elenco di espressioni di controllo.

 [Modificare il valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md) spiega che modifica il valore di una variabile locale, ogni riga della finestra variabili locali è associato un oggetto che fornisce il nome, tipo e il valore corrente di una variabile locale.

 [Implementare i visualizzatori di tipi e visualizzatori personalizzati](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) viene illustrato quale interfaccia deve essere implementata da quale componente per supportare i visualizzatori di tipi e visualizzatori personalizzati.

## <a name="see-also"></a>Vedere anche
 [Estendibilità del debugger Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)