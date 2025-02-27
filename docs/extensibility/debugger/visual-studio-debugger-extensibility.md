---
title: Estendibilità del Debugger di Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4184ae40a91e05b1110aed8d3e9b9c9edc64a06d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321482"
---
# <a name="visual-studio-debugger-extensibility"></a>Estendibilità del debugger Visual Studio
Visual Studio include un debugger di codice sorgente completamente interattivi, che fornisce uno strumento potente e facile da usare per tenere traccia dei bug nel programma. Il debugger ha supporto completo per Visual Basic, c#, C/C++ e JavaScript. Tuttavia, con il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vale a dire disponibile la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), altri linguaggi di programmazione possono essere supportati nel debugger con le stesse funzionalità avanzate.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger è il front-end comune (vale a dire, l'interfaccia utente) per i componenti di debug che sono, a sua volta, a seconda della lingua in fase di debug. Per nuove lingue, è sufficiente per supportare dal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger consiste nel creare i componenti necessari di back-end, ad esempio un motore di debug (DE). In questo punto è dove il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] è disponibile in.

 Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] include un riferimento completo a tutti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementi necessari per creare un nuovo DE. Inoltre, esistono esempi ed esercitazioni utili per iniziare a usare.

 Per un esempio completo di un sistema di progetto linguaggio con il supporto del debug, vedere la [esempio di IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Le sezioni seguenti viene descritto come estendere il debugger usando la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>Contenuto della sezione
 [Iniziare a usare](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) descrive cosa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug offerte e su come installare il SDK.

 [Creare un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) illustra il processo DE personalizzato, dalla preparazione programma per un CRI per scollegare il DE.

 [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) spiega se è necessario scrivere un analizzatore di espressioni.

 [Scegliere una strategia di implementazione del motore di debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) viene illustrato come implementare il DE.

 [Riferimento](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) documenti il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API di debug.

 [Esempi di](../../extensibility/debugger/visual-studio-debugging-samples.md) contiene collegamenti a un esempio dell'analizzatore di espressioni espressione di common language runtime e un esempio di motore di debug.
