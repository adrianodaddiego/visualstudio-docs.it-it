---
title: IDiaSession::findLinesByAddr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByAddr method
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4658075c61a06c3616a4d9a42e9d3e37c0166e98
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964954"
---
# <a name="idiasessionfindlinesbyaddr"></a>IDiaSession::findLinesByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera le righe che contengono un indirizzo specificato in un modulo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findLinesByAddr (   
   DWORD                 seg,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `seg`  
 [in] Specifica il componente di sezione dell'indirizzo specifico.  
  
 `offset`  
 [in] Specifica il componente di offset di indirizzo specifico.  
  
 `length`  
 [in] Specifica il numero di byte dell'intervallo di indirizzi per coprire la query viene usata.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) oggetto che contiene un elenco di tutto la riga di numeri che coprono l'intervallo di indirizzi specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrata una funzione che ottiene tutti i numeri di riga inclusi in una funzione usando l'indirizzo e la lunghezza della funzione.  
  
```cpp#  
IDiaEnumLineNumbers* GetLineNumbersByAddr(IDiaSymbol *pFunc,  
                                          IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                seg;  
    DWORD                offset;  
    ULONGLONG            length;  
  
    if (pFunc->get_addressSection ( &seg ) == S_OK &&  
        pFunc->get_addressOffset ( &offset ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByAddr( seg, offset, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)
