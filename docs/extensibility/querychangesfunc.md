---
title: QUERYCHANGESFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ac0003d26296a25659debbab3352e4e37cbf2ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334401"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Si tratta di una funzione di callback utilizzata per la [SccQueryChanges](../extensibility/sccquerychanges-function.md) operazione per enumerare una raccolta di nomi di file e determinare lo stato di ogni file.

 Il `SccQueryChanges` ha un elenco di file e un puntatore a funzione di `QUERYCHANGESFUNC` callback. Il plug-in del controllo del codice sorgente enumera l'elenco specificato e fornisce lo stato (tramite questo callback) per ogni file nell'elenco.

## <a name="signature"></a>Signature

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametri
 pvCallerData

[in] Il `pvCallerData` parametro passato dal chiamante (IDE) per [SccQueryChanges](../extensibility/sccquerychanges-function.md). Il plug-in del controllo del codice sorgente consigliabile non fare supposizioni sul contenuto di questo valore.

 pChangesData

[in] Puntatore a un [QUERYCHANGESDATA struttura](#LinkQUERYCHANGESDATA) struttura che descrive le modifiche in un file.

## <a name="return-value"></a>Valore restituito
 Nell'IDE viene restituito un codice di errore appropriato:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Continuare l'elaborazione.|
|SCC_I_OPERATIONCANCELED|Arrestare l'elaborazione.|
|SCC_E_xxx|Qualsiasi errore di controllo del codice sorgente appropriato deve arrestare l'elaborazione.|

## <a name="LinkQUERYCHANGESDATA"></a> Struttura QUERYCHANGESDATA
 La struttura passata per ogni file è simile al seguente:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 dwSize dimensione di questa struttura (in byte).

 lpFileName il nome file originale per questo elemento.

 dwChangeType del codice che indica lo stato del file:

|Codice|Descrizione|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Non può stabilire cosa è cambiato.|
|`SCC_CHANGE_UNCHANGED`|Nessuna modifica di nome per questo file.|
|`SCC_CHANGE_DIFFERENT`|File con un'identità diversa, ma lo stesso nome esiste nel database.|
|`SCC_CHANGE_NONEXISTENT`|File non esiste nel database o in locale.|
|`SCC_CHANGE_DATABASE_DELETED`|File eliminati dal database.|
|`SCC_CHANGE_LOCAL_DELETED`|File eliminati localmente, ma il file esiste ancora nel database. Se ciò non può essere determinato, restituire `SCC_CHANGE_DATABASE_ADDED`.|
|`SCC_CHANGE_DATABASE_ADDED`|File aggiunti al database ma non esiste in locale.|
|`SCC_CHANGE_LOCAL_ADDED`|File non esiste nel database ed è un nuovo file locale.|
|`SCC_CHANGE_RENAMED_TO`|File rinominati o spostati nel database come `lpLatestName`.|
|`SCC_CHANGE_RENAMED_FROM`|File rinominati o spostati nel database da `lpLatestName`; se questo è troppo costoso tenere traccia, restituiscono un flag diverso, ad esempio `SCC_CHANGE_DATABASE_ADDED`.|

 lpLatestName il nome di file corrente per questo elemento.

## <a name="see-also"></a>Vedere anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Codici di errore](../extensibility/error-codes.md)