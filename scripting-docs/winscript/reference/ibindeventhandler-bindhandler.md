---
title: IBindEventHandler::BindHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBindEventHandler.BindHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01372766eb434efe73f47b265c7984bab48ea164
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991382"
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
Associa un evento a un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrEvent`  
 [in] Specifica l'evento da gestire.  
  
 `pdisp`  
 [in] Specifica l'oggetto per gestire l'evento.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo associa un evento a un oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IBindEventHandler](../../winscript/reference/ibindeventhandler-interface.md)