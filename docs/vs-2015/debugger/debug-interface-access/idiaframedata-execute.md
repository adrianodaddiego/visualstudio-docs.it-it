---
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4042cf58ee34b5f49df601b94e1110f03e0b6f5b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969156"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esegue la rimozione dello stack e restituisce i risultati in un'interfaccia di frame dello stack del percorso.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `frame`  
 [in] Un' [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) oggetto che contiene lo stato dei registri di frame.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra i valori restituiti possibili per questo metodo.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Non è possibile eseguire uno stack frame nel codice di prologo.|  
|E_DIA_SYNTAX|Analizzare l'errore nel programma di frame.|  
|E_DIA_FRAME_ACCESS|Non è possibile registri di accesso o la memoria.|  
|E_DIA_VALUE|Errore nel calcolo di un valore (ad esempio, la divisione per zero).|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato durante il debug di rimozione dello stack. Il [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) oggetto viene implementato dall'applicazione client per ricevere gli aggiornamenti per i registri e fornire i metodi utilizzati dal `execute` (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
