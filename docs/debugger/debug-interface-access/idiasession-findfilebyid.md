---
title: IDiaSession::findFileById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3454ff5ef087b67dda5d48849d4a6c4eceb7e52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839355"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Recupera un file di origine dall'identificatore di file di origine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `uniqueId`

[in] Specifica l'identificatore di file di origine.

 `ppResult`

[out] Restituisce un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) recuperare l'oggetto che rappresenta il file di origine.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'identificatore di file di origine è un valore univoco utilizzato internamente per il DIA SDK affinché tutti i file di origine univoco. Questo metodo viene in genere utilizzato internamente per il DIA SDK.

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)