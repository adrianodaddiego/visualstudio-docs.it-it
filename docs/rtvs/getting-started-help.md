---
title: Finestra della Guida per R
description: La Guida di R è integrata direttamente nella finestra interattiva in Visual Studio tramite il comando .
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: af6c6156b1d88c1d015f7700fc7bed061bbe9a76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950569"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Guida di R Tools per Visual Studio

La Guida di R è integrata direttamente nella finestra interattiva in Visual Studio. Quando si usa il comando `?`, ad esempio `?mtcars`, viene visualizzata la Guida dalla documentazione di R in una finestra di Visual Studio:

![Finestra della Guida in Visual Studio](media/help-window.png)

> [!Tip]
> La finestra della Guida, come tutte le finestre di Visual Studio, può essere disposta e ancorata a seconda delle proprie preferenze. Vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Per aprire i risultati della Guida in un browser, selezionare il menu **R Tools** > **Opzioni** e impostare la proprietà **Browser della Guida di R** su `External`. Vedere [R Tools for Visual Studio options](options-for-r-tools-in-visual-studio.md) (Opzioni di R Tools per Visual Studio).

Per eseguire ricerche nella Guida, usare il comando `??` seguito dal termine di ricerca. Se il termine di ricerca contiene spazi, usare le virgolette:

```R
??"Motor Trend"
```

![Risultati della ricerca nella Guida](media/help-search1.png)

La finestra della Guida ha anche un campo di immissione per la ricerca tramite il quale è possibile eseguire altre ricerche direttamente nella documentazione di R:

![Risultati della ricerca nella Guida tramite il campo di immissione](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Ricerca nella Guida integrata

Gli sviluppatori spesso cercano nella documentazione di R informazioni sui nomi di funzione, i set di dati e altri elementi. R Tools per Visual Studio (RTVS) semplifica il processo grazie all'integrazione delle ricerche nella Guida direttamente nell'editor e nelle finestre interattive.

- Se si preme **F1** durante un'operazione di completamento automatico, viene visualizzato un elenco di risultati della ricerca nella Guida corrispondenti alla sottostringa.
- Fare clic con il pulsante destro del mouse su un termine di ricerca, ad esempio una funzione, e selezionare il comando **Help on** (Guida su) per aprire la Guida per tale funzione. È anche possibile richiamare **Help on** (Guida su) per qualsiasi selezione.

    ![Richiamare la Guida mediante il menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse](media/help-right-click.png)

> [!Tip]
> Per aprire la Guida integrata in un browser, selezionare **R Tools** > **Opzioni** e impostare **Web browser F1** su `External`. Vedere [R Tools for Visual Studio options](options-for-r-tools-in-visual-studio.md) (Opzioni di R Tools per Visual Studio).

## <a name="integrated-stackoverflow-search"></a>Ricerca di StackOverflow integrata

Oltre a eseguire ricerche nella documentazione di R, gli sviluppatori spesso cercano anche in StackOverflow durante la scrittura del codice. RTVS semplifica anche tale processo. Fare clic con il pulsante destro del mouse su un termine o una selezione, selezionare il comando **Cerca nel Web** (**CTRL**+**F1**). Visual Studio apre una finestra con i risultati della ricerca nell'ambito di StackOverflow:

![Risultati della ricerca nel Web in Visual Studio](media/help-web-search-results.png)

È possibile modificare la stringa di ambito aggiunta, `R site:stackoverflow`, tramite l'opzione **R Tools** > **Opzioni** > **Stringa di ricerca sul Web F1**:

![Modifica dell'opzione Stringa di ricerca sul Web F1](media/options-dialog.png)

Se si preferisce visualizzare i risultati in un browser, modificare l'opzione **Web browser F1** come descritto in [Opzioni](options-for-r-tools-in-visual-studio.md).