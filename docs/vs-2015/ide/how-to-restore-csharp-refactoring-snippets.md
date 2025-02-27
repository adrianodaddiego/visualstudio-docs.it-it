---
title: 'Procedura: Ripristinare il refactoring di frammenti C# | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9f81514db881ad26a5fa827b0bde11df2467f23d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050812"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Procedura: ripristinare refactoring di frammenti C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le operazioni di refactoring di C# si basano sui frammenti di codice disponibili nella directory seguente:  
  
 *Directory di installazione*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID linguaggio*\Refactoring  
  
 Se la directory Refactoring o i file in questa directory vengono eliminati o danneggiati, le operazioni di refactoring di C# potrebbero non funzionare nell'IDE. Le procedure seguenti consentono di ripristinare i frammenti di codice per il refactoring di C#.   
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Per verificare la disponibilità di frammenti di codice per il refactoring di C# tramite Gestione frammenti di codice  
  
1. Scegliere **Gestione frammenti di codice** dal menu **Strumenti**.  
  
2. Nella finestra di dialogo **Gestione frammenti di codice** selezionare **Visual C#** nell'elenco a discesa **Linguaggio**.  
  
     Nell'elenco di cartelle della visualizzazione albero dovrebbe essere visualizzata una cartella **Refactoring**.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Per ripristinare il refactoring vedere il commento in Gestione frammenti di codice  
  
1. Se la cartella **Refactoring** non viene visualizzata nell'elenco di cartelle della visualizzazione albero di Gestione frammenti di codice, seguire questa procedura per aggiungere di nuovo i frammenti per il refactoring in Gestione frammenti di codice.  
  
2. Scegliere **Gestione frammenti di codice** dal menu **Strumenti**.  
  
3. Nella finestra di dialogo **Gestione frammenti di codice** selezionare **Visual C#** nell'elenco a discesa **Linguaggio**.  
  
4. Fare clic su **Aggiungi**. Viene visualizzata la finestra di dialogo **Directory dei frammenti di codice**, che consente di individuare e specificare la directory da aggiungere nuovamente a Gestione frammenti di codice.  
  
5. Individuare la cartella **Refactoring**, il cui percorso di directory è:  
  
     *Directory di installazione*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID linguaggio*\Refactoring  
  
     Per un'installazione predefinita, il percorso effettivo è simile al seguente:  
  
     C:\Programmi\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring.  
  
6. Fare clic su **Apri** nella finestra di dialogo **Directory dei frammenti di codice** e quindi su **OK** in Gestione frammenti di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Frammenti di codice Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)   
 [Frammenti di codice](../ide/code-snippets.md)
