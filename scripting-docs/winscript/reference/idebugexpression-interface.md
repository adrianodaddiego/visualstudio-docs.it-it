---
title: Interfaccia IDebugExpression | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1757317e9ab148b508bfed95107b5c3b3369b598
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430019"
---
# <a name="idebugexpression-interface"></a>Interfaccia IDebugExpression
Rappresenta un'espressione valutata in modo asincrono. Motori di script in genere implementano questa interfaccia. Un IDE debugger Usa in genere questa interfaccia per abilitare una finestra di esecuzione immediata o finestra Espressioni di controllo.  
  
> [!NOTE]
> Il `IDebugExpression` interfaccia è disponibile solo da uno stack frame.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugExpression` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Inizia la valutazione dell'espressione.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Interrompe l'espressione.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Determina se l'operazione è stata completata.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Restituisce il risultato della valutazione dell'espressione come stringa e il valore restituito dell'operazione.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Restituisce il risultato della valutazione dell'espressione come una proprietà di debug e il valore restituito dell'operazione.|