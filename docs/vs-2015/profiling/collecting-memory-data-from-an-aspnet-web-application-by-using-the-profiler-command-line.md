---
title: Raccolta di dati di memoria da un'applicazione Web ASP.NET tramite la riga di comando del profiler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f7c759d4c2c4760be6782a518f4cdf209e828d4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436786"
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Raccolta di dati di memoria da un'applicazione Web ASP.NET tramite la riga di comando del profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa sezione descrive le procedure e le opzioni per la raccolta di dati sull'allocazione della memoria e sulla durata degli oggetti per un'applicazione Web ASP.NET tramite lo strumento da riga di comando **VSPerfCmd**.  
  
> [!NOTE]
> Lo strumento **VSPerfCmd** consente l'accesso completo alle funzionalità degli strumenti di profilatura, tra cui la sospensione e la ripresa della profilatura e la raccolta di dati aggiuntivi dal processore e dai contatori delle prestazioni di Windows. Quando queste funzionalità non sono necessarie è anche possibile usare lo strumento da riga di comando **VSPerfASPNETCmd**. Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), non è necessario impostare variabili di ambiente né riavviare il computer. Per altre informazioni, vedere [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) (Profilatura rapida di un sito Web con VSPerfASPNETCmd).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Connettere il profiler a un'applicazione ASP.NET in esecuzione**|-   [Procedura: Connettere il profiler a un'applicazione Web ASP.NET per raccogliere dati di memoria](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentare file binari compilati in modo statico**|-   [Procedura: Instrumentare un'applicazione ASP.NET compilata in modo statico e raccogliere dati di memoria](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumentare file binari compilati in modo dinamico**|-   [Procedura: Instrumentare un'applicazione ASP.NET compilata in modo dinamico e raccogliere dati di memoria](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
### <a name="profiling-aspnet-web-applications"></a>Profilatura di applicazioni Web ASP.NET  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Sottoporre a profilatura tramite il metodo di strumentazione**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Sottoporre a profilatura i conflitti di risorse e le attività dei thread**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Profilatura di dati di memoria .NET Framework  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni client autonome**|-   [Raccolta di dati di memoria di .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura i servizi**|-   [Collecting .NET Memory Data](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) (Raccolta di dati di memoria .NET)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Analisi di visualizzazioni dati e di report di memoria .NET  
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Riferimenti  
 [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)
