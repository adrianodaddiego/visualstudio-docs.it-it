---
title: IDiaEnumDebugStreams::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Item method
ms.assetid: 6b388fe1-eabc-4720-9d59-dc09b0ceaeac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f07ecb151b6bf2cd4a9d48fbe6596bc7a533f97a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838259"
---
# <a name="idiaenumdebugstreamsitem"></a>IDiaEnumDebugStreams::Item
Recupera un flusso di debug tramite un indice o nome.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item (
    VARIANT                   index,
    IDiaEnumDebugStreamData** stream
);
```

#### <a name="parameters"></a>Parametri
indice

[in] Indice o nome del flusso di debug da recuperare. Se si usa una variante dell'integer, deve essere compreso nell'intervallo da 0 a `count`-1, dove `count` viene restituito dalle [Idiaenumdebugstreams](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md) (metodo).

flusso

[out] Restituisce un [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) oggetto che rappresenta il flusso di debug specificato.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="example"></a>Esempio

```C++
IDiaEnumDebugStreamData *GetStreamData(IDiaEnumDebugStreams *pStreamList,
                                       LONG whichStream)
{
    IDiaEnumDebugStreamData *pStreamData = NULL;
    if (pStreamList != NULL)
    {
        LONG numStreams = 0;
        if (pStreamList->get_count(&numStreams) == S_OK &&
            whichStream >= 0 && whichStream < numStreams)
        {
            VARIANT vIndex;
            vIndex.vt   = VT_I4;
            vIndex.lVal = whichStream;
            if (pStreamList->Item(vIndex,&pStreamData) != S_OK)
            {
                std::cerr << "Error retrieving stream " << whichStream << std::endl;
            }
        }
    }
    return(pStreamData);
}
```

## <a name="see-also"></a>Vedere anche
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
