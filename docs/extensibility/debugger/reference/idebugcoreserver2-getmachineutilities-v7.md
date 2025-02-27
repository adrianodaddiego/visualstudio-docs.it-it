---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5aefe3b348f36b32792ebce9600f846d5a9cffe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317836"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Questo metodo ottiene le utilità di computer per un server.

> [!NOTE]
> Questo metodo è obsoleto: non usare ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato). Questa viene conservata per motivi cronologici.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parametri
`ppUtil`\
[out] Restituisce un `IDebugMDMUtil2_V7` interfaccia che rappresenta le informazioni di utilità macchina.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL`, che indica che il metodo non è implementato.

## <a name="remarks"></a>Note
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato.

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)