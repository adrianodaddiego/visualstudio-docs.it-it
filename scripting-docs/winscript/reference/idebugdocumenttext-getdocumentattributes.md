---
title: IDebugDocumentText::GetDocumentAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetDocumentAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetDocumentAttributes
ms.assetid: 8c544ca1-8db4-4bca-973e-09315d9a0ee5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8f545d9a8208440299d0dccb16145c6ef0c8731
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008657"
---
# <a name="idebugdocumenttextgetdocumentattributes"></a>IDebugDocumentText::GetDocumentAttributes
Restituisce gli attributi del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDocumentAttributes(  
   TEXT_DOC_ATTR*  ptextdocattr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ptextdocattr`  
 [out] Gli attributi di testo del documento.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce gli attributi del documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Costanti TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)