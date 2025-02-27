---
title: Aggiungere una regola di soglia per i test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a5865eba5ec6971a35104af3ccd090ee6b06410
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002290"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Procedura: Aggiungere una regola di soglia usando l'Editor test di carico

Le regole di soglia nei test di carico consentono di confrontare il valore di un contatore delle prestazioni con il valore di una costante o di un altro contatore delle prestazioni.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Per aggiungere una regola di soglia

1. Aprire un test di carico.

2. Nell'Editor test di carico espandere il nodo **Insiemi di contatori**.

3. Espandere una delle **Categorie contatori** in uno degli Insiemi di contatori. Ad esempio, è possibile selezionare **LoadTest:Scenario**. Espandere il nodo.

4. Fare clic con il pulsante destro del mouse sui contatori, ad esempio **Carico utente**, in **LoadTest:Scenario**. Selezionare **Aggiungi regola di soglia**.

     Viene visualizzata la finestra di dialogo **Aggiungi regola di soglia**.

5. È possibile scegliere tra due tipi di regole: **Confronta costante** e **Confronta Contatori**. Selezionare il tipo appropriato e impostare i valori.

    > [!NOTE]
    > Impostare la proprietà **Avvisa se supera** su **True** per indicare che il superamento della soglia è un problema oppure su **False** per indicare che il non raggiungimento della soglia è un problema.

## <a name="see-also"></a>Vedere anche

- [Analisi delle violazioni delle regole di soglia](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
