---
title: Prestazioni di XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ecc5482c8519ceadfe1e6d5db7880c98b3d2ceb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988033"
---
# <a name="the-xslt-profiler"></a>Il Profiler XSLT

Il Profiler XSLT crea rapporti di prestazioni XSLT dettagliati utili per misurare, valutare e trattare problemi correlati alle prestazioni nel codice XSLT. Il Profiler XSLT include suggerimenti utili per le ottimizzazioni dei fogli di stile XSL e XSLT. Per applicazioni XSLT che richiedono massime prestazioni, questo strumento potrebbe essere essenziale.

Il Profiler XSLT è parte di Visual Studio ed è disponibile nel **XML** menu.

![Profiler XSLT](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> Il Profiler XSLT è disponibile solo nell'edizione Enterprise di Visual Studio.

## <a name="create-a-performance-report"></a>Creare un report di prestazioni

1. Aprire un documento XSLT in Visual Studio.

2. Nella barra dei menu, scegliere **XML** > **profila XSLT**.

3. Fornire un documento XML di input. Se non è già aperto un documento XML, verrà richiesto il file.

   L'analisi viene avviata e un indicatore di stato visualizza lo stato di avanzamento all'interno dell'editor. Anche l'output XSLT è visibile.

4. Al termine della sessione di prestazioni, controllare il report sulle prestazioni per analizzare le prestazioni di XSLT.

## <a name="get-all-available-views"></a>Ottenere tutte le visualizzazioni disponibili

1. Fare clic sui **vista corrente** elenco a discesa per ottenere tutte le visualizzazioni disponibili.

2. Selezionare il **visualizzazione di riepilogo** opzione il **visualizzazione corrente** elenco a discesa. Per impostazione predefinita, viene visualizzato un report di prestazioni nel **visualizzazione di riepilogo**. Questa visualizzazione costituisce un punto iniziale per determinare problemi di prestazioni con i documenti XSLT. Il **visualizzazione di riepilogo** sono elencati i punti dati seguenti:

   - Funzioni più chiamate

   - Funzioni con più lavoro individuale

   - Funzioni la cui esecuzione richiede più tempo

   Per impostazione predefinita, esistono tre colonne per ogni punto dati: il nome della funzione, il numero di chiamate in valore assoluto e un valore percentuale della funzione denominata per sommare le chiamate di funzione. Da ogni punto dati nella **visualizzazione di riepilogo**, è possibile passare a visualizzazioni più dettagliate facendo clic sui punti dati (funzione).

3. Selezionare il **visualizzazione funzione** opzione il **visualizzazione corrente** elenco a discesa. Il **visualizzazione funzione** Elenca le funzioni chiamate durante la profilatura. Per ordinare i dati è possibile fare clic sul nome di una colonna. Le colonne visualizzate per impostazione predefinita sono:

    - **Nome funzione**

    - **Tempo inclusivo trascorso**

    - **Tempo esclusivo trascorso**

    - **Tempo inclusivo applicazione**

    - **Tempo esclusivo applicazione**

    - **Numero di chiamate**

   Tutte le colonne dell'ora vengono visualizzate sia in valori assoluti che in percentuali. Il termine **esclusivo** si riferisce al tempo totale di una funzione per l'esecuzione, escluso il tempo impiegato da altre funzioni chiamata durante l'esecuzione di questa funzione.

   Il termine **inclusivo** si riferisce al tempo totale impiegato da una funzione per l'esecuzione, incluso il tempo di esecuzione di tutte le funzioni chiamate e indica se uno qualsiasi di queste funzioni chiamate ha chiamato altre funzioni.

## <a name="select-callercallee-view"></a>Selezionare la visualizzazione Chiamante/chiamato

Selezionare **chiamante/chiamato** visualizzare il **visualizzazione corrente** elenco a discesa. Il **chiamante/chiamato** Vista ha tre parti distinte seguenti:

- **Funzioni che hanno chiamato**: Tutte le funzioni che ha chiamato una particolare funzione vengono elencate nella parte superiore della visualizzazione.

- **Funzione corrente**: La funzione specifica che è stata chiamata è elencata nella parte centrale della visualizzazione.

- **Le funzioni chiamate dalla**: Tutte le funzioni chiamate dalla particolare funzione vengono elencate nella parte inferiore della visualizzazione.

Se una funzione denominata `SyncToNavigator` viene riportata nella parte centrale della visualizzazione, tutte le funzioni che hanno chiamato la funzione `SyncToNavigator` vengono visualizzate nella parte superiore della visualizzazione e tutte le funzioni che sono state chiamate da `SyncToNavigator` vengono elencate nella parte inferiore della visualizzazione.

- È possibile modificare la funzione nella parte centrale della visualizzazione facendo doppio clic su una delle funzioni elencate nelle altre due parti della visualizzazione. La visualizzazione verrà quindi automaticamente aggiornata in base alle modifiche.

- Per ordinare i dati, è anche possibile fare clic sui nomi delle colonne.

## <a name="select-call-tree-view"></a>Selezionare una visualizzazione albero delle chiamate

- Selezionare **visualizzazione albero delle chiamate** nel **visualizzazione corrente** elenco a discesa. Questa visualizzazione è un albero dell'esecuzione del programma.

   Il **visualizzazione albero delle chiamate** mostri la radice dell'albero come nome del processo. Le funzioni sono i nodi dell'albero. Questa visualizzazione consente di esaminare determinate tracce di chiamata e di analizzare quali tracce hanno il maggiore impatto sulle prestazioni. La visualizzazione è simile al **visualizzazione Stack di chiamate** disponibile durante il debug. Oltre alle colonne nel **visualizzazione funzione**, nella **visualizzazione albero delle chiamate**, è una colonna aggiuntiva per visualizzare il **nome modulo**.

- Selezionare **segni** nel **visualizzazione corrente** elenco a discesa.

   Con il Profiler XSLT, sono presenti contrassegni nel flusso di raccolta dati con un commento associato. I contrassegni sono parti del codice che dispongono di contatori. Indicando al Profiler XSLT di raccogliere contatori delle prestazioni XSLT, i contatori vengono raccolti ogni volta che viene eseguito uno di questi contrassegni. I dati vengono visualizzati in una tabella che contiene il **ID contrassegno**, **nome contrassegno** (**Avvia programma**, **termina programma**) e il  **Data e ora**. I contrassegni non vengono aggregati e visualizzati in ordine cronologico nel **visualizzazione contrassegni** del rapporto di prestazioni.

## <a name="select-modules-in-the-current-view"></a>Selezionare i moduli nella visualizzazione corrente

- Selezionare **moduli** nel **visualizzazione corrente** elenco a discesa.

   La visualizzazione dei moduli è un elenco completo di tutte le funzioni aggregate a livello di modulo. Espandere o comprimere il nome del modulo per visualizzare o chiudere la visualizzazione dei dati relativi alle prestazioni del modulo. Per ordinare i dati è possibile fare clic sul nome di una colonna. Per impostazione predefinita, esistono sia valori assoluti che numeri in percentuale per **corrispondente al tempo inclusivo trascorso**, **corrispondente al tempo esclusivo trascorso**, **tempo inclusivo applicazione**, **Corrispondente al tempo esclusivo applicazione**, e **numero di chiamate**.

- Selezionare **processo** nel **visualizzazione corrente** elenco a discesa.

   La visualizzazione processo Visualizza una tabella che include il **ID del processo**, **nome del processo**, **ora di inizio**e il **ora di fine**. Per ordinare i dati, è possibile fare clic sui nomi delle colonne.

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Uso della gerarchia XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)