---
title: IDebugApplication::RemoveGlobalExpressionContextProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveGlobalExpressionContextProvider
ms.assetid: ace638a3-ed34-4d20-8404-45c684aaaf1a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12ac95ee040d3813aa1fcac6358b8328c780a9d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990795"
---
# <a name="idebugapplicationremoveglobalexpressioncontextprovider"></a>IDebugApplication::RemoveGlobalExpressionContextProvider
Rimuove un provider di contesto dell'espressione globale da questa applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT RemoveGlobalExpressionContextProvider(  
   DWORD_PTR  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCookie`  
 [in] Il cookie restituito dal `AddGlobalExpressionContextProvider` metodo quando è stato aggiunto il provider di contesto globale.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il `RemoveGlobalExpressionContextProvider` metodo rimuove un provider di contesto dell'espressione globale da questa applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)   
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)