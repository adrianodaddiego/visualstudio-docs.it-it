---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b574ae45dafed11ed28047859676524054951512
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65678962"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia viene utilizzata per notificare le modifiche al documento di origine che vengono fornite dal motore di debug di Visual Studio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per il supporto delle modifiche al codice sorgente. Questa interfaccia viene implementata in genere sullo stesso oggetto che implementa il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Ottiene questa interfaccia tramite una chiamata al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> (metodo). Il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia viene ottenuta da una chiamata al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> (metodo). Il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia viene ottenuta chiamando il [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) metodo su un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentTextEvents2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica che è stato eliminato l'intero documento.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica il pacchetto di debug che il testo è stato inserito nel documento.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica il pacchetto di debug che il testo è stato rimosso dal documento.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Informa il pacchetto di debug che è stato sostituito il testo nel documento.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica il pacchetto di debug che sono stati aggiornati gli attributi di testo nel documento.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al destinatario dell'evento che sono stati aggiornati gli attributi del documento.|  
  
## <a name="remarks"></a>Note  
 Solo i motori di debug che forniscono i propri documenti sarebbero poter sfruttare il `IDebugDocumentTextEvent2` interfaccia. Un esempio di questo sarebbe un motore di debug di script. In corso l'interpretazione degli script, può essere generato nuovo codice sorgente che non è presente in qualsiasi file di disco ed è noto solo per la Germania.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
