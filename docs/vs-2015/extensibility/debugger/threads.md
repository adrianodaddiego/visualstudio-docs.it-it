---
title: Thread | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 028ad25495ba01d9763c8bec3bbb9c4480d72ff8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054586"
---
# <a name="threads"></a>Thread
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **thread**:  
  
- È l'unità fondamentale di calcolo. Un thread viene eseguito in modo sequenziale le proprie istruzioni all'interno del contesto di uno stack di chiamate singolo, lo spostamento dal contesto di un codice a quella successiva.  
  
- Possibile identificare se stesso e il programma è in esecuzione in e può essere denominato, sospesa e ripresa. Un thread può inoltre enumerare relativo frame dello stack associata e, in alcune condizioni, può essere spostato in un altro stack frame. Dato il contesto di un frame dello stack, un thread può restituire il thread logico associato, se presente. Un thread dispone di proprietà, ad esempio un conteggio di sospensione, che possono essere visualizzati nella finestra thread dell'IDE.  
  
- È rappresentato da un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaccia, in genere creato da un motore di debug (DE) o una macchina virtuale di conseguenza l'esecuzione di un programma.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Gestione del debug delle sessioni](../../extensibility/debugger/session-debug-manager.md)
