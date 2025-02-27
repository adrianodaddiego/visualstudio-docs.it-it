---
title: Finestra Esplora prestazioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a370ae802408ecc821de4cd15824f9d1fca42b75
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105331"
---
# <a name="performance-explorer-window"></a>Finestra Esplora prestazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La finestra **Esplora prestazioni** nell'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di configurare e avviare sessioni di prestazioni tramite gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
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
  
- **Destinazioni**: visualizza i nomi dei file binari da profilare nella sessione. Fare clic con il pulsante destro del mouse su **Destinazioni** per aggiungere o rimuovere un file binario, un progetto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o un sito Web. Fare clic con il pulsante destro del mouse su un nome di destinazione per impostare le proprietà per il singolo file binario.  
  
- **Report**: visualizza i nomi dei file di dati del profiler generati per la sessione. Fare clic con il pulsante destro del mouse su **Report** per aggiungere un rapporto esistente o confrontare due file di dati del profiler. Fare clic con il pulsante destro del mouse sul nome di un rapporto per aprire, rimuovere o esportare un file di dati del profiler.  
  
## <a name="see-also"></a>Vedere anche  
 [Overviews](../profiling/overviews-performance-tools.md)  (Panoramiche)  
 [Configuring Performance Sessions](../profiling/configuring-performance-sessions.md)  (Configurazione di sessioni di prestazioni)  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)
