---
title: Interfaccia IEnumJsStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e8302737fb4abf96c55d3ae70424cc03579b270
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963325"
---
# <a name="ienumjsstackframes-interface"></a>Interfaccia IEnumJsStackFrames
Implementata dal debugger per fornire dello stack di rimozione in jscript9diag.dll per JavaScript.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Ottiene il numero di frame specificato.|  
|[Metodo IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Reimposta lo stack frame alla posizione prima del primo elemento.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)