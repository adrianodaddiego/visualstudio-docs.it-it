---
title: Collegamento dopo un avvio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437428"
---
# <a name="attaching-after-a-launch"></a>Collegamento dopo un avvio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dopo aver avviato un programma, la sessione di debug è pronta per collegare il motore di debug (DE) a tale programma.  
  
## <a name="design-decisions"></a>Decisioni di progettazione  
 Poiché la comunicazione è più semplice all'interno di uno spazio di indirizzi condivisa, è necessario decidere se è più opportuno per facilitare la comunicazione tra la sessione di debug e il DE o tra il DE e il programma. Scegliere tra gli elementi seguenti:  
  
- Se è più opportuno per facilitare la comunicazione tra la sessione di debug e il DE, la sessione di debug CO-crea il DE e chiede di DE collegare al programma. In questo modo la sessione di debug e DE insieme in uno spazio indirizzi e l'ambiente di runtime e programma insieme in un altro.  
  
- Se è più opportuno per facilitare la comunicazione tra il DE e il programma, l'ambiente di runtime condiviso crea quindi il DE. In tal modo il modello SDM in uno spazio indirizzi e la Germania, ambiente run-time e programma insieme in un altro. Questo è tipico di un CRI implementata con un interprete per eseguire i linguaggi basati su script.  
  
    > [!NOTE]
    > Modalità la Germania viene associato al programma è dipendente dall'implementazione. Comunicazione tra il DE e il programma viene anche dipende dall'implementazione.  
  
## <a name="implementation"></a>Implementazione  
 A livello di codice quando la sessione debug manager (SDM) prima di tutto riceve la [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma da avviare, chiama il [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) passandogli un [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto, che è successivo usato per passare gli eventi di debug indietro per il modello SDM. Il `IDebugProgram2::Attach` chiama quindi il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (metodo). Per altre informazioni sul modo in cui il modello SDM riceve la `IDebugProgram2` dell'interfaccia, vedere [notifica della porta](../../extensibility/debugger/notifying-the-port.md).  
  
 Se la Germania deve essere eseguito nello spazio degli indirizzi stesso come il programma sottoposto a debug, in genere perché la Germania fa parte di un interprete eseguendo uno script, il `IDebugProgramNodeAttach2::OnAttach` restituzione del metodo `S_FALSE`, che indica che completato il processo di collegamento.  
  
 Se, d'altra parte, la Germania viene eseguito nello spazio degli indirizzi di SDM, il `IDebugProgramNodeAttach2::OnAttach` restituzione del metodo `S_OK` o il [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia non è affatto d'implementata il [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto associato al programma in fase di debug. In questo caso, il [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) viene chiamato alla fine per completare l'operazione di collegamento.  
  
 Nel secondo caso, è necessario chiamare il [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo sul `IDebugProgram2` che è stato passato al `IDebugEngine2::Attach` (metodo), store il `GUID` nel programma locale dell'oggetto e restituire this `GUID` quando il `IDebugProgram2::GetProgramId` viene successivamente chiamato su questo oggetto. Il `GUID` viene usato per identificare in modo univoco il programma per i vari componenti di debug.  
  
 Si noti che nel caso del `IDebugProgramNodeAttach2::OnAttach` metodo che restituisce `S_FALSE`, il `GUID` da usare per il programma viene passato al metodo ed è il `IDebugProgramNodeAttach2::OnAttach` metodo che imposta il `GUID` sull'oggetto programma locale.  
  
 La Germania è ora allegato al programma e pronto per inviare gli eventi di avvio.  
  
## <a name="see-also"></a>Vedere anche  
 [Collegamento diretto a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notifica della porta](../../extensibility/debugger/notifying-the-port.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Collegare](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
