---
title: IDebugEnumField::GetUnderlyingSymbol | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1841ca2bf9bd5a43ec5a16a515a03769db64ea15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955595"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il nome dell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppField`  
 [out] Restituisce il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descriva il nome di questa enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il nome dell'enumerazione contiene anche il tipo di enumerazione, che è associato a una posizione di memoria usando [associare](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)
