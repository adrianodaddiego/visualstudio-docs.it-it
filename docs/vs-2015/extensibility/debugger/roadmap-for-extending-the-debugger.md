---
title: Guida di orientamento per l'estensione del Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695963"
---
# <a name="roadmap-for-extending-the-debugger"></a>Guida di orientamento per l'estensione del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa documentazione vengono fornite informazioni di riferimento e Guida per l'estensione di [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] del debugger con la [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debug documentazione include esempi, un riferimento completo e numerosi scenari rappresentativi che illustrano i modi tipici per personalizzare il debugger.  
  
 Il compilatore e il relativo output determinare cosa è necessario eseguire per implementare il debug nel prodotto. Se il compilatore:  
  
- Ha come destinazione di Windows nativo del sistema operativo e scrive un. Il file PDB, eseguire il debug di programmi con il motore di debug di codice nativo (DE), integrata in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Non occorre implementare un analizzatore DE o un'espressione. L'analizzatore di espressioni viene scritto per la sintassi del linguaggio di programmazione C++.  
  
- Produce Microsoft intermediate language (MSIL) di output, è possibile eseguire il debug di programmi con il motore di debug di codice gestito, DE, che è anche integrato in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Di conseguenza, è necessario implementare solo un analizzatore di espressioni. Un analizzatore di espressioni di esempio viene fornito automaticamente. Per altre informazioni, vedere i seguenti argomenti:  
  
     [Valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Valutazione di espressioni](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contesto di valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Valutazione delle espressioni in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Scrittura di un analizzatore di espressioni di Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Destinato a un proprietario o un altro ambiente di runtime del sistema operativo, è necessario scrivere il proprio DE. Viene fornita un'esercitazione che crea un semplice DE utilizzando ATL COM. Per altre informazioni, vedere i seguenti argomenti:  
  
     [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Esercitazione: Creazione di un motore di Debug tramite COM ATL](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
