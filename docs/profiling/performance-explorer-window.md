---
title: Finestra Esplora prestazioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8ffa5340ceaa00adb5e86100d8e58c307f41d40
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62794434"
---
# <a name="performance-explorer-window"></a>Finestra Esplora prestazioni

La finestra **Esplora prestazioni** nell'IDE di Visual Studio consente di configurare e avviare sessioni di prestazioni tramite gli strumenti di profilatura di Visual Studio. Se è necessario aprire la finestra, seguire le istruzioni in [Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-cpu-sampling.md).

## <a name="performance-explorer-toolbar"></a>Barra degli strumenti di Esplora prestazioni

Nella barra degli strumenti di **Esplora prestazioni** sono disponibili le opzioni seguenti:

- **Avvia Creazione guidata sessione di prestazioni**: visualizza la Creazione guidata sessione di prestazioni che consente di aggiungere una nuova sessione di prestazioni nella finestra Esplora prestazioni.

- **Nuova sessione di prestazioni**: aggiunge una sessione di prestazioni vuota nella finestra Esplora prestazioni.

- **Avvia**: l'elenco del pulsante di comando **Avvia** consente di avviare l'applicazione di destinazione con la profilatura immediatamente abilitata (**Avvio con analisi**) o con la profilatura in sospeso (**Avvio con analisi sospeso**).

- **Metodo**: specifica se il metodo di profilatura della sessione è campionamento o strumentazione.

- **Interrompi**: chiude immediatamente l'applicazione di destinazione e il profiler.

- **Connetti/Disconnetti**: visualizza la finestra di dialogo **Connettere profiler a processo** per selezionare un processo in esecuzione a cui connettere il profiler.

## <a name="performance-explorer-window"></a>Finestra Esplora prestazioni

La finestra **Esplora prestazioni** contiene un controllo albero che visualizza i file binari e i file dei dati di rapporto di una o più sessioni di prestazioni.

- **Nome sessione**: la radice del controllo albero contiene il nome della sessione. Fare clic con il pulsante destro del mouse sul nome della sessione per impostare le proprietà della sessione o avviare l'applicazione di destinazione e il profiler.

- **Destinazioni**: visualizza i nomi dei file binari da profilare nella sessione. Fare clic con il pulsante destro del mouse su **Destinazioni** per aggiungere o rimuovere un file binario, un progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o un sito Web. Fare clic con il pulsante destro del mouse su un nome di destinazione per impostare le proprietà per il singolo file binario.

- **Report**: visualizza i nomi dei file di dati del profiler generati per la sessione. Fare clic con il pulsante destro del mouse su **Report** per aggiungere un rapporto esistente o confrontare due file di dati del profiler. Fare clic con il pulsante destro del mouse sul nome di un rapporto per aprire, rimuovere o esportare un file di dati del profiler.

## <a name="see-also"></a>Vedere anche

[Panoramiche](../profiling/overviews-performance-tools.md)
[Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
[Controllo della raccolta di dati](../profiling/controlling-data-collection.md)