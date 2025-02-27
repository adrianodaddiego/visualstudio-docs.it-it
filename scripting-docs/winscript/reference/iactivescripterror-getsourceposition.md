---
title: IActiveScriptError::GetSourcePosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4446235a9584bc45fad84b6f92ecc02592e554f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009624"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Recupera la posizione nel codice sorgente in cui un errore durante il motore di script era in esecuzione uno script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwSourceContext`  
 [out] Indirizzo di una variabile che riceve un cookie che identifica il contesto. L'interpretazione di questo parametro dipende dall'applicazione host.  
  
 `pulLineNumber`  
 [out] Indirizzo di una variabile che riceve il numero di riga nel file di origine in cui si è verificato l'errore.  
  
 `pichCharPosition`  
 [out] Indirizzo di una variabile che riceve la posizione del carattere nella riga in cui si è verificato l'errore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` caso di esito positivo o `E_FAIL` se il percorso non è stato recuperato.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)