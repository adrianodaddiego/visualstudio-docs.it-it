---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a42b67eb3fd308011bf725f8dd7e24a4d9ddca6f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311516"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Ottiene il nome utente dal fornitore della porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Parametri
`pbstrUserName`\
[out] Stringa contenente il nome utente.

## <a name="return-value"></a>Valore restituito
 Se il metodo ha esito positivo, restituisce `S_OK`. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 `GetUserName` Restituisce il nome utente visualizzato nei **nome utente** della colonna della **Connetti a processo** nella finestra di dialogo. Per visualizzare il **Connetti a processo** della finestra di dialogo fare clic su **Connetti a processo** sul **strumenti** dal menu il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE).

## <a name="see-also"></a>Vedere anche
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)