---
title: Comando Elenca memoria | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 884dda624d5405ec017b544afd223be0bebc97e9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655868"
---
# <a name="list-memory-command"></a>Comando Elenca memoria
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visualizza il contenuto dell'intervallo di memoria specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## <a name="arguments"></a>Argomenti  
 `expression`  
 Facoltativo. L'indirizzo di memoria da cui iniziare la visualizzazione della memoria.  
  
## <a name="switches"></a>Opzioni  
 /ANSI&#124;Unicode  
 Facoltativo. Visualizza la memoria come caratteri corrispondenti ai byte di memoria, ANSI o Unicode.  
  
 /Count:`number`  
 Facoltativo. Determina il numero di byte di memoria da visualizzare, a partire da `expression`.  
  
 /Format:`formattype`  
 Facoltativo. Tipo di formato per la visualizzazione di informazioni sulla memoria nella finestra **Memoria**; può essere OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bit) o Double (64 bit). Se viene usato il formato OneByte, `/Unicode` non è disponibile.  
  
 /Hex&#124;Signed&#124;Unsigned  
 Facoltativo. Specifica il formato per la visualizzazione dei numeri: con segno, senza segno o esadecimale.  
  
## <a name="remarks"></a>Osservazioni  
 Invece di scrivere un comando **Debug.ListMemory** completo con tutte le opzioni, è possibile richiamare il comando tramite alias predefiniti con alcune opzioni preimpostate su valori specificati. Ad esempio, anziché immettere:  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 è possibile scrivere:  
  
```  
>df /Count:30 /Unicode  
```  
  
 Di seguito viene riportato un elenco degli alias disponibili per il comando **Debug.ListMemory**:  
  
|Alias|Comandi e opzioni|  
|-----------|--------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory /Ansi|  
|**db**|Debug.ListMemory /Format:OneByte|  
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|  
|**dd**|Debug.ListMemory /Format:FourBytes|  
|**df**|Debug.ListMemory /Format:Float|  
|**dq**|Debug.ListMemory /Format:EightBytes|  
|**du**|Debug.ListMemory /Unicode|  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)   
 [Comando Elenca thread](../../ide/reference/list-threads-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
