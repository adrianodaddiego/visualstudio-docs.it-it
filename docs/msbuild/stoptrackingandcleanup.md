---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56f4fb82ab0e9792cadbeeea05499744e4c8ce46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939023"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Arresta tutte le operazioni di verifica e libera tutta la memoria usata dalla sessione di verifica.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Valore restituito
 Restituisce un **HRESULT** con il bit **SUCCEEDED** impostato se la verifica è stata sospesa.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedere anche
- [StartTrackingContext](../msbuild/starttrackingcontext.md)