---
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 18edddd698953bf71febb8f9f2f1bac704205120
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703932"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia nei registri o Annulla la registrazione di un programma che è possibile eseguire il debug con la porta in cui viene eseguito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia per supportare l'aggiunta e rimozione di programmi dalla porta. Viene in genere implementato nello stesso oggetto che implementa il [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) nel `IDebugPort2` interfaccia restituisce questa interfaccia. Inoltre, una chiamata a [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) restituisce questa interfaccia. Un motore di debug è possibile visualizzare questa interfaccia come parametro per [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortNotify2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programma che è possibile eseguire il debug con la porta in cui viene eseguito.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annulla la registrazione di un programma che è possibile eseguire il debug dalla porta di che cui è in esecuzione.|  
  
## <a name="remarks"></a>Note  
 A meno che una porta di debug è un modo per sapere quando i programmi vengono caricati o scaricati, un fornitore di porte personalizzato deve implementare questa interfaccia. Tutti i programmi che vengono caricati per l'esecuzione del debug attraverso una porta specifica vengono rilevati tramite questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
