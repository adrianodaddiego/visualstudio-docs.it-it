---
title: Dialogo Risolvi ambiguità | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d784766e3c90241be3759a7113c52e6d863fa47
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902661"
---
# <a name="resolve-ambiguity-dialog-box"></a>finestra di dialogo Risolvi ambiguità
La finestra di dialogo `Resolve Ambiguity` viene visualizzata quando il debugger non è in grado di determinare il percorso da visualizzare. Se, ad esempio, si utilizzano i modelli C++, è possibile creare più funzioni da un unico modello di funzione. Se il debugger si arresta in corrispondenza di un percorso di origine nel modello e si sceglie `Go To Disassembly`, possono verificarsi più condizioni. Ciascuna funzione creata dal modello ha un proprio codice disassembly e il debugger non è in grado di determinare quale codice si desidera visualizzare. La finestra di dialogo `Resolve Ambiguity` consente di selezionare il percorso desiderato da un elenco di tutti i percorsi corrispondenti.

 `Choose the specific location` Elenca tutti i percorsi corrispondenti al comando.

 `Address` Mostra gli indirizzi di memoria per ogni funzione.

 `Function` Mostra il nome di ogni funzione.

 `Module` Mostra il modulo (EXE o DLL) che contiene il codice oggetto per la funzione.

## <a name="see-also"></a>Vedere anche
- [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md)