---
title: IDiaSymbol::get_dataBytes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb0946c586c7b9ac3bb8907a9b5eb907d8f3ae70
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430602"
---
# <a name="idiasymbolgetdatabytes"></a>IDiaSymbol::get_dataBytes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera i byte di dati di un simbolo OEM.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_dataBytes (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cbData`  
 [in] Dimensione del buffer per contenere i dati.  
  
 `pcbData`  
 [out] Restituisce il numero di byte scritti, oppure, se il `data` parametro è `NULL`, restituisce il numero di byte disponibili.  
  
 `data[]`  
 [out], Un buffer che viene compilato con i byte di dati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
> Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Version:|DIA SDK v7.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
