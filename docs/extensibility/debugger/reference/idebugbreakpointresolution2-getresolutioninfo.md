---
title: IDebugBreakpointResolution2::GetResolutionInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2::GetResolutionInfo
helpviewer_keywords:
- IDebugBreakpointResolution2::GetResolutionInfo
ms.assetid: 828cbdf6-b87d-4c45-be87-d87087b04a60
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e5b847590a066f10580eeaaa3d600089b70a2e0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352854"
---
# <a name="idebugbreakpointresolution2getresolutioninfo"></a>IDebugBreakpointResolution2::GetResolutionInfo
Ottiene le informazioni di risoluzione dei punti di interruzione che descrive il punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetResolutionInfo( 
   BPRESI_FIELDS       dwFields,
   BP_RESOLUTION_INFO* pBPResolutionInfo
);
```

```csharp
int GetResolutionInfo( 
   enum BPRESI_FIELDS   dwFields,
   BP_RESOLUTION_INFO[] pBPResolutionInfo
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
[in] Una combinazione di flag dal [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) enumerazione che determinano quali campi del `pBPResolutionInfo` parametro devono essere compilati.

`pBPResolutionInfo`\
[out] Il [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struttura deve essere compilato con informazioni su questo punto di interruzione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="example"></a>Esempio
 L'esempio seguente implementa questo metodo per un semplice `CDebugBreakpointResolution` oggetto che espone il [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaccia.

```
HRESULT CDebugBreakpointResolution::GetResolutionInfo(
   BPRESI_FIELDS dwFields,
   BP_RESOLUTION_INFO* pBPResolutionInfo)
{
   HRESULT hr;

   if (pBPResolutionInfo)
   {
      // Copy the specified fields of the request information from the class
      // member variable to the local BP_RESOLUTION_INFO variable.
      hr = CopyBP_RESOLUTION_INFO(m_bpResolutionInfo,
                                  *pBPResolutionInfo,
                                  dwFields);
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}

HRESULT CDebugBreakpointResolution::CopyBP_RESOLUTION_INFO(
   BP_RESOLUTION_INFO& bpResSrc,
   BP_RESOLUTION_INFO& bpResDest,
   DWORD dwFields)
{
   HRESULT hr = S_OK;

   // Start with a raw copy.
   memcpy(&bpResDest, &bpResSrc, sizeof(BP_RESOLUTION_INFO));

   // The fields in the destination is the result of the AND of
   //  bpInfoSrc.dwFields and dwFields.
   bpResDest.dwFields = dwFields & bpResSrc.dwFields;

   // Fill in the bp location information if the BPRESI_BPRESLOCATION
   //  flag is set in BPRESI_FIELDS.
   if (IsFlagSet(bpResDest.dwFields, BPRESI_BPRESLOCATION))
   {
      // Switch based on the BP_TYPE.
      switch (bpResSrc.bpResLocation.bpType)
      {
         case BPT_CODE:
         {
            // AddRef the IDebugCodeContext2 of the BP_RESOLUTION_CODE structure.
            bpResDest.bpResLocation.bpResLocation.bpresCode.pCodeContext->AddRef();
            break;
         }
         case BPT_DATA:
         {
            // Copy the bstrDataExpr, bstrFunc, and bstrImage of the
            // BP_RESOLUTION_DATA structure.
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrDataExpr =
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrDataExpr);
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrFunc =
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrFunc);
            bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage =
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage);
            break;
         }
         default:
         {
            assert(FALSE);
            // Clear the BPRESI_BPRESLOCATION flag in the BPRESI_FIELDS
            // of the destination BP_RESOLUTION_INFO.
            ClearFlag(bpResDest.dwFields, BPRESI_BPRESLOCATION);
            break;
         }
      }
   }
   // AddRef the IDebugProgram2 if the BPRESI_PROGRAM flag is set in BPRESI_FIELDS.
   if (IsFlagSet(bpResDest.dwFields, BPRESI_PROGRAM))
   {
      bpResDest.pProgram->AddRef();
   }
   // AddRef the IDebugThread2 if the BPRESI_THREAD flag is set in BPRESI_FIELDS.
   if (IsFlagSet(bpResDest.dwFields, BPRESI_THREAD))
   {
      bpResDest.pThread->AddRef();
   }

   return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)