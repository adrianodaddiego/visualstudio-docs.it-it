---
title: IDiaDataSource::loadDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb34098f8d69d3c8618c406eff9666d52eace1f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554144"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Viene aperto e lo prepara un file di database (con estensione pdb) del programma come un'origine dati di debug.

## <a name="syntax"></a>Sintassi

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parametri
pdbPath

[in] Il percorso del file con estensione pdb.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra i valori restituiti possibili per questo metodo.

|Value|Descrizione|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Non è stato possibile aprire il file o determinato che il file di formato non è valido.|
|E_PDB_FORMAT|È stato effettuato un tentativo di accedere a un file con formato obsoleto.|
|E_INVALIDARG|Parametro non valido.|
|E_UNEXPECTED|Origine dati è già stata preparata.|

## <a name="remarks"></a>Note
Questo metodo carica i dati di debug direttamente da un file con estensione pdb.

Per convalidare il file con estensione PDB in base ai criteri specifici, usare il [Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) (metodo).

Per ottenere l'accesso per il processo di caricamento dei dati (tramite un meccanismo di callback), usare il [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (metodo).

Per caricare un file con estensione pdb direttamente dalla memoria, usare il [Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) (metodo).

## <a name="example"></a>Esempio

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Vedere anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
