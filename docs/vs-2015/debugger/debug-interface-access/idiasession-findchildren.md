---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964535"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera tutti gli elementi figlio di un identificatore di oggetto padre specificato che corrispondono al tipo di nome e il simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `parent`  
 [in] Un' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta l'elemento padre. Se questo simbolo padre è una funzione, un modulo o un blocco, quindi vengono restituiti i figli lessicali in `ppResult`. Se il simbolo padre è un tipo, vengono restituiti i figli di classe. Se questo parametro è `NULL`, quindi `symtag` deve essere impostata su `SymTagExe` o `SymTagNull`, che restituisce l'ambito globale (file .exe).  
  
 `symtag`  
 [in] Specifica il tag di simboli degli elementi figlio da recuperare. I valori sono ricavati dal [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumerazione. Impostare su `SymTagNull` per recuperare tutti gli elementi figlio.  
  
 `name`  
 [in] Specifica il nome degli elementi figlio da recuperare. Impostare su `NULL` per tutti gli elementi figlio da recuperare.  
  
 `compareFlags`  
 [in] Specifica le opzioni di confronto applicate alla corrispondenza dei nomi. I valori di [enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumerazione può essere utilizzata singolarmente o in combinazione.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recuperare l'oggetto che contiene l'elenco dei simboli figlio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come trovare le variabili locali della funzione `pFunc` tale nome corrispondenza `szVarName`.  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
