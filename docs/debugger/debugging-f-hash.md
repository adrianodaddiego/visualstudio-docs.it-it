---
title: Debug di F# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92f570aece9d68e2a4be20c3487137e085e33001
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851884"
---
# <a name="debugging-f"></a>Debug di F\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debug di F #è simile al debug di qualsiasi linguaggio gestito, con alcune eccezioni:

- Nella finestra **Auto** non vengono visualizzate le variabili F#.

- La modifica e la continuazione non sono supportate per F#. La modifica del codice F# durante una sessione di debug è possibile ma deve essere evitata. Poiché le modifiche al codice non vengono applicate durante la sessione di debug, la modifica del codice F# durante il debug provocherà una mancata corrispondenza tra il codice sorgente e il codice in fase di debug.

- Il debugger non riconosce le espressioni F#. Per immettere un'espressione in una finestra o una finestra di dialogo del debugger durante il debug di F#, è necessario tradurre l'espressione nella sintassi C#. Quando si traduce un'espressione F# in C#, ricordare che C# utilizza == come operatore di confronto per uguaglianza e che F# utilizza un solo =.

## <a name="see-also"></a>Vedere anche

- [Debug di codice gestito](../debugger/debugging-managed-code.md)
