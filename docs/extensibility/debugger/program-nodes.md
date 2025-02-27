---
title: I nodi di programma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 084a386cc7d7f9c6d606e7015e593a4075ba53a9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351433"
---
# <a name="program-nodes"></a>Nodi di programma
Nell'architettura di debugger, un *nodo programma*:

- È una semplice descrizione di un programma.

- Possibile identificare se stesso e il processo in che è in esecuzione. Un nodo del programma può essere collegato per essere disconnesso da e descrivere il motore di debug (DE) cui è stato creato, se presente.

- È rappresentato da un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia, in genere creato da una porta o DE. Nodi di programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando viene aggiunto un nodo di programma a una porta, aggiungerlo al processo che contiene il programma che rappresenta questo nodo del programma.

  Un certo punto dopo una sessione di debug viene avviata, a seconda dell'implementazione del pacchetto di debug, nodi di programma vengono usati per creare programmi corrispondenti. Quando un processo viene eseguita una query per i relativi programmi, vengono enumerati i programmi, uno per ogni nodo del programma.

  Prima di un programma viene collegato, l'IDE deve solo una semplice descrizione del programma. Queste informazioni possono essere ottenute dal nodo del programma. Una volta il programma viene collegato, l'IDE visualizza le informazioni più dettagliate, ad esempio un elenco di tutti i thread in esecuzione del programma. Queste informazioni vengono ottenute dal programma stesso.

## <a name="see-also"></a>Vedere anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Processi](../../extensibility/debugger/processes.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)