---
title: 'Procedura: Tenere traccia del codice personalizzando la barra di scorrimento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da6745b3980b6ef5b0200c91d4abf245daadfa71
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113820"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Procedura: Tenere traccia del codice personalizzando la barra di scorrimento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si usano file di codice lunghi, può risultare difficile tenere presente tutto il contenuto. È possibile personalizzare la barra di scorrimento della finestra del codice per ottenere una panoramica del contenuto del codice.  
  
### <a name="to-show-annotations-on-the-scroll-bar"></a>Per mostrare le annotazioni sulla barra di scorrimento  
  
1. È possibile configurare la barra di scorrimento in modo da visualizzare le modifiche al codice, i punti di interruzione, gli errori e i segnalibri.  
  
     Aprire la pagina delle opzioni **Barra di scorrimento** (**Strumenti, Opzioni, Editor di testo, Tutti i linguaggi** o un linguaggio specifico oppure digitare **barra di scorrimento** nella finestra Avvio veloce).  
  
2. Selezionare **Mostra annotazioni su barra di scorrimento verticale** e quindi selezionare le annotazioni da visualizzare. L'opzione **Contrassegni** include punti di interruzione e segnalibri.  
  
3. Provare ora a eseguire l'operazione. Aprire un file di codice di grandi dimensioni e sostituire un elemento presente in diversi punti nel file. La barra di scorrimento mostra l'effetto delle sostituzioni, pertanto è possibile annullare le modifiche se è stato sostituito qualche elemento che non doveva essere sostituito.  
  
     Ecco l'aspetto della barra di scorrimento dopo la ricerca di una stringa. Si noti che vengono visualizzate tutte le istanze della stringa.  
  
     ![Barra di scorrimento dopo la ricerca di una stringa.](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")  
  
     Ecco la barra di scorrimento dopo la sostituzione di tutte le istanze della stringa. È possibile vedere immediatamente che l'operazione ha provocato alcuni problemi.  
  
     ![Barra di scorrimento dopo la sostituzione di una stringa con errori](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")  
  
### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Per impostare la modalità di visualizzazione per la barra di scorrimento  
  
1. La barra di scorrimento ha due modalità, modalità barra (impostazione predefinita) e modalità mappa. La modalità barra consente di visualizzare solo gli indicatori delle annotazioni sulla barra di scorrimento. In modalità mappa sulla barra di scorrimento sono rappresentate le righe di codice. È possibile scegliere la larghezza delle righe e se visualizzare o meno il codice sottostante quando si posiziona il puntatore su di esse. Quando si fa clic su una posizione sulla barra di scorrimento, il cursore si sposta in tale posizione nel codice. Le aree compresse hanno un'ombreggiatura diversa e vengono espanse quando si fa doppio clic su di esse.  
  
     Nella pagina delle opzioni **Barra di scorrimento** selezionare **Usa modalità barra per barra di scorrimento verticale** o **Usa modalità mappa per barra di scorrimento verticale**. È possibile scegliere la larghezza nell'elenco a discesa **Panoramica origine**.  
  
     Ecco come appare l'esempio di ricerca quando è attivata la modalità mappa e la larghezza viene impostata su Media:  
  
     ![Barra di scorrimento in modalità mappa](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")  
  
2. In modalità mappa per abilitare le anteprime del codice quando si sposta il cursore verso l'alto e il basso nella barra di scorrimento, selezionare l'opzione **Mostra descrizione comando anteprima**. L'aspetto è il seguente:  
  
     ![Barra di scorrimento con una descrizione comando](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")  
  
     Se si vogliono mantenere il comportamento di scorrimento della modalità mappa e la descrizione comando anteprima ma non si vuole visualizzare la panoramica del codice sorgente, è possibile impostare **Panoramica origine** su **Off**.
