---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f7192eb7b2fa6d8bc886c0e601788ecba8eebcd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965048"
---
# <a name="bpflags90"></a>BP_FLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enumera i valori validi per i flag facoltativi. Il flag facoltativo consente di specificare informazioni aggiuntive quando si imposta un punto di interruzione. Questa enumerazione estende la [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 BP90_FLAG_NONE  
 Non specifica alcun flag per il punto di interruzione.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Specifica che il motore di debug (DE) deve eseguire il mapping del punto di interruzione usando la posizione del documento. Ciò si applica solo ai punti di interruzione impostati nei file di origine orientata ai servizi script, ad esempio le pagine ASP (Active Server).  
  
 BP90_FLAG_DONT_STOP  
 Specifica che il punto di interruzione deve essere elaborato dal motore di debug, ma che il motore di debug in definitiva non deve arrestare vale a dire, un' [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) oggetto dell'evento non deve essere inviato. Questo flag è progettato per essere utilizzati principalmente con i punti di traccia.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Utilizzato dal motore di debug nativo per determinare se lo stato di avanzamento nell'esecuzione deve essere cancellato. Si differenzia dal BP90_FLAG_DONT_STOP perché BP90_FLAG_DONT_STOP non è impostato se il punto di traccia viene eseguita una macro.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg90.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
