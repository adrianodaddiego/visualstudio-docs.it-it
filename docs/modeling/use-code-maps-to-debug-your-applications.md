---
title: Usare le mappe codice per eseguire il debug delle applicazioni
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e421c65e83bca88c01ea58cfd5cc402c6011cb23
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907901"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Usare le mappe codice per eseguire il debug delle applicazioni

Le mappe codice consentono di evitare di perdersi nelle codebase di grandi dimensioni, nel codice con cui si ha poca familiarità o nel codice legacy. Quando esegue il debug, ad esempio, potrebbe essere necessario esaminare codice nei file e progetti diversi. Usare le mappe codice per esplorare queste parti di codice e comprendere le relazioni tra loro. In questo modo, non è necessario tenere traccia di questo codice a mente o creare un diagramma separato. Se il lavoro viene interrotto, le mappe codice consentono di aggiornare la memoria relativa al codice usato.

![Mappa del codice &#45; eseguire il mapping di relazioni nel codice](../modeling/media/codemapstoryboardpaint.png)

**Una freccia verde indica la posizione il cursore nell'editor**

Per informazioni dettagliate dei comandi e le azioni è possibile usare quando si lavora con le mappe codici, vedere [cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md).

> [!NOTE]
> Per creare e modificare mappe del codice, è necessario Visual Studio Enterprise edition. In Visual Studio Community e Professional Edition, è possibile aprire diagrammi generati in Enterprise edition, ma non modificarli.

## <a name="understand-the-problem"></a>Informazioni sul problema
 Si supponga che sia presente un bug in un programma di disegno su cui si sta lavorando. Per riprodurre il bug, aprire la soluzione in Visual Studio e premere **F5** per avviare il debug.

 Quando Disegna una linea e si sceglie **Annulla ultimo tratto**, non accade nulla fino a quando non si disegna la riga successiva.

 ![Mappa del codice &#45; bug Repro](../modeling/media/codemapstoryboardpaint0.png)

 Di conseguenza, iniziare l'analisi cercando il metodo `Undo`. Il metodo si trova nella classe `PaintCanvas`.

 ![Mappa del codice &#45; trovare codice](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Avviare il mapping del codice
 A questo punto è possibile avviare il mapping del metodo `undo` e le relative relazioni. Nell'editor di codice aggiungere il metodo `undo` e i campi a cui viene fatto riferimento a una nuova mappa codici. Quando si crea una nuova mappa, l'indicizzazione del codice potrebbe richiedere del tempo. Ciò consente alle operazioni successive di essere eseguite più velocemente.

 ![Mappa del codice &#45; Mostra metodo e i campi correlati](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> L'evidenziazione verde indica gli ultimi elementi aggiunti alla mappa. La freccia verde indica la posizione del cursore nel codice. Le frecce tra gli elementi rappresentano relazioni diverse. È possibile ottenere altre informazioni sugli elementi nella mappa spostandovi sopra il mouse ed esaminando le relative descrizioni comandi.

 ![Mappa del codice &#45; visualizzazione di descrizioni comandi](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Passare al codice ed esaminarlo dal mapping
 Per visualizzare la definizione di codice per ogni campo, fare doppio clic sul campo nella mappa o selezionare il campo e premere **F12**. La freccia verde si sposta tra gli elementi nella mappa. Il cursore nell'editor di codice viene spostato automaticamente.

 ![Mappa del codice &#45; esaminare la definizione di campo](../modeling/media/codemapstoryboardpaint5.png)

 ![Mappa del codice &#45; esaminare la definizione di campo](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> È inoltre possibile spostare la freccia verde sulla mappa spostando il cursore nell'editor di codice.

## <a name="understand-relationships-between-pieces-of-code"></a>Informazioni sulle relazioni tra parti di codice
 A questo punto si desidera sapere quale altro codice interagisce con i campi `history` e `paintObjects`. È possibile aggiungere tutti i metodi che fanno riferimento a questi campi alla mappa. Questa operazione può essere eseguita dalla mappa o dall'editor di codice.

 ![Mappa del codice &#45; Trova tutti i riferimenti](../modeling/media/codemapstoryboardpaint6.png)

 ![Aprire una mappa del codice nell'editor del codice](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Se si aggiungono elementi da un progetto condiviso in più applicazioni, ad esempio Windows Phone o Windows Store, tali elementi vengono sempre visualizzati nella mappa insieme al progetto di app attualmente attivo. Se pertanto si modifica il contesto in un altro progetto di app, il contesto nella mappa viene modificato anche per tutti gli elementi appena aggiunti dal progetto condiviso. Le operazioni eseguite con un elemento nella mappa si applicano solo agli elementi che condividono lo stesso contesto.

 Modificare il layout per ridisporre il flusso di relazioni e rendere la mappa più facile da leggere. È inoltre possibile spostare elementi nella mappa trascinandoli.

 ![Mappa del codice &#45; modificare il layout](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Per impostazione predefinita **Layout incrementale** è attivata. Ciò consente di ridisporre la mappa il meno possibile quando vengono aggiunti nuovi elementi. Per ridisporre l'intera mappa ogni volta che si aggiungono nuovi elementi, disattivare **Layout incrementale**.

 ![Mappa del codice &#45; modificare il layout](../modeling/media/codemapstoryboardpaint7.png)

 Esaminiamo questi metodi. Sulla mappa, fare doppio clic il **PaintCanvas** metodo, o selezionarlo e premere **F12**. Questo metodo crea `history` e `paintObjects` come elenchi vuoti.

 ![Mappa del codice &#45; esaminare la definizione di metodo](../modeling/media/codemapstoryboardpaint8.png)

 A questo punto, ripetere gli stessi passaggi per esaminare la definizione del metodo `clear`. Il metodo `clear` esegue alcune attività con `paintObjects` e `history` e quindi chiama il metodo `Repaint`.

 ![Mappa del codice &#45; esaminare la definizione di metodo](../modeling/media/codemapstoryboardpaint9.png)

 A questo punto, esaminare la definizione del metodo `addPaintObject`. Tale metodo esegue alcune attività con `history` e `paintObjects`. e chiama inoltre `Repaint`.

 ![Mappa del codice &#45; esaminare la definizione di metodo](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Individuare il problema esaminando il mapping
 Sembra che tutti i metodi che modificano `history` e `paintObjects` chiamino `Repaint`. Tuttavia il metodo `undo` non chiama `Repaint`, anche se `undo` modifica gli stessi campi. Pertanto, è possibile risolvere il problema chiamando `Repaint` da `undo`.

 ![Mappa del codice &#45; Find chiamata al metodo mancante](../modeling/media/codemapstoryboardpaint11.png)

 Se non fosse stata disponibile una mappa che mostrava questa chiamata mancante, sarebbe stato più difficile individuare il problema, specialmente in caso di codice più complesso.

## <a name="share-your-discovery-and-next-steps"></a>Condividere l'individuazione e passaggi successivi
 Prima che l'utente o un altro sviluppatore corregga il bug, è possibile inserire note nella mappa sul problema e su come correggerlo.

 ![Mappa del codice &#45; elementi di commento e il flag per completamento](../modeling/media/codemapstoryboardpaint12.png)

 Ad esempio, è possibile aggiungere commenti alla mappa e contrassegnare gli elementi usando i colori.

 ![Mappa del codice &#45; commenti e gli elementi con flag](../modeling/media/codemapstoryboardpaint12a.png)

 Se Microsoft Outlook è installato, è possibile inviare la mappa ad altre persone tramite posta elettronica. È inoltre possibile esportare la mappa come un'immagine o in un altro formato.

 ![Mappa del codice &#45; condivisione di esportazione, posta elettronica](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Correggere il problema e visualizzare le operazioni effettuate
 Per correggere il bug, aggiungere la chiamata per `Repaint` a `undo`.

 ![Mappa del codice &#45; aggiungere una chiamata al metodo mancante](../modeling/media/codemapstoryboardpaint14.png)

 Per confermare la correzione, riavviare la sessione di debug e tentare di riprodurre il bug. A questo punto la scelta **Annulla ultimo tratto** funziona come previsto e conferma reso la soluzione corretta.

 ![Mappa del codice &#45; Confirm correzione del codice](../modeling/media/codemapstoryboardpaint15.png)

 È possibile aggiornare la mappa per mostrare la correzione apportata.

 ![Mappa del codice &#45; aggiornare la mappa con una chiamata al metodo mancante](../modeling/media/codemapstoryboardpaint16.png)

 La mappa mostrerà un collegamento tra **undo** e **ridisegnare**.

 ![Mappa del codice &#45; mappa aggiornata con la chiamata di metodo](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Quando si aggiorna la mappa, è possibile che venga visualizzato un messaggio che indica che l'indice di codice usato per creare la mappa è stato aggiornato. Ciò significa che un utente ha modificato il codice e di conseguenza la mappa non corrisponde al codice corrente. L'aggiornamento della mappa non verrà arrestato, ma potrebbe essere necessario ricreare la mappa per confermare che corrisponde al codice.

 A questo punto è terminata con l'analisi. Il problema è stato individuato e corretto eseguendo il mapping del codice. Si dispone inoltre di una mappa che consente di spostarsi nel codice e di ricordare quanto indicato e che mostra i passaggi eseguiti per correggere il problema.

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping dei metodi nello stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Visualizzare il codice](../modeling/visualize-code.md)
