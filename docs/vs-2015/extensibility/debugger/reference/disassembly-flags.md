---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d48fcf9dd941194b56e2c794ad7f5673f8e58421
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966743"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica i flag per il disassembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Membri  
 DF_DOCUMENTCHANGE  
 Indica che questa istruzione è in un documento diverso da quello precedente.  
  
 DF_DISABLED  
 Indica che questa istruzione non verrà eseguita.  
  
 DF_INSTRUCTION_ACTIVE  
 Indica che questa istruzione è una delle istruzioni successive da eseguire (potrebbero essere presenti più di uno).  
  
 DF_DATA  
 Indica che questa istruzione è davvero data (non nel codice).  
  
 DF_HASSOURCE  
 Indica che questa istruzione ha origine. Alcune istruzioni, ad esempio il codice di raccolta profilatura o garbage, non dispone di alcuna origine corrispondente.  
  
 DF_DOCUMENT_CHECKSUM  
 Indica che `bstrDocumentUrl` campo contiene dati di checksum dopo l'URL del documento. Vedere la sezione Osservazioni per il [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struttura per la modalità in cui sono archiviati i dati di checksum.  
  
## <a name="remarks"></a>Note  
 Utilizzato come il `dwFlags` membro della [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struttura.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
