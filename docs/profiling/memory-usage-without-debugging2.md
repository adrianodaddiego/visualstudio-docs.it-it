---
title: Analizzare l'utilizzo della memoria senza debug | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e59e1bd618cfeb28b93d073997ef451357ee8d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830699"
---
# <a name="analyze-memory-usage-without-the-debugger"></a>Analizzare l'utilizzo della memoria senza il debugger

Lo strumento **Utilizzo memoria** monitora l'utilizzo della memoria dell'app. È possibile utilizzare lo strumento per studiare gli effetti in tempo reale sulla memoria degli scenari in corso di sviluppo attivo in Visual Studio. Creare snapshot dettagliati degli stati di memoria dell'app e confrontare gli snapshot per individuare le cause principali dei problemi di memoria.

Lo strumento **Utilizzo memoria** può essere eseguito con o senza debugger. Le istruzioni seguenti illustrano come usare lo strumento **Utilizzo memoria** senza il debugger, con **Profiler prestazioni** di Visual Studio.

>[!NOTE]
>- Per misurare l'utilizzo della memoria da parte di un'app .NET Core, è necessario utilizzare lo strumento **Utilizzo memoria** con il debugger. Per istruzioni, vedere [Profilare l'utilizzo della memoria in Visual Studio](memory-usage.md).
>- Per analizzare il consumo di memoria nelle app JavaScript o HTML UWP, usare lo strumento [Memoria JavaScript](../profiling/javascript-memory.md) in **Profiler prestazioni**.

## <a name="memory-usage-diagnostic-sessions"></a>Sessioni di diagnostica con lo strumento Utilizzo memoria

**Per avviare una sessione di diagnostica con lo strumento Utilizzo memoria:**

1. Aprire un progetto universale di Windows C# (UWP) in Visual Studio.

1. Nella barra dei menu scegliere **Debug** > **Profiler prestazioni**.

1. Selezionare **Utilizzo memoria**, quindi selezionare **Avvia**.

   ![Avviare una sessione di diagnostica con lo strumento Utilizzo memoria](../profiling/media/memuse_start_diagnosticssession.png "Avviare una sessione di diagnostica con lo strumento Utilizzo memoria")

### <a name="monitor-memory-use"></a>Monitorare l'uso della memoria

Quando si avvia una sessione di diagnostica, l'app viene avviata e nella finestra **Strumenti di diagnostica** viene visualizzato un grafico della sequenza temporale dell'uso della memoria dell'app.

![Pagina delle informazioni generali dello strumento Utilizzo memoria](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Il grafico della sequenza temporale mostra le fluttuazioni di memoria durante l'esecuzione dell'app. Eventuali picchi nel grafico in genere indicano che alcune stringhe di codice stanno raccogliendo o creando dati, per poi rimuoverli al termine del processo. Picchi significativi indicano aree che potrebbero essere ottimizzate. Più preoccupante sarebbe un aumento del consumo di memoria che non torna ai valori normali, perché può indicare un uso della memoria non efficiente o addirittura una perdita di memoria.

### <a name="take-snapshots-of-app-memory-states"></a>Creare snapshot degli stati di memoria dell'app

Poiché un'app usa un gran numero di oggetti, si potrebbe voler concentrare la propria analisi su un solo scenario. Oppure, si potrebbe desiderare esaminare i problemi di memoria. Durante una sessione di diagnostica è possibile creare alcuni snapshot per rilevare l'utilizzo della memoria in determinati momenti. È buona prassi acquisire uno snapshot di base di un'app prima che si verifichi un problema di memoria, un altro dopo che il problema si presenta per la prima volta e snapshot aggiuntivi se si può ripetere lo scenario.

Per raccogliere gli snapshot, scegliere **Crea snapshot** quando si vogliono acquisire i dati di memoria.

### <a name="BKMK_Close_a_monitoring_session"></a> Chiudere la sessione di diagnostica

Per arrestare una sessione di monitoraggio senza creare un report, chiudi semplicemente la finestra di diagnostica. Per generare un report al termine della raccolta o della creazione di snapshot, selezionare **Arresta raccolta**.

![Arresta raccolta](../profiling/media/memuse__stopcollection.png "Arresta raccolta")

## <a name="memory-usage-reports"></a>Report sull'utilizzo della memoria

Una volta completata la raccolta dei dati, lo strumento **Utilizzo memoria** arresta l'app e visualizza la pagina di panoramica **Utilizzo memoria**.

![Pagina di panoramica Utilizzo memoria](../profiling/media/memuse__reportoverview1.png "Pagina di panoramica Utilizzo memoria")

### <a name="BKMK_Memory_Usage_snapshot_views"></a> Snapshot di Utilizzo memoria

I numeri dei riquadri **Snapshot** mostrano i byte e gli oggetti in memoria quando è stato creato ogni snapshot e la differenza tra lo snapshot e quello precedente.

I numeri sono collegamenti che aprono visualizzazioni report dettagliate di **Utilizzo memoria** in nuove finestre di Visual Studio. Un [report dettagli dello snapshot](#snapshot-details-reports) mostra i tipi e le istanze in uno snapshot. Un [report differenze degli snapshot](#snapshot-difference-diff-reports) confronta i tipi e le istanze in due snapshot.

  ![Collegamenti delle visualizzazioni snapshot](../profiling/media/memuse__snapshotview_numbered.png "Collegamenti delle visualizzazioni snapshot")

|||
|-|-|
|![Passaggio 1](../profiling/media/procguid_1.png "ProcGuid_1")|Il numero totale di byte in memoria quando è stato creato lo snapshot.<br /><br /> Selezionare questo collegamento per visualizzare un report dettagli dello snapshot, ordinato in base alla dimensione totale delle istanze di tipo.|
|![Passaggio 2](../profiling/media/procguid_2.png "ProcGuid_2")|Il numero totale di oggetti in memoria quando è stato creato lo snapshot.<br /><br /> Selezionare questo collegamento per visualizzare un report dettagli dello snapshot, ordinato in base al numero di istanze dei tipi.|
|![Passaggio 3](../profiling/media/procguid_3.png "ProcGuid_3")|La differenza tra la dimensione totale degli oggetti di memoria in questo snapshot e nello snapshot precedente. <br /><br /> Un numero positivo indica che la dimensione della memoria dello snapshot è maggiore rispetto allo snapshot precedente e un numero negativo indica che la dimensione è minore. **Linea di base** significa che uno snapshot è il primo di una sessione di diagnostica. **Nessuna differenza** significa che la differenza è zero.<br /><br /> Selezionare questo collegamento per visualizzare un report differenze degli snapshot, ordinato in base alla differenza riguardo alla dimensione totale delle istanze dei tipi.|
|![Passaggio 4](../profiling/media/procguid_4.png "ProcGuid_4")|La differenza tra il numero totale degli oggetti di memoria in questo snapshot e nello snapshot precedente.<br /><br /> Selezionare questo collegamento per visualizzare un report differenze degli snapshot, ordinato in base alla differenza riguardo al numero totale delle istanze dei tipi.|

## <a name="memory-usage-snapshot-reports"></a>Report snapshot di Utilizzo memoria

<a name="BKMK_Snapshot_report_trees"></a> Quando si seleziona uno dei collegamenti dello snapshot nella pagina di panoramica **Utilizzo di memoria**, un report snapshot viene aperto in una nuova pagina.

![Report snapshot dello strumento Utilizzo memoria](../profiling/media/memuse_snapshotreport_all.png "Report snapshot dello strumento Utilizzo memoria")

In un report snapshot è possibile espandere le voci **Tipo di oggetto** per visualizzare le voci figlio. I nomi di istanza sono ID univoci generati dallo strumento Utilizzo memoria.

Se un **Tipo di oggetto** è blu, è possibile selezionarlo per passare all'oggetto nel codice sorgente, in una finestra separata.

I tipi che non è possibile identificare o il cui coinvolgimento nel codice risulta sconosciuto appartengono probabilmente al sistema operativo .NET Framework o agli oggetti del compilatore. Lo strumento **Utilizzo memoria** visualizza questi oggetti se sono coinvolti nelle catene di proprietà degli oggetti.

Nei report snapshot:

- L'albero **Heap gestito** mostra i tipi e le istanze presenti nel report. Quando si seleziona un tipo o un'istanza, vengono visualizzati gli alberi **Percorsi della radice** e **Oggetti a cui si fa riferimento** per l'elemento selezionato.

- L'albero **Percorsi della radice** mostra la catena di oggetti che fanno riferimento a un tipo o a un'istanza. Garbage Collector di .NET Framework pulisce la memoria per un oggetto solo una volta rilasciati tutti i riferimenti.

- L'albero **Tipi a cui si fa riferimento** o **Oggetti a cui si fa riferimento** mostra gli oggetti a cui fa riferimento l'istanza o il tipo selezionato.

### <a name="BKMK_Report_tree_filters_"></a> Filtri degli alberi dei rapporti

Molti tipi di app non sono particolarmente interessanti per gli sviluppatori di app. I filtri dei report snapshot possono nascondere la maggior parte di questi tipi negli alberi **Heap gestito** e **Percorsi della radice**.

![Opzioni di ordinamento e filtro](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a> Per filtrare un albero in base al nome del tipo, immettere il nome nella casella **Filtro**. Il filtro non fa distinzione tra maiuscole e minuscole e riconosce la stringa specificata in ogni parte del nome del tipo.

- <a name="BKMK_Collapse_Small_Objects"></a> Selezionare **Comprimi oggetti piccoli** nell'elenco a discesa **Filtro** per nascondere i tipi la cui **Dimensione (byte)** è minore dello 0,5% della memoria totale.

- <a name="BKMK_Just_My_Code"></a> Selezionare **Just My Code** nell'elenco a discesa **Filtro** per nascondere la maggior parte delle istanze generate da codice esterno. I tipi esterni appartengono al sistema operativo, ai componenti del framework oppure sono generati dal compilatore.

## <a name="snapshot-details-reports"></a>Report dettagli degli snapshot

 Un report dettagli dello snapshot descrive uno snapshot di una sessione di diagnostica. Per aprire il report, selezionare il collegamento alla dimensione o agli oggetti in un riquadro dello snapshot.

 ![Collegamenti al report snapshot in un riquadro snapshot](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "Collegamenti al report snapshot in un riquadro snapshot")

Entrambi i collegamenti aprono lo stesso report. L'unica differenza è il tipo di ordinamento iniziale dell'albero **Heap gestito**. Il collegamento dimensione ordina il rapporto in base alla colonna **Dimensione inclusiva (byte)**. Il collegamento Oggetti ordina il rapporto in base alla colonna **Conteggio**. È possibile modificare il tipo o la colonna di ordinamento dopo l'apertura del report.

### <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Albero Heap gestito (report dettagli dello snapshot)
 Nell'albero **Heap gestito** sono elencati i tipi di oggetti contenuti in memoria. Espandere un nome di tipo per visualizzare le dieci istanze più grandi del tipo, ordinate in base alla dimensione. Selezionare un tipo o un'istanza per visualizzare gli alberi **Percorsi della radice** e **Oggetti a cui si fa riferimento** per l'elemento selezionato.

 ![Albero Heap gestito](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Albero Heap gestito")

L'albero **Heap gestito** di un report dettagli dello snapshot include le colonne seguenti:

|||
|-|-|
|**Tipo di oggetto**|Nome dell'istanza di tipo o di oggetto.|
|**Conteggio**|Numero di istanze di oggetto del tipo. Il valore di **Conteggio** è sempre 1 per un'istanza.|
|**Dimensioni (byte)**|Per un tipo, la dimensione di tutte le istanze del tipo nello snapshot meno la dimensione degli oggetti contenuti nelle istanze.<br /><br /> Per un'istanza, la dimensione dell'oggetto meno la dimensione degli oggetti contenuti nell'istanza. |
|**Dimensione inclusiva (byte)**|La dimensione delle istanze del tipo o di una singola istanza, inclusa la dimensione degli oggetti contenuti.|
|**Modulo**|Il modulo che contiene il costruttore.|

### <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Albero Percorsi della radice (report dettagli dello snapshot)
L'albero **Percorsi della radice** mostra la catena di oggetti che fanno riferimento a un tipo o a un'istanza. Garbage Collector di .NET Framework pulisce la memoria per un oggetto solo una volta rilasciati tutti i riferimenti.

Per un tipo nell'albero **Percorsi della radice**, il numero di oggetti che contengono riferimenti al tipo viene visualizzato nella colonna **Conteggio riferimenti**.

![Albero Percorsi della radice per i tipi](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "Albero Percorsi della radice per i tipi")

### <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Albero Tipi a cui si fa riferimento o Oggetti a cui si fa riferimento (report dettagli dello snapshot)
L'albero **Tipi a cui si fa riferimento** o **Oggetti a cui si fa riferimento** mostra gli oggetti a cui fa riferimento l'istanza o il tipo selezionato.

![Albero Oggetti a cui si fa riferimento per le istanze](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "Albero Oggetti a cui si fa riferimento per le istanze")

Un albero **Tipi a cui si fa riferimento** di un report dettagli dello snapshot include le colonne seguenti. Un albero **Oggetti a cui si fa riferimento** non comprende la colonna **Conteggio riferimenti**.

|||
|-|-|
|**Tipo di oggetto** o **Istanza**|Il nome del tipo o dell'istanza.|
|**Conteggio riferimenti**|Per i tipi, il numero di istanze di oggetto del tipo.|
|**Dimensioni (byte)**|Per un tipo, la dimensione di tutte le istanze del tipo, meno la dimensione degli oggetti contenuti nel tipo.<br /><br /> Per un'istanza, la dimensione dell'oggetto meno la dimensione degli oggetti contenuti nell'oggetto.|
|**Dimensione inclusiva (byte)**|La dimensione totale delle istanze del tipo o la dimensione dell'istanza, inclusa la dimensione degli oggetti contenuti.|
|**Modulo**|Il modulo che contiene il costruttore.|

## <a name="snapshot-difference-diff-reports"></a>Report delle differenze degli snapshot

Un report differenze degli snapshot mostra le differenze tra uno snapshot principale e lo snapshot precedente. Per aprire un report delle differenze, selezionare uno dei collegamenti differenza in un riquadro snapshot.

Entrambi i collegamenti aprono lo stesso report. L'unica differenza è il tipo di ordinamento iniziale dell'albero **Heap gestito** nel report. Il collegamento dimensione ordina il report in base alla colonna **Differenza dimensioni inclusive (byte)**. Il collegamento oggetti ordina il rapporto in base alla colonna **Diff. conteggio**. È possibile modificare il tipo o la colonna di ordinamento dopo l'apertura del report.

 ![Collegamenti al report delle differenze in un riquadro snapshot](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "Collegamenti al report delle differenze in un riquadro snapshot")

### <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Albero Heap gestito (report differenze degli snapshot)

 Nell'albero **Heap gestito** sono elencati i tipi di oggetti contenuti in memoria. Puoi espandere un nome di tipo per visualizzare le dieci istanze più grandi del tipo, ordinate in base alla dimensione. Selezionare un tipo o un'istanza per visualizzare gli alberi **Percorsi della radice** e **Oggetti a cui si fa riferimento** per l'elemento selezionato.

 ![Albero Heap gestito per un tipo nel report delle differenze](../profiling/media/memuse_snapshotdiff_type_heap.png "Albero Heap gestito per un tipo nel report delle differenze")

L'albero **Heap gestito** di un report differenze dello snapshot include le colonne seguenti:

|||
|-|-|
|**Tipo di oggetto**|Nome dell'istanza di tipo o di oggetto.|
|**Conteggio**|Numero di istanze di un tipo nello snapshot principale. Il valore di **Conteggio** è sempre 1 per un'istanza.|
|**Diff. conteggio**|Per un tipo, differenza nel numero di istanze del tipo tra lo snapshot principale e quello precedente. Il campo è vuoto per un'istanza.|
|**Dimensioni (byte)**|La dimensione degli oggetti nello snapshot principale, meno la dimensione degli oggetti negli oggetti. Per un tipo, **Dimensione (byte)** e **Dimensione inclusiva (byte)** corrispondono ai totali delle dimensioni delle istanze di tipo.|
|**Diff. dimensione totale (byte)**|Per un tipo, la differenza nella dimensione totale delle istanze del tipo tra lo snapshot principale e quello precedente, meno la dimensione degli oggetti nelle istanze. Il campo è vuoto per un'istanza.|
|**Dimensione inclusiva (byte)**|La dimensione degli oggetti nello snapshot principale, inclusa la dimensione degli oggetti negli oggetti.|
|**Differenza dimensioni inclusive (byte)**|Per un tipo, la differenza nella dimensione di tutte le istanze del tipo tra lo snapshot principale e quello precedente, inclusa la dimensione degli oggetti negli oggetti. Il campo è vuoto per un'istanza.|
|**Modulo**|Il modulo che contiene il costruttore.|

### <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Albero Percorsi della radice (report differenze degli snapshot)

L'albero **Percorsi della radice** mostra la catena di oggetti che fanno riferimento a un tipo o a un'istanza. Garbage Collector di .NET Framework pulisce la memoria per un oggetto solo una volta rilasciati tutti i riferimenti.

Per un tipo nell'albero **Percorsi della radice**, il numero di oggetti che contengono riferimenti al tipo viene visualizzato nella colonna **Conteggio riferimenti**. La differenza di numero rispetto allo snapshot precedente è indicata nella colonna **Diff. conteggio riferimenti**.

 ![Albero Percorsi della radice in un report delle differenze](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "Albero Percorsi della radice in un report delle differenze")

### <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Albero Tipi a cui si fa riferimento o Oggetti a cui si fa riferimento (report differenze degli snapshot)

L'albero **Tipi a cui si fa riferimento** o **Oggetti a cui si fa riferimento** mostra gli oggetti a cui fa riferimento l'istanza o il tipo selezionato.

![Tipi a cui si fa riferimento in un report delle differenze](../profiling/media/memuse_snapshotdiff_referencedtypes.png "Tipi a cui si fa riferimento in un report delle differenze")

Un albero **Tipi a cui si fa riferimento** di un report differenze dello snapshot include le colonne seguenti. Un albero **Oggetti a cui si fa riferimento** comprende le colonne **Istanza**, **Dimensione (byte)**, **Dimensione inclusiva (byte)** e **Modulo**.

|||
|-|-|
|**Tipo di oggetto** o **Istanza**|Nome dell'istanza di tipo o di oggetto.|
|**Conteggio riferimenti**|Numero di istanze di un tipo nello snapshot principale.|
|**Diff. conteggio riferimenti**|Per un tipo, differenza nel numero di istanze del tipo tra lo snapshot principale e quello precedente.|
|**Dimensioni (byte)**|La dimensione degli oggetti nello snapshot principale, meno la dimensione degli oggetti negli oggetti. Per un tipo, **Dimensione (byte)** e **Dimensione inclusiva (byte)** corrispondono ai totali delle dimensioni delle istanze di tipo.|
|**Diff. dimensione totale (byte)**|Per un tipo, la differenza nella dimensione totale delle istanze del tipo tra lo snapshot principale e quello precedente, meno la dimensione degli oggetti nelle istanze. |
|**Dimensione inclusiva (byte)**|La dimensione degli oggetti nello snapshot principale, inclusa la dimensione degli oggetti negli oggetti.|
|**Differenza dimensioni inclusive (byte)**|Per un tipo, la differenza nella dimensione di tutte le istanze del tipo tra lo snapshot principale e quello precedente, inclusa la dimensione degli oggetti negli oggetti.|
|**Modulo**|Il modulo che contiene il costruttore.|

## <a name="see-also"></a>Vedere anche
- [Memoria JavaScript](../profiling/javascript-memory.md)
- [Profilatura in Visual Studio](../profiling/index.md)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
- [Procedure consigliate per le prestazioni per app UWP scritte in C++, C# e Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Diagnosing memory issues with the new Memory Usage Tool in Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=394706) (Diagnostica dei problemi di memoria con il nuovo strumento Utilizzo memoria in Visual Studio)