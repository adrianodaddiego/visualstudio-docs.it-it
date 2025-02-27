---
title: IRemoteDebugApplicationEvents Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEvents interface
ms.assetid: 9626519e-910c-48e0-ae99-c711ce6628fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 052a408d6e92066c14617f46f722d3e603985195
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943800"
---
# <a name="iremotedebugapplicationevents-interface"></a>Interfaccia IRemoteDebugApplicationEvents
Il `IRemoteDebugApplicationEvents` è l'interfaccia di eventi fornita da un'applicazione di debug. Questa interfaccia viene sempre chiamata dall'interno del thread del debugger.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IRemoteDebugApplicationEvents` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplicationEvents::OnConnectDebugger](../../winscript/reference/iremotedebugapplicationevents-onconnectdebugger.md)|Evento connect gli handle di un debugger.|  
|[IRemoteDebugApplicationEvents::OnDisconnectDebugger](../../winscript/reference/iremotedebugapplicationevents-ondisconnectdebugger.md)|Debugger gestisce l'evento di disconnessione.|  
|[IRemoteDebugApplicationEvents::OnSetName](../../winscript/reference/iremotedebugapplicationevents-onsetname.md)|Gestisce l'evento nome set.|  
|[IRemoteDebugApplicationEvents::OnDebugOutput](../../winscript/reference/iremotedebugapplicationevents-ondebugoutput.md)|Gestisce un evento di output del debugger.|  
|[IRemoteDebugApplicationEvents::OnClose](../../winscript/reference/iremotedebugapplicationevents-onclose.md)|Gestisce un evento di chiusura dell'applicazione.|  
|[IRemoteDebugApplicationEvents::OnEnterBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onenterbreakpoint.md)|Gestisce un evento per l'immissione di un punto di interruzione.|  
|[IRemoteDebugApplicationEvents::OnLeaveBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onleavebreakpoint.md)|Gestisce un evento per uscire da un punto di interruzione.|  
|[IRemoteDebugApplicationEvents::OnCreateThread](../../winscript/reference/iremotedebugapplicationevents-oncreatethread.md)|Gestisce l'evento create thread.|  
|[IRemoteDebugApplicationEvents::OnDestroyThread](../../winscript/reference/iremotedebugapplicationevents-ondestroythread.md)|Gestisce l'evento thread eliminato.|  
|[IRemoteDebugApplicationEvents::OnBreakFlagChange](../../winscript/reference/iremotedebugapplicationevents-onbreakflagchange.md)|Gestisce un evento quando cambiano i flag di interruzione.|