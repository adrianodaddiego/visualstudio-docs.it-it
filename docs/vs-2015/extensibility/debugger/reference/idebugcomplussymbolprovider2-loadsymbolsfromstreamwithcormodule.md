---
title: IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
- LoadSymbolsFromStreamWithCorModule
ms.assetid: f79b894f-52c4-43c2-9a68-c71536451f6c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c47c8e2df88e25f7b0eaf2d8d82c343ccbd360c6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965389"
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromstreamwithcormodule"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Caricare i simboli di debug da un flusso di dati ha il **ICorDebugModule** oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT LoadSymbolsFromStreamWithCorModule(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IUnknown* pUnkCorDebugModule,  
   IStream*  pStream  
);  
```  
  
```csharp  
int LoadSymbolsFromStreamWithCorModule(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   ulong   baseAddress,  
   object  pUnkMetadataImport,  
   object  pUnkCorDebugModule,  
   IStream pStream  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ulAppDomainID`  
 [in] Identificatore del dominio dell'applicazione.  
  
 `guidModule`  
 [in] Identificatore univoco del modulo.  
  
 `baseAddress`  
 [in] Indirizzo di base di memoria.  
  
 `pUnkMetadataImport`  
 [in] Oggetto che contiene i metadati del simbolo.  
  
 `pUnkCorDebugModule`  
 [in] Oggetto che implementa il [ICorDebugModule (interfaccia)](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface).  
  
 `pStream`  
 [in] Flusso di dati che contiene i simboli di debug da caricare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfaccia.  
  
```cpp#  
HRESULT CDebugSymbolProvider::LoadSymbolsFromStreamWithCorModule(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* pUnkMetadataImport,  
    IUnknown* pUnkCorDebugModule,  
    IStream* pStream  
)  
{  
    CAutoLock Lock(this);  
  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<ICorDebugModule> pCorModule;  
  
    CModule* pmodule = NULL;  
    CModule* pmoduleNew = NULL;  
    bool fAlreadyLoaded = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    DWORD dwCurrentState = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pUnkMetadataImport, IUnknown));  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbolsFromStream );  
  
    IfFalseGo( pUnkMetadataImport, E_INVALIDARG );  
    IfFalseGo( pUnkCorDebugModule, E_INVALIDARG );  
  
    IfFailGo( pUnkMetadataImport->QueryInterface( IID_IMetaDataImport,  
              (void**)&pMetadata) );  
  
    IfFailGo( pUnkCorDebugModule->QueryInterface( IID_ICorDebugModule,  
              (void**)&pCorModule) );  
  
    ASSERT(guidModule != GUID_NULL);  
  
    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;  
  
    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );  
  
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;  
  
    IfFailGo( pmoduleNew->Create( idModule,  
                                  dwCurrentState,  
                                  pMetadata,  
                                  pCorModule,  
                                  pStream,  
                                  baseOffset ) );  
  
    if (fAlreadyLoaded)  
    {  
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));  
        RemoveModule(pmodule);  
    }  
  
    IfFailGo( AddModule( pmoduleNew ) );  
  
Error:  
  
    RELEASE (pmodule);  
    RELEASE (pmoduleNew);  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbolsFromStream, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
