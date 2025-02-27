---
title: Just-In-Time, debug, finestra di dialogo Opzioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23a285cf0ce017130a5fe76171c50082362e4856
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905935"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>JIT, Debug, Finestra di dialogo Opzioni
Per accedere alla pagina **JIT** scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere il nodo **Debug** e selezionare **JIT**. Questa pagina consente di abilitare il debug JIT per codice gestito, codice nativo e script. Per altre informazioni, vedere [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md).

 È possibile abilitare il debug JIT per questi tipi di programma:

- Gestito

- Nativo

- Script

  Il debug JIT è una tecnica per il debug di un programma avviato al di fuori di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È possibile eseguire un programma creato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] al di fuori dell'ambiente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se il debug JIT è abilitato e si verifica un arresto anomalo, viene visualizzata una finestra di dialogo in cui viene chiesto se si desidera eseguire il debug.

## <a name="associated-warnings"></a>Avvisi associati
 Quando si accede a questa pagina della finestra di dialogo **Opzioni**, è possibile che venga visualizzato il seguente messaggio di avviso:

 **Un altro debugger è stato registrato come debugger JIT. Per risolvere il problema, abilitare il debug JIT o ripristinare Visual Studio.**

 Questo messaggio viene visualizzato se come debugger JIT è impostato un altro debugger, ad esempio una versione precedente del debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 È anche possibile che venga visualizzato il messaggio seguente:

 **Rilevati errori di registrazione del debug JIT. Per risolvere il problema, abilitare il debug JIT o ripristinare Visual Studio.**

 In entrambi i casi, finché il problema non viene risolto, per l'esecuzione del debug JIT con [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] sarà necessario disporre dei privilegi di amministratore. Se si tenta di abilitare la modalità JIT in queste condizioni senza disporre di questi privilegi, viene visualizzato il seguente messaggio di errore:

 **Accesso negato. Chiedere a un amministratore di abilitare il debug JIT o ripristinare l'installazione di Visual Studio.**

## <a name="see-also"></a>Vedere anche
- [Debug, finestra di dialogo Opzioni](../debugger/debugging-options-dialog-box.md)
- [Procedura: Specificare le impostazioni del debugger](../debugger/how-to-specify-debugger-settings.md)