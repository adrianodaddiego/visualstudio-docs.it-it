---
title: I programmi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9070b33c7522cdc13fd6217956fcab72cd83f8d1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069442"
---
# <a name="programs"></a>Programs
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **programma**:  
  
- È un contenitore per un set di thread e un set di moduli. Un programma non ha nessuna analogia singolo nel sistema operativo Windows.  
  
     Un programma è un tipo di processo secondario. Ad esempio, quando si esegue il debug di un sito Web, uno script può essere considerato un programma. Mentre è in esecuzione uno script nel processo del motore di scripting, indipendente da altri script, include anche un proprio set di thread. Un motore di debug (DE) viene associato a un programma e non a un processo o un thread.  
  
- Possibile identificare se stesso e il processo in esecuzione in e può essere collegato per essere disconnesso da e descrivono il DE che ha creato, se presente. Un programma possa eseguire, arrestare, continuare e terminare.  
  
- Possibile enumerare tutti i relativi thread. Un programma può fornire anche il proprio flusso disassembly e possa enumerare tutti i contesti di codice di una posizione del documento specificato.  
  
- È rappresentato da un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaccia, creata prima che il programma viene collegato o come parte del processo di collegamento, a seconda dell'implementazione. Quando una porta enumera i programmi di un processo, viene creato ogni programma in base a una corrispondente [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) passata come argomento a interfaccia [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Mentre i motori di debug anche creare `IDebugProgram2` interfacce per rappresentare i programmi, questi programmi non vengono create in base a un nodo di programma. Il `IDebugProgramNode2` interfacce create da un CRI vengono usate per eseguire il debug effettivi, mentre quelli creati da una porta sono utilizzati solo per l'individuazione dei quali programmi sono in esecuzione in un processo.  
  
## <a name="see-also"></a>Vedere anche  
 [Processi](../../extensibility/debugger/processes.md)   
 [Nodi di programma](../../extensibility/debugger/program-nodes.md)   
 [Moduli](../../extensibility/debugger/modules.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Posizione di documento](../../extensibility/debugger/document-position.md)   
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
