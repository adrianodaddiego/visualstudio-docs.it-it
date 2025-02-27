---
title: Usare il sommario di Help Viewer in Visual Studio
ms.date: 11/02/2017
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e75a732ddc9c56e7305e4ebbfec6a188fb6df2bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951339"
---
# Procedura: Trovare argomenti nel sommario

Nella scheda **Contenuto** è possibile usare il sommario per trovare le informazioni. Il sommario è un elenco espandibile che contiene tutti argomenti dei libri installati. Per informazioni sull'accessibilità relative a come spostarsi nel sommario, vedere [Tasti di scelta rapida (Help Viewer)](../help-viewer/shortcut-keys.md).

> [!IMPORTANT]
> L'ambito degli argomenti disponibili nel sommario dipende dal filtro selezionato.

## Filtrare il sommario

È possibile filtrare il sommario per limitare l'ambito degli argomenti visualizzati nella scheda **Contenuto**. I titoli vengono visualizzati nell'elenco solo se contengono la radice del termine specificato. Ad esempio, se si specifica la parola "risoluzione" come filtro, verranno visualizzati solo i titoli contenenti la parola "risolvere" o "risoluzione". I nodi i cui titoli non contengono il termine verranno compressi in un unico nodo con i puntini di sospensione (**...**).

1. Scegliere la scheda **Contenuto**.

2. Nella casella di testo **Filtra contenuti** immettere un termine.

> [!NOTE]
> Se l'esecuzione del filtro richiede molto tempo, è possibile visualizzare i risultati più rapidamente usando l'operatore di ricerca avanzata `title:`.

## Sincronizzare un argomento con il sommario

Se un argomento è stato aperto tramite l'indice o le funzionalità di ricerca full-text, è possibile determinarne la posizione all'interno del sommario sincronizzando quest'ultimo con la finestra dell'argomento.

1. Visualizzare un argomento.

2. Fare clic sul pulsante **Mostra argomento nel contenuto** nella barra degli strumenti oppure premere **CTRL**+**S**.

     Viene aperta la scheda **Contenuto** in cui viene visualizzata la posizione dell'argomento nel sommario.

## Vedere anche

- [Procedura: Trovare argomenti nell'indice](../help-viewer/find-topics-index.md)
- [Procedura: Eseguire la ricerca di argomenti](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)