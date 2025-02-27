---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955523"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mantiene dello stack di contesto tra le chiamate dei [Idiaframedata](../../debugger/debug-interface-access/idiaframedata-execute.md) (metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaStackWalkFrame`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Recupera il valore di un registro.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Imposta il valore di un registro.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Legge dall'immagine della memoria.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Cerca stack frame specificato per l'indirizzo del mittente (funzione) più vicino.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Cerca stack frame specificato per un indirizzo del mittente o in prossimità dell'indirizzo specificato.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene utilizzata durante l'esecuzione del programma per leggere e scrivere registri, nonché accedere alla memoria e trovare gli indirizzi restituiti.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 L'applicazione client implementa questa interfaccia e passa un'istanza dell'interfaccia per il [Idiaframedata](../../debugger/debug-interface-access/idiaframedata-execute.md) (metodo). La stessa istanza di questa interfaccia viene utilizzata ripetutamente per mantenere lo stato dei registri durante ogni richiamata del `execute` (metodo). Il `execute` metodo Usa inoltre questa interfaccia per stabilire l'indirizzo del mittente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: DIA2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
