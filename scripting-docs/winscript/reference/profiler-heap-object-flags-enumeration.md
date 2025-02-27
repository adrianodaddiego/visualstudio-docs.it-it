---
title: Enumerazione PROFILER_HEAP_OBJECT_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7fde5ed275691d78e534cd7b8d8e958a8f20325
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823837"
---
# <a name="profilerheapobjectflags-enumeration"></a>Enumerazione PROFILER_HEAP_OBJECT_FLAGS
Flag che rappresentano informazioni di base sull'oggetto heap. Utilizzato nel [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,} PROFILER_HEAP_OBJECT_FLAGS;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Value|Descrizione|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT|0x00000001|Questo oggetto heap è stato allocato dopo la precedente richiesta di enumerazione dell'heap. [Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md) valori possono essere riutilizzati se l'oggetto viene raccolto.|  
|PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT|0x00000002|Questo oggetto heap è un oggetto radice dell'oggetto grafico.|  
|PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED|0x00000004|Questo oggetto heap proviene da un sito di uno script che è stata chiusa.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL|0x00000008|Questo oggetto heap è stato allocato all'heap di garbage collection JavaScript esterno.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN|0x00000010|Questo oggetto heap è stato allocato all'esterno dell'heap di garbage collection e implementa IUnknown.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH|0x00000020|Questo oggetto heap è stato allocato all'esterno dell'heap di garbage collection e implementa l'interfaccia IDISPATCH.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE|0x00000040|Le dimensioni di questo oggetto heap sono approssimative.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE|x00000080|Le dimensioni di questo oggetto heap non sono disponibile.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE|0x00000200|L'oggetto heap è un'istanza di Windows Runtime.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS|0x00000400|L'oggetto heap è una classe di runtime di Windows Runtime.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE|0x00000800|L'oggetto heap è un delegato di Windows Runtime.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE|0x00001000|L'oggetto heap è nello spazio dei nomi di Windows Runtime.|