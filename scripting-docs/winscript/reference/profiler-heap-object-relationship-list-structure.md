---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST Structure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 46ca87ea-5b0f-437d-a33f-b2d9a457e036
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23c6ee5f8ff4d7a8a19c19bae55bb72eb5c8fd06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823879"
---
# <a name="profilerheapobjectrelationshiplist-structure"></a>Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST
Rappresenta un elenco di relazioni che appartengono a un oggetto heap.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_RELATIONSHIP elements[];} PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Tipo|Descrizione|  
|------------|----------|-----------------|  
|count|UINT|Il numero di relazioni di un oggetto heap.|  
|elementi|[Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Le relazioni di un oggetto heap.|