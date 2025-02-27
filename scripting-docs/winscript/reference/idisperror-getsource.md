---
title: IDispError::GetSource | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a84640f020a1ff255b8c7e5dd753752e0d310a7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446889"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Restituisce l'identificatore a livello di codice dipendente dalla lingua per la classe o un'applicazione che ha generato l'errore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrSource`  
 [out] Stringa che contiene un identificatore a livello di codice, nel formato `progname.objectname`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato per determinare la classe o l'applicazione in cui si è verificata l'eccezione. L'identificatore a livello di codice può essere restituito nel linguaggio specificato dall'identificatore delle impostazioni locali (LCID) fornito al momento della chiamata.  
  
> [!NOTE]
> Questo metodo non è implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispError](../../winscript/reference/idisperror-interface.md)