---
title: IDebugArrayField::GetNumberOfElements | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5627f263d743c4f8c83de683c24baf21cf594a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966740"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il numero di elementi nella matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```csharp  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwNumElements`  
 [out] Restituisce il numero di elementi nella matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il valore restituito è il numero totale di elementi nella matrice, indipendentemente dal numero di dimensioni.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
