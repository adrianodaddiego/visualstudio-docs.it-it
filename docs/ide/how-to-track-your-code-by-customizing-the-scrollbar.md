---
title: Modalità mappa e modalità barra della barra di scorrimento
ms.date: 09/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77f7db396b814eb9163c055b8fadb8793432acee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548319"
---
# <a name="how-to-customize-the-scroll-bar"></a>Procedura: Personalizzare la barra di scorrimento

Quando si usano file di codice di grandi dimensioni, può essere difficile tenere traccia di tutto il contenuto dei file. È possibile personalizzare la barra di scorrimento dell'editor di codice per ottenere una panoramica di cosa avviene nel codice.

## <a name="annotations"></a>Annotazioni

È possibile specificare se la barra di scorrimento deve mostrare annotazioni, ad esempio modifiche al codice, punti di interruzione, segnalibri, errori e posizione del cursore.

   1. Aprire la pagina delle opzioni **Barre di scorrimento** scegliendo **Strumenti** > **Opzioni** > **Editor di testo** > **Tutti i linguaggi** > **Barre di scorrimento**.

   2. Selezionare **Mostra annotazioni su barra di scorrimento verticale** e quindi selezionare le annotazioni da visualizzare. Le annotazioni disponibili sono:

      - modifiche
      - contrassegni
      - errori
      - posizione del cursore

      > [!TIP]
      > L'opzione **Mostra contrassegni** include punti di interruzione e segnalibri.

È possibile provarla aprendo un file di codice di grandi dimensioni e sostituendo una stringa di testo presente in diverse posizioni nel file. La barra di scorrimento mostra l'effetto delle sostituzioni, pertanto è possibile annullare le modifiche se è stato sostituito qualche elemento che non doveva essere sostituito.

Ecco l'aspetto della barra di scorrimento dopo la ricerca di una stringa. Si noti che tutte le istanze della stringa sono indicate nella barra di scorrimento.

![Barra di scorrimento di Visual Studio dopo la ricerca di una stringa](../ide/media/enhancedscrollbarsearch.png)

Ecco la barra di scorrimento dopo la sostituzione di tutte le istanze della stringa. I segni rossi nella barra di scorrimento indicano i punti in cui la sostituzione del testo ha introdotto errori.

![Barra di scorrimento di Visual Studio dopo la sostituzione di una stringa con errori](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Modalità di visualizzazione

La barra di scorrimento ha due modalità: modalità barra (impostazione predefinita) e modalità mappa.

### <a name="bar-mode"></a>Modalità barra

La *modalità barra* visualizza indicatori di annotazione sulla barra di scorrimento. Facendo clic sulla barra di scorrimento, è possibile scorrere la pagina verso l'alto o verso il basso, ma non passare alla posizione corrispondente nel file.

### <a name="map-mode"></a>Modalità mappa

Quando in *modalità mappa* si fa clic su una posizione sulla barra di scorrimento, il cursore passa alla posizione nel file anziché scorrere semplicemente la pagina verso l'alto o verso il basso. Sulla barra di scorrimento vengono visualizzate, in miniatura, righe di codice. È possibile scegliere la larghezza della colonna della mappa selezionando un valore in **Panoramica origine**. Per abilitare un'anteprima di dimensioni maggiori del codice quando si posiziona il puntatore del mouse sulla mappa, selezionare l'opzione **Mostra descrizione comando anteprima**. Le aree compresse hanno un'ombreggiatura diversa e si espandono quando si fa doppio clic su di esse.

> [!TIP]
> È possibile disattivare la visualizzazione del codice in miniatura in modalità mappa impostando **Panoramica origine** su **Disattivata**. Se l'opzione **Mostra descrizione comando anteprima** è selezionata, viene comunque visualizzata un'anteprima del codice in tale posizione quando si posiziona il puntatore del mouse sulla barra di scorrimento e il cursore passa comunque alla posizione nel file quando si fa clic.

L'immagine seguente mostra l'esempio di ricerca quando è attiva la modalità mappa e la larghezza è impostata su **Media**:

![Barra di scorrimento di Visual Studio in modalità mappa](../ide/media/enhancedscrollbar.png)

La figura seguente mostra l'opzione **Mostra descrizione comando anteprima**:

![Barra di scorrimento di Visual Studio con una descrizione comando](../ide/media/enhancedscrollbarsearchtooltip.png)

## <a name="see-also"></a>Vedere anche

- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)