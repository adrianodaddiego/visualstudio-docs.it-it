---
title: IDebugComPlusSymbolProvider::IsHiddenCode | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsHiddenCode
ms.assetid: 1352c6ab-7b92-4a16-b2d2-6520b628830e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecbd7aaa05b48efcf43bb299c9c3dc2be9c679ae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967844"
---
# <a name="idebugcomplussymbolproviderishiddencode"></a>IDebugComPlusSymbolProvider::IsHiddenCode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se il codice in corrispondenza dell'indirizzo di debugger specificato è nascosto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT IsHiddenCode(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int IsHiddenCode(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in] L'indirizzo di debug che è rappresentato da un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se il codice è nascosto, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.  
  
```cpp#  
HRESULT CDebugSymbolProvider::IsHiddenCode(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));  
  
    METHOD_ENTRY( CDebugSymbolProvider::IsHiddenCode );  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->IsHiddenCode( address.addr.addr.addrMethod.tokMethod,  
                                address.addr.addr.addrMethod.dwVersion,  
                                address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates this sequence point is not hidden  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::IsHiddenCode, hr );  
  
    if (!SUCCEEDED(hr))  
    {  
        hr = S_FALSE;  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
