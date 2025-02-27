---
title: Comando Go To | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 010d2c395d77be590b3d8d3bc26fc83aaa63adfa
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660606"
---
# <a name="go-to-command"></a>Comando Vai a
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sposta il cursore sulla riga specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Argomenti  
 `linenumber`  
 Facoltativo. Valore integer che rappresenta il numero della riga a cui passare.  
  
## <a name="remarks"></a>Osservazioni  
 La numerazione delle righe inizia da uno. Se il valore di `linenumber` è minore di uno, viene visualizzata la prima riga. Se il valore di `linenumber` è maggiore del numero dell'ultima riga, viene visualizzata l'ultima riga.  
  
 Se non viene specificato alcun un valore per `linenumber`, viene visualizzata la finestra di dialogo **Vai alla riga**.  
  
 L'alias per questo comando è GoToLn.  
  
## <a name="example"></a>Esempio  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
