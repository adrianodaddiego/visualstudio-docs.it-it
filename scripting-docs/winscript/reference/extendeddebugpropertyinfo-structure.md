---
title: Struttura ExtendedDebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fe0eef00d2bf064a8a002925f4ba5607d36f31c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955184"
---
# <a name="extendeddebugpropertyinfo-structure"></a>Struttura ExtendedDebugPropertyInfo
Estende il `DebugPropertyInfo` struttura con membri aggiuntivi per caratterizzare la proprietà estesa.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Membri  
 `dwValidFields`  
 Tipo di dati enumerato consente di specificare quali campi vengono inizializzati.  
  
 `bstrName`  
 Il nome della proprietà all'interno di un contesto.  
  
 `bstrType`  
 Il tipo di proprietà come stringa formattata.  
  
 `bstrValue`  
 Il valore della proprietà come stringa formattata.  
  
 `bstrFullName`  
 Nome completo della proprietà.  
  
 `dwAttrib`  
 Enumerazione che specifica i flag per gli attributi della proprietà di debug.  
  
 `pDebugProp`  
 `IDebugProperty` oggetto che corrisponde a questo `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 L'id di invio.  
  
 `nType`  
 Il tipo della proprietà estesa.  
  
 `varValue`  
 Il valore della proprietà estesa se può essere adattato nella variante.  
  
 `plbValue`  
 Byte di dati effettivo del valore della proprietà.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` oggetto che corrisponde a questo `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Vedere anche  
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Interfaccia IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)