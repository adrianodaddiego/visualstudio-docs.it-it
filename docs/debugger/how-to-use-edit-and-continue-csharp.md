---
title: 'Procedura: Utilizzare Modifica e continuazione (C#) | Microsoft Docs'
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 515068f29045ef92ee7d2323f752ba2185f28cac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906271"
---
# <a name="how-to-use-edit-and-continue-c"></a>Procedura: Usare Modifica e continuazione (C#)
Con modifica e continuazione, è possibile verificare e applicare le modifiche al codice in modalità di interruzione durante il debug, senza dover arrestare e riavviare la sessione di debug.

Modifica e continuazione per C# viene eseguita automaticamente quando è apportare modifiche al codice in modalità di interruzione, quindi continuare il debug usando **continuazione**, **passaggio**, o **Imposta istruzione successiva**, oppure si valuta una funzione in una finestra del debugger.

Per altre informazioni, vedere [modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Modifica e continuazione non è supportato per ottimizzato, misto, o codice di SQL Server common language runtime (CLR) integration. Per informazioni su altri scenari non supportati, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md). Se si tenta di modifica e continuazione con uno di questi scenari, viene visualizzata una finestra di messaggio che informa che modifica e continuazione non è supportato.

**Per abilitare o disabilitare Modifica e continuazione:**

1. Se lavora in una sessione di debug, arrestare il debug (**Debug** > **Termina debug** oppure **MAIUSC**+**F5**) .

1. Nella **degli strumenti** > **opzioni** (o **Debug** > **opzioni**) > **debug**  >  **Generali**, selezionare o deselezionare le **Abilita modifica e continuazione** casella di controllo.

L'impostazione diventa effettiva quando si avvia o riavvia la sessione di debug.

**Per usare modifica e continuazione:**

1. Durante il debug in modalità di interruzione, apportare una modifica al codice sorgente.

1. Dal **Debug** menu, fare clic su **continua**, **passaggio**, o **Imposta istruzione successiva**, oppure si valuta una funzione in una finestra del debugger.

   Debug continua con il nuovo codice compilato.

Alcuni tipi di modifiche al codice non sono supportate in modifica e continuazione. Per altre informazioni, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).
