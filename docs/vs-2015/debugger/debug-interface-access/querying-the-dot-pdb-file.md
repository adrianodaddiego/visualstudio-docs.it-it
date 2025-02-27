---
title: L'esecuzione di query di. Il File PDB | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b9013d41ac4d5ca890e7cc9e09b5eb9415cb640
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691335"
---
# <a name="querying-the-pdb-file"></a>Ricerche nel file PDB
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un file di database di programma (con estensione pdb) è un file binario che contiene informazioni sul debug simbolici raccolti nel corso della compilazione e collegamento del progetto e tipo. Viene creato un file PDB quando si compila un programma C/C++ con **/ZI** o **/Zi** o un [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], oppure [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] programmare con il **/debug** opzione. File oggetto contengono riferimenti nel file con estensione PDB per le informazioni di debug. Per altre informazioni sui file pdb, vedere [file con estensione PDB](https://msdn.microsoft.com/1761c84e-8c2c-4632-9649-b5f99964ed3f). Un'applicazione di DIA può utilizzare i passaggi generali seguenti per ottenere ulteriori dettagli su varie simboli, oggetti e gli elementi di dati all'interno di un'immagine eseguibile.  
  
### <a name="to-query-the-pdb-file"></a>Per eseguire query sul file con estensione pdb  
  
1. Acquisire un'origine dati mediante la creazione di un' [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) interfaccia.  
  
    ```cpp#  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2. Chiamare [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) oppure [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) per caricare le informazioni di debug.  
  
    ```cpp#  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3. Chiamare [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md) per aprire un' [IDiaSession](../../debugger/debug-interface-access/idiasession.md) per ottenere l'accesso alle informazioni di debug.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4. Usare i metodi in `IDiaSession` per eseguire query per i simboli nell'origine dati.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5. Usare il `IDiaEnum*` interfacce di enumerare e analizzare i simboli o altri elementi di informazioni di debug.  
  
    ```cpp#  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
