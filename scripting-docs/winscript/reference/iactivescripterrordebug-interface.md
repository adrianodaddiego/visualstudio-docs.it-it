---
title: Interfaccia IActiveScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 936770859d3bdfe81c84245d32ae63346b142a01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009532"
---
# <a name="iactivescripterrordebug-interface"></a>Interfaccia IActiveScriptErrorDebug
Fornisce informazioni sul contesto di documento per le eccezioni di runtime ed errori in fase di compilazione. Il `IActiveScriptError::QueryInterface` metodo supporta il `IActiveScriptErrorDebug` interfaccia.  
  
 Oltre ai metodi ereditati da `IActiveScriptError`, il `IActiveScriptErrorDebug` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Fornisce il contesto di documento per questo errore.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Fornisce lo stack frame che è attiva per gli errori di runtime.|