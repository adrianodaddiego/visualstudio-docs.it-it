---
title: IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetAddressesInModuleFromPosition
- IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
ms.assetid: f901c66e-f53c-4ea0-8004-d8fcbf46f916
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471997a5497413869c3c4662592f4c585c2d76d
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "59000903"
---
# <a name="idebugcomplussymbolprovidergetaddressesinmodulefromposition"></a>IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esegue il mapping di una posizione del documento nel modulo specificato in una matrice di indirizzi di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[C++]  
HRESULT GetAddressesInModuleFromPosition(  
   ULONG32                  ulAppDomainID,  
   GUID                     guidModule,  
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```  
[C#]  
int GetAddressesInModuleFromPosition(  
   uint                    ulAppDomainID,  
   Guid                    guidModule,  
   IDebugDocumentPosition2 pDocPos,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ulAppDomainID`  
 [in] Identificatore del dominio applicazione.  
  
 `guidModule`  
 [in] Identificatore univoco del modulo.  
  
 `pDocPos`  
 [in] Posizione del documento.  
  
 `fStatmentOnly`  
 [in] Se `TRUE`, limita gli indirizzi di debug per una singola istruzione.  
  
 `ppEnumBegAddresses`  
 [out] Restituisce un enumeratore per gli indirizzi iniziali di debug che sono associati a questa istruzione o la riga.  
  
 `ppEnumEndAddresses`  
 [out] Restituisce un enumeratore per gli indirizzi finale di debug che sono associati a questa istruzione o la riga.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPosition(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IDebugDocumentPosition2* pDocPos,  
    BOOL fStatementOnly,  
    IEnumDebugAddresses** ppEnumBegAddresses,  
    IEnumDebugAddresses** ppEnumEndAddresses  
)  
{  
    GUID guidNULL = {0};  
  
    if (guidNULL == guidModule)  
    {  
        return GetAddressesInAppDomainFromPosition( ulAppDomainID,  
                pDocPos,  
                fStatementOnly,  
                ppEnumBegAddresses,  
                ppEnumEndAddresses );  
    }  
    else  
    {  
        return GetAddressesInModuleFromPositionHelper( ulAppDomainID,  
                guidModule,  
                pDocPos,  
                fStatementOnly,  
                ppEnumBegAddresses,  
                ppEnumEndAddresses );  
    }  
}  
  
HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IDebugDocumentPosition2* pDocPos,  
    BOOL fStatementOnly,  
    IEnumDebugAddresses** ppEnumBegAddresses,  
    IEnumDebugAddresses** ppEnumEndAddresses  
)  
{  
    HRESULT hr = S_OK;  
    CComBSTR bstrFileName;  
    TEXT_POSITION posBeg;  
    TEXT_POSITION posEnd;  
    DWORD dwLine;  
    USHORT segRet = 0;  
    ULONG offRet = 0;  
    CAddrList listAddr;  
    CAddrList listAddrEnd;  
    CAddrList* plistAddrEnd = NULL;  
    bool fFileFound = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    DWORD dwListCount;  
    bool fFoundAddresses = false;  
    CComPtr<CModule> pmodule;  
    DWORD dwBegCol = 0;  
    DWORD dwEndCol = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pDocPos, IDebugDocumentPosition2));  
    ASSERT(IsValidWritePtr(ppEnumBegAddresses, IEnumDebugAddresses*));  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper);  
  
    // Bail on Invalid Args  
  
    IfFalseGo( pDocPos && ppEnumBegAddresses, E_INVALIDARG );  
  
    *ppEnumBegAddresses = NULL;  
    if (ppEnumEndAddresses)  
    {  
        *ppEnumEndAddresses = NULL;  
        plistAddrEnd = &listAddrEnd;  
    }  
  
    // Get the Position  
  
    IfFailGo( pDocPos->GetFileName(&bstrFileName) );  
    IfFailGo( pDocPos->GetRange(&posBeg, &posEnd) );  
  
    // Iterate over the module list accumulating addresses  
    // that match the position  
  
    dwLine = posBeg.dwLine;  
    IfFailGo( GetModule( idModule, &pmodule ) );  
    dwListCount = listAddr.GetCount();  
  
    if ( fStatementOnly )  
    {  
        dwBegCol = posBeg.dwColumn;  
        dwEndCol = posBeg.dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);  
    }  
    else  
    {  
        dwBegCol = 0;  
        dwEndCol = DWORD( -1);  
    }  
  
    while (!fFoundAddresses && dwLine <= posEnd.dwLine )  
    {  
        hr = pmodule->GetAddressesFromLine( bstrFileName,  
                                            dwLine,  
                                            posEnd.dwLine,  
                                            dwBegCol,  
                                            dwEndCol,  
                                            &listAddr,  
                                            plistAddrEnd );  
  
        dwLine++;  
        dwBegCol = 0;  
        dwEndCol = dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);  
  
        if (hr == E_SH_INVALID_POSITION)  
        {  
            fFileFound = true;  
            break;  
        }  
  
        if (FAILED(hr))  
        {  
            // Move on to the next module  
            break;  
        }  
  
        fFileFound = true;  
        fFoundAddresses = listAddr.GetCount() != dwListCount;  
    }  
  
    // Distinguish no file from bad position in the file  
    IfFalseGo( fFileFound, E_SH_FILE_NOT_FOUND);  
  
    // If the list is empty the position is bad  
    IfFalseGo( listAddr.GetCount(), E_SH_INVALID_POSITION );  
  
    // Create enumerators  
    IfFailGo( CreateEnumerator( ppEnumBegAddresses, &listAddr ) );  
    if (ppEnumEndAddresses)  
    {  
        IfFailGo( CreateEnumerator( ppEnumEndAddresses, &listAddrEnd ) );  
    }  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper, hr);  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
