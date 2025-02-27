---
title: Costanti DEBUG_TEXT | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2342555c4ee92b403aa01cc0ca15bb805f2b002e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955250"
---
# <a name="debugtext-constants"></a>Costanti DEBUG_TEXT
Usato durante [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Costanti  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica che il testo è un'espressione anziché un'istruzione. Questo flag può influenzare le modalità in cui il testo viene analizzato per alcune lingue.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se un valore restituito è disponibile, si verrà utilizzato dal chiamante.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Non consente effetti collaterali. Se questo flag è impostato, la valutazione dell'espressione dovrebbe modificare nessuno stato di runtime.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Consenti i punti di interruzione durante la valutazione del testo. Se questo flag non è impostato, i punti di interruzione verrà ignorati durante la valutazione del testo.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Consenti segnalazioni degli errori durante la valutazione del testo. Se questo flag non è impostato, quindi gli errori non verranno segnalati nell'host durante la valutazione.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica che l'espressione da valutare per un contesto di codice piuttosto che in esecuzione l'espressione stessa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)