---
title: 'Procedura: Usare lo strumento di ricerca | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf3fcf00486ebb8ec54f2d692d483a7f9cf18d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387663"
---
# <a name="how-to-use-the-finder-tool"></a>Procedura: Usare lo strumento di ricerca
È possibile usare lo strumento di ricerca nel **Trova finestra** finestra di dialogo per visualizzare le proprietà della finestra o messaggi. Lo strumento di ricerca consente anche di individuare finestre figlio disabilitato e discernere quale finestra per evidenziare se disabilitata finestre figlio si sovrappongono.

 ![Spy&#43; &#43; finestra di dialogo Trova](../debugger/media/icon_spy--_find.png "Icon_Spy + + Find") strumento di ricerca nella finestra di dialogo Trova finestra

 La figura precedente mostra la finestra di dialogo Trova finestra dopo il passaggio 3 riportato di seguito.

### <a name="to-display-window-properties-or-messages"></a>Per visualizzare le proprietà della finestra o messaggi

1. Disporre le finestre in modo che sia Spy + + e la finestra di destinazione sono visibili.

2. Dal **Spy** menu, scegliere **Trova finestra**.

    Il [finestra di dialogo Trova](../debugger/find-window-dialog-box.md) apre.

3. Trascinare il **strumento di ricerca** nell'intervallo di destinazione.

    Quando si trascina lo strumento, il **Trova finestra** nella finestra di dialogo vengono visualizzati i dettagli sulla finestra selezionata.

   - oppure -

     Se hai l'handle della finestra di cui si vuole esaminare (ad esempio, copiato dal debugger), digitarla nella **gestire** casella di testo.

   > [!TIP]
   > Per ridurre il disordine schermata, selezionare la **Nascondi Spy + +** opzione. Questa opzione consente di nascondere la finestra principale di Spy + + e di mantenere solo le **Trova finestra** nella finestra di dialogo visibile nella parte superiore alle altre applicazioni. La finestra principale di Spy + + è ripristinata quando si fa clic **OK** oppure **Cancel**, o quando si cancella il **Nascondi Spy + +** opzione.

4. Sotto **mostrano**, selezionare **proprietà** oppure **messaggi**.

5. Fare clic su **OK**.

    Se è stato selezionato **delle proprietà**, il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md) apre. Se è stato selezionato **messaggi**, un [visualizzazione messaggi](../debugger/messages-view.md) verrà visualizzata la finestra.

## <a name="see-also"></a>Vedere anche
- [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)
- [Uso di Spy++](../debugger/using-spy-increment.md)
- [riferimenti per Spy++](../debugger/spy-increment-reference.md)