---
title: Costanti (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 931e1ab46793a5ff7e0434949330eaf4dbc820e8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968644"
---
# <a name="constants-debug-interface-access-sdk"></a>Costanti (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Queste costanti di stringa possono essere utilizzate per identificare diverse sezioni di un file di database (PDB) di debug programma tramite il DIA SDK.  
  
## <a name="constants"></a>Costanti  
 Di seguito viene dichiarati come macro C/C++.  
  
|Macro|Value|  
|-----------|-----------|  
|`DiaTable_Symbols`|L "Simboli"|  
|`DiaTable_Sections`|L "Sezioni"|  
|`DiaTable_SrcFiles`|L"SourceFiles"|  
|`DiaTable_LineNums`|L "LineNumbers"|  
|`DiaTable_SegMap`|L"SegmentMap"|  
|`DiaTable_Dbg`|L"Dbg"|  
|`DiaTable_InjSrc`|L"InjectedSource"|  
|`DiaTable_FrameData`|L"FrameData"|  
  
## <a name="example"></a>Esempio  
 Di seguito è riportato un esempio con uno di questi simboli:  
  
```cpp#  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dia2.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
