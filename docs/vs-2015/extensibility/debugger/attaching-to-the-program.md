---
title: Collegamento al programma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab9301f31976b084c3c8565329dca248503e40ae
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437421"
---
# <a name="attaching-to-the-program"></a>Collegamento al programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dopo avere registrato i programmi con la porta appropriata, è necessario connettere il debugger al programma da sottoporre a debug.  
  
## <a name="choosing-how-to-attach"></a>Scelta di come collegare  
 Esistono tre modi in cui la gestione del debug sessione (SDM) prova a collegare al programma in corso il debug.  
  
1. Per i programmi che vengono avviati dal motore di debug tramite il [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metodo (tipica dei linguaggi interpretati, ad esempio), il modello SDM Ottiene le [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia da il [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associato al programma da connettere all'oggetto. Se il modello SDM può ottenere il `IDebugProgramNodeAttach2` interfaccia, il modello SDM chiama quindi il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (metodo). Il `IDebugProgramNodeAttach2::OnAttach` restituzione del metodo `S_OK` per indicare che non è stato allegato al programma e che possono essere eseguiti altri tentativi per collegare al programma.  
  
2. Se il modello SDM può ottenere il [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) dell'interfaccia dal programma che viene connesso a, le chiamate SDM il [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) (metodo). Questo approccio è tipico per i programmi che sono stati avviati in remoto dal fornitore della porta.  
  
3. Se il programma non può essere collegato tramite il `IDebugProgramNodeAttach2::OnAttach` o `IDebugProgramEx2::Attach` metodi, il modello SDM carica il motore di debug (se non è già caricato) chiamando il `CoCreateInstance` (funzione) e quindi chiama il [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) (metodo). Questo approccio è tipico per i programmi avviati in locale da un fornitore di porte.  
  
    È anche possibile che un fornitore di porte personalizzato chiamare il `IDebugEngine2::Attach` nell'implementazione del fornitore della porta personalizzata del metodo di `IDebugProgramEx2::Attach` (metodo). In genere in questo caso, il fornitore della porta personalizzata consente di avviare il motore di debug nel computer remoto.  
  
   Allegato avviene quando il gestore di sessione di debug (SDM) chiama il [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) (metodo).  
  
   Se si esegue il DE nello stesso processo dell'applicazione da sottoporre a debug, quindi è necessario implementare i metodi seguenti della [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
  Dopo il `IDebugEngine2::Attach` viene chiamato il metodo, seguire questi passaggi nell'implementazione del `IDebugEngine2::Attach` metodo:  
  
1. Invio di un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) oggetto dell'evento per il modello SDM. Per altre informazioni, vedere [l'invio di eventi](../../extensibility/debugger/sending-events.md).  
  
2. Chiamare il [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo sul [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) oggetto passato per il `IDebugEngine2::Attach` (metodo).  
  
     Restituisce un `GUID` che viene usato per identificare il programma. Il `GUID` devono essere archiviate nell'oggetto che rappresenta il programma di locale per la Germania e deve essere restituito quando il `IDebugProgram2::GetProgramId` metodo viene chiamato sul `IDebugProgram2` interfaccia.  
  
    > [!NOTE]
    > Se si implementa il `IDebugProgramNodeAttach2` dell'interfaccia, il programma `GUID` viene passato per il `IDebugProgramNodeAttach2::OnAttach` (metodo). Ciò `GUID` viene usato per il programma `GUID` restituiti dai `IDebugProgram2::GetProgramId` (metodo).  
  
3. Invio di un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) oggetto dell'evento per notificare il modello SDM che locale `IDebugProgram2` oggetto è stato creato per rappresentare il programma per la Germania. Per informazioni dettagliate, vedere [l'invio di eventi](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    > Ciò non è uguale `IDebugProgram2` oggetto passato il `IDebugEngine2::Attach` (metodo). Il valore passato in precedenza `IDebugProgram2` oggetto riconosciuto da solo la porta ed è un oggetto separato.  
  
## <a name="see-also"></a>Vedere anche  
 [Attacco basato su avvio](../../extensibility/debugger/launch-based-attachment.md)   
 [L'invio di eventi](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Collegare](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
