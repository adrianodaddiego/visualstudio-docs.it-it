---
title: Uso di regole per le prestazioni per analizzare dati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2032100e03ae36e991d724a009e1fdcd485dda54
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422160"
---
# <a name="use-performance-rules-to-analyze-data"></a>Usare le regole per le prestazioni per analizzare dati
Gli avvisi di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] segnalano i problemi che possono rallentare l'esecuzione di un'applicazione sottoposta a profilatura. Gli avvisi possono anche indicare che potrebbe essere necessario modificare i metodi di raccolta per raccogliere dati più utili. Gli avvisi di prestazioni sono generati automaticamente in una sessione di profilatura. Gli avvisi vengono visualizzati nella finestra **Elenco errori** quando viene aperto un file di dati di profilatura in Visual Studio. Dalla finestra **Elenco errori** è possibile individuare il codice sorgente del problema e visualizzare informazioni dettagliate sull'errore, ad esempio informazioni su come risolvere il problema. È inoltre possibile disabilitare gli avvisi a cui non si è interessati.

> [!NOTE]
> Gli avvisi di prestazioni del profiler vengono generati dall'analisi dinamica dell'esecuzione del programma e sono indipendenti dagli avvisi di Analisi codice. Analisi codice può inoltre generare avvisi di prestazioni per il codice gestito in base all'analisi statica del codice sorgente. Per altre informazioni, vedere [Analisi della qualità del codice gestito](/visualstudio/code-quality/code-analysis-for-managed-code-overview) e [Avvisi di prestazioni](../code-quality/performance-warnings.md).

## <a name="in-this-section"></a>Contenuto della sezione
- [Procedura: Visualizzare gli avvisi di prestazioni](../profiling/how-to-view-performance-warnings.md)

 Fornisce informazioni su come aprire la finestra **Elenco errori** per visualizzare gli avvisi di prestazioni del profiler.

- [Procedura: Configurare le regole di prestazioni](../profiling/how-to-configure-performance-rules.md)

 Fornisce informazioni su come attivare o disattivare i singoli avvisi di prestazioni.

- [Tabella di riferimento delle regole di prestazioni](../profiling/performance-rules-reference.md)

 Fornisce informazioni dettagliate sugli avvisi di prestazioni del profiler.