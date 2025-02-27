---
title: IDispatchEx::GetNextDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d964a8744f1f0a28704dd0a1d5e0fd2e67aab1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997349"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Enumera i membri dell'oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>Parametri

`grfdex`\
Determina quale set di elementi da enumerare. Può trattarsi di una combinazione dei valori seguenti:

|Value|Significato|
|-----------|-------------|
|fdexEnumDefault|Richieste che l'oggetto enumera gli elementi predefiniti. L'oggetto è consentita l'enumerazione qualsiasi set di elementi.|
|fdexEnumAll|Richieste che l'oggetto enumera tutti gli elementi. L'oggetto è consentita l'enumerazione qualsiasi set di elementi.|

`id`\
Identifica il membro corrente. GetNextDispID recupera l'elemento dell'enumerazione dopo questo. Utilizza GetDispID o una chiamata precedente a GetNextDispID per ottenere questo identificatore. Usa il valore DISPID_STARTENUM per ottenere il primo identificatore del primo elemento.

`pid`\
Indirizzo di una variabile DISPID che riceve l'identificatore dell'elemento successivo nell'enumerazione.

Se un membro viene eliminato dal `DeleteMemberByName` oppure `DeleteMemberByDispID`, il `DISPID` deve rimanere valido per `GetNextDispID`.

## <a name="return-value"></a>Valore restituito

Restituisce uno dei valori seguenti:

|||
|-|-|
|`S_OK`|Operazione completata.|
|`S_FALSE`|Enumerazione viene eseguita.|

## <a name="example"></a>Esempio

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>Vedere anche

- [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)