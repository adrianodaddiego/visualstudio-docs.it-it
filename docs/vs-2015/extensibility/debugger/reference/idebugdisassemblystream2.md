---
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b5126758c60262564390f84b6278300a41660f5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955272"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un flusso di istruzioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un motore di debug implementa questa interfaccia supporta il disassembly del codice del programma.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata per il [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metodo restituisce questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugDisassemblyStream2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Legge le istruzioni a partire dalla posizione corrente nel flusso di disassemblaggio.|  
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Sposta il puntatore di lettura nel flusso di disassemblaggio di un determinato numero di istruzioni rispetto alla posizione specificata.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Restituisce un identificatore percorso codice per un contesto di codice specifico.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Restituisce un oggetto di contesto codice corrispondente a un identificatore percorso codice specificato.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Restituisce un identificatore percorso codice che rappresenta il percorso di codice corrente.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ottiene il documento di origine associato a questo flusso disassembly.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ottiene l'ambito di questo flusso disassembly.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ottiene le dimensioni di questo flusso disassembly.|  
  
## <a name="remarks"></a>Note  
 È possibile creare il flusso disassembly per rappresentare l'intero spazio indirizzi o semplicemente una funzione o un modulo all'interno dello spazio. Ogni istruzione è rappresentata da un [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struttura restituita da una chiamata ai [lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
