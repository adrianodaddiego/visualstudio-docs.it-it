---
title: Stack frame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de3a0267d366f926fa5705c7455b237cafe4820a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348500"
---
# <a name="stack-frames"></a>Stack frame
Nell'architettura di debugger, un *frame dello stack*:

- È un'astrazione di un oggetto stack che fornisce il contesto di esecuzione di un thread. Un thread viene sempre eseguito all'interno di una funzione. Uno stack frame contiene le variabili locali della funzione e gli argomenti ad esso. Per eseguire il debug con Visual Studio, la lingua o l'ambiente in fase di debug deve supportare gli stack frame.

- Possono entrambi identificare e descrivere se stesso e può restituire il thread associato. Uno stack frame può restituire anche il contesto del codice che rappresenta il puntatore all'istruzione corrente e la documentazione associata e contesti di valutazione di espressione.

- Dispone di proprietà che descrivono il nome, tipo e valore di argomenti e variabili locali e che vengono visualizzati nelle varie finestre di debug dell'IDE.

- È rappresentato da un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia, in genere creato da un motore di debug (DE) o una macchina virtuale come conseguenza l'esecuzione di un thread.

## <a name="see-also"></a>Vedere anche
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)