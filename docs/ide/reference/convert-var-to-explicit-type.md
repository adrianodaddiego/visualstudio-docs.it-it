---
title: Eseguire il refactoring del codice per sostituire var con un tipo esplicito
ms.date: 05/15/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2708bca578b613fac77e9b8ce77b1b2aff8f0945
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968152"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refactoring per sostituire var con un tipo esplicito

Usare questo refactoring per sostituire [var](/dotnet/csharp/language-reference/keywords/var) in una dichiarazione di variabile locale con un tipo esplicito.

Questo refactoring si applica a:

- C#

## <a name="why-to-use-an-explicit-type"></a>Motivi per usare un tipo esplicito

Di seguito sono riportati alcuni motivi per dichiarare una variabile con un tipo esplicito:

- Per migliorare la leggibilità del codice.

- Quando non si vuole inizializzare la variabile nella dichiarazione.

Tuttavia, [var](/dotnet/csharp/language-reference/keywords/var) deve essere usato quando una variabile viene inizializzata con un tipo anonimo e si accede alle proprietà dell'oggetto in un momento successivo. Per altre informazioni, vedere [Variabili locali tipizzate in modo implicito (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Come usare la funzionalità

1. Posizionare il cursore sulla parola chiave `var`.

1. Premere **CTRL**+**.** oppure fare clic sull'icona a forma di cacciavite ![icona cacciavite](../media/screwdriver-icon.png) nel margine del file di codice.

   ![Menu delle azioni rapide Usare un tipo esplicito](media/use-explicit-type.png)

1. Selezionare **Usare un tipo esplicito**. In alternativa, selezionare **Anteprima modifiche** per aprire la finestra di dialogo [Anteprima modifiche](../../ide/preview-changes.md) e quindi selezionare **Applica**.

## <a name="see-also"></a>Vedere anche

- [Variabili tipizzate in modo implicito (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)