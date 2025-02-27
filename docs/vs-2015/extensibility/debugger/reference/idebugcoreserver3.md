---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1781b133b4c3ee95b4207a0dd237e2dd7298a1
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685655"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia fornisce accesso alle informazioni sul server che in cui viene eseguito il processo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Uso [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per ottenere questa interfaccia da un' [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia. Una chiamata a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) può restituire anche questa interfaccia. Questa interfaccia viene utilizzata in genere da un fornitore di porte personalizzate per avviare i programmi in un server (locale o remoto).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia, questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera il nome del server.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera una versione breve del nome del server|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indica i motori di debug specifiche connettersi automaticamente ai processi quando avvia i processi.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera un codice di errore specifico quando automatico collegamento ha esito negativo.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crea un'istanza di un motore di debug nel server.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera un flag che indica se il server è nello stesso computer del chiamante.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera un valore che indica il protocollo usato per comunicare con il server.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Disabilita tutte le connessione automatica le impostazioni per tutti i motori di debug, che questo server è a conoscenza.|  
  
## <a name="remarks"></a>Note  
 Un fornitore di porte personalizzato riceve la [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia in una chiamata a [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md). Il `IDebugCoreServer3` interfaccia può essere ottenuta da tale interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
