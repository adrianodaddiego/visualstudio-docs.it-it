---
title: Convertire il metodo Get in proprietà; convertire una proprietà in metodo Get
ms.date: 01/26/2018
ms.topic: reference
ms.devlang: csharp
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 87fc623f781c54267fa70da7c5d2a341823e35ae
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263092"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Refactoring per convertire il metodo Get in proprietà o una proprietà in metodo Get

Questi refactoring si applicano a:

- C#

## <a name="convert-get-method-to-property"></a>Convertire il metodo Get in proprietà

**Cosa:** consente di convertire un metodo Get (e facoltativamente il metodo Set) in una proprietà.

**Quando:** si ha un metodo Get che non contiene logica.

### <a name="how-to"></a>Procedura

1. Posizionare il cursore nel nome del metodo Get.

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Sostituisci metodo con la proprietà** dal popup della finestra di anteprima.
   - **Mouse**
      - fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Sostituisci metodo con la proprietà** dal popup della finestra di anteprima.

1. (Facoltativo) Se si dispone di un metodo Set, è anche possibile convertire il metodo Set in questo momento selezionando **Sostituisci metodo Get e metodo Set con la proprietà**.

1. Se si è soddisfatti delle modifiche nell'anteprima del codice, premere **INVIO** o fare clic sulla correzione nel menu. Verrà eseguito il commit delle modifiche.

Esempio:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Convertire una proprietà in un metodo Get

**Cosa:** consente di convertire una proprietà in un metodo Get

**Quando:** è presente una proprietà con maggiori esigenze rispetto all'impostazione e al recupero immediati di un valore

### <a name="how-to"></a>Procedura

1. Posizionare il cursore nel nome del metodo Get.

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Sostituisci proprietà con metodi** dal popup della finestra di anteprima.
   - **Mouse**
      - fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Sostituisci proprietà con metodi** dal popup della finestra di anteprima.

1. Se si è soddisfatti delle modifiche nell'anteprima del codice, premere **INVIO** o fare clic sulla correzione nel menu. Verrà eseguito il commit delle modifiche.

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)