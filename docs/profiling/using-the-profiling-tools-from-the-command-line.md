---
title: Uso degli strumenti per la profilatura dalla riga di comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 049e1163f54dfcdfe2338faa59ae8c37c3114fa7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422043"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Usare gli strumenti per la profilatura dalla riga di comando
È possibile usare gli strumenti da riga di comando degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire la profilatura di applicazioni dal prompt dei comandi e automatizzare la profilatura tramite file batch e script. È anche possibile generare file di report dal prompt dei comandi. È possibile usare il profiler autonomo leggero per raccogliere dati nei computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).

## <a name="common-tasks"></a>Attività comuni

| Attività | Contenuto correlato |
| - | - |
| **Impostare il percorso dei simboli:** per visualizzare i nomi di funzioni e parametri, il profiler deve avere accesso ai file di simboli (con estensione *pdb*) dei file binari sottoposti a profilatura. Questi file devono includere i file di simboli per il sistema operativo Microsoft e le applicazioni da visualizzare nell'analisi. È possibile usare il server di simboli pubblico di Microsoft per assicurarsi di disporre dei file con estensione *pdb* corretti per i file binari Microsoft. | -   [Procedura: Specificare percorsi dei file di simboli dalla riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Eseguire la profilatura dell'applicazione:** gli strumenti e le opzioni della riga di comando usati per la profilatura di un'applicazione di destinazione dipendono dal tipo di applicazione, dal metodo di profilatura e dal fatto che la destinazione sia un'applicazione gestita o nativa. | -   [Usare i metodi di profilatura dalla riga di comando](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md) |
| **Creare report con estensione xml e csv:** la profilatura al prompt dei comandi crea file di dati che possono essere visualizzati nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È anche possibile generare file di dati con estensione *xml* o con valori delimitati da virgole (con estensione *csv*) usando lo strumento da riga di comando VSPerfReport. | -   [Creare report del profiler dalla riga di comando](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Eseguire la profilatura del codice nei computer senza Visual Studio:** è possibile usare il profiler autonomo degli Strumenti di profilatura per raccogliere dati per le applicazioni nei computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. | -   [Procedura: Installare il profiler autonomo](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Riferimenti
- [Informazioni di riferimento sugli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Vedere anche
- [Esplora prestazioni](../profiling/performance-explorer.md)