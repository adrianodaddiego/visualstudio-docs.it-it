---
title: IDebugMethodField::EnumParameters | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ebdd604ba97fda8751cf037e7494b59e7bb77ff
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969291"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumeratore per i parametri del metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppParams`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) dell'oggetto che rappresenta l'elenco di parametri al metodo; in caso contrario, restituisce un valore null se non sono presenti parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non sono presenti parametri. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ogni elemento è un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetti che rappresentano diversi tipi di parametri. Chiamare il [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metodo su ogni oggetto per determinare esattamente quale tipo di parametro l'oggetto rappresenta.  
  
 Un parametro include il nome di variabile e il relativo tipo. Il primo parametro a un metodo della classe è in genere il puntatore "this".  
  
 Se solo i tipi dei parametri è necessaria, chiamare il [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
