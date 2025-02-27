---
title: Enumerazione profiler_info_object_flags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0aa0a94668d06f75b959de2ee933ab079feba596
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808893"
---
# <a name="profilerrelationshipinfo-enumeration"></a>Enumerazione PROFILER_INFO_OBJECT_FLAGS
Rappresenta le informazioni sull'oggetto nella relazione. Usato nel [struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Value|Descrizione|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|L'oggetto è un numero.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|L'oggetto è una stringa.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|L'oggetto è un oggetto heap.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|L'oggetto esterno, vale a dire, non è nell'heap di garbage collection.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|L'oggetto è un oggetto BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|L'oggetto è una SOTTOSTRINGA.|