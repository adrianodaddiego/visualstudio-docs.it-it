---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 829c7a0193ce2742959f677e95dd4a499997cf5b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964312"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Restituisce tutti i valori di tag puntatore tasti di scelta rapida che corrispondono a una funzione di stub di tasti di scelta rapida AMP C++.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cnt`  
 [in] Le dimensioni della matrice di output `pPointerTags`.  
  
 `pcnt`  
 [out] Il conteggio dei tag di puntatore tasti di scelta rapida nella funzione di stub di tasti di scelta rapida AMP C++.  
  
 `pPointerTags`  
 [out] Oggetto `DWORD` puntatore di una matrice che viene riempito con i valori di tag acceleratore puntatore della funzione di stub di tasti di scelta rapida AMP C++.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato su un `IDiaSymbol` interfaccia che corrisponde a una funzione di stub di tasti di scelta rapida AMP C++.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
