---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63e4f1a3621dde3fba5e8a2dabf45eaceb5d8ea4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418052"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

DEPRECATO. NON USARE.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrHostMachineName`  
 [out] Restituisce il nome del computer in cui viene eseguito il programma.  
  
## <a name="return-value"></a>Valore restituito  
 Un'implementazione deve sempre restituire `E_NOTIMPL`.  
  
## <a name="remarks"></a>Note  
  
> [!WARNING]
> A partire [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
