---
title: Interfacce di fornitore di porte necessarie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82e70ea9a4ba30b6b1d312188a91d9c0c8aa2904
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116641"
---
# <a name="required-port-supplier-interfaces"></a>Interfacce obbligatorie dei fornitori di porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un fornitore di porte deve implementare il [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interface.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Poiché un fornitore di porte fornisce porte, è necessario implementare anche loro. Pertanto, deve implementare le interfacce seguenti:  
  
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Descrive la porta e possono enumerare tutti i processi in esecuzione sulla porta.  
  
- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Fornisce per l'avvio e terminazione dei processi sulla porta.  
  
- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Fornisce un meccanismo per i programmi in esecuzione nel contesto di questa porta per inviare una notifica di eliminazione e la creazione di nodi di programma. Per altre informazioni, vedere [nodi di programma](../../extensibility/debugger/program-nodes.md).  
  
- `IConnectionPointContainer`  
  
     Fornisce un punto di connessione per [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operazione fornitore della porta  
 Il [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) sink riceve le notifiche quando il processo e i programmi vengono creati e distrutti su una porta. Una porta è necessaria per inviare [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando viene creato un processo e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando un processo viene eliminato definitivamente sulla porta. Una porta è necessaria anche per inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando viene creato un programma e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando viene eliminato un programma in un processo in esecuzione sulla porta.  
  
 Una porta in genere invia programma creare ed eliminare definitivamente gli eventi in risposta al [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) e [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) metodi, rispettivamente.  
  
 Poiché una porta può avviare e terminare i processi fisici sia logici programmi, anche queste interfacce devono essere implementate dal motore di debug:  
  
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Descrive il processo fisico. Almeno devono essere implementati i metodi seguenti:  
  
    - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Fornisce un modo per il modello SDM collegare e scollegare se stesso da un processo.  
  
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Descrive la logica del programma. Almeno devono essere implementati i metodi seguenti:  
  
    - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Fornisce un modo per il modello SDM collegare a questo programma.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
