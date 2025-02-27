---
title: Raccolta di dati di intervallo dettagliati per un'applicazione Web ASP.NET usando il metodo di strumentazione del profiler tramite la riga di comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 79e8ad7842070d13941ad921ccb25ba502209eb0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405950"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Raccogliere dati di intervallo dettagliati per un'applicazione Web ASP.NET usando il metodo di strumentazione del profiler tramite la riga di comando
Questa sezione descrive le procedure e le opzioni per la raccolta di dati dettagliati sulle prestazioni per un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando lo strumento della riga di comando **VSPerfCmd** e il metodo di strumentazione.

> [!NOTE]
> Lo strumento **VSPerfCmd** consente l'accesso completo alle funzionalità degli strumenti di profilatura, tra cui la sospensione e la ripresa della profilatura e la raccolta di dati aggiuntivi dal processore e dai contatori delle prestazioni di Windows. Quando queste funzionalità non sono necessarie è anche possibile usare lo strumento da riga di comando **VSPerfASPNETCmd**. Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), non è necessario impostare variabili di ambiente e non è richiesto il riavvio del computer. Per altre informazioni, vedere [Profilatura rapida di sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Profilare file binari compilati in modo statico**|-   [Procedura: Instrumentare un'applicazione ASP.NET compilata in modo statico e raccogliere dati di intervallo dettagliati](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Profilare file binari compilati in modo dinamico**|-   [Procedura: Instrumentare un'applicazione ASP.NET compilata in modo dinamico e raccogliere dati di intervallo dettagliati](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Attività correlate

### <a name="profile-aspnet-web-applications"></a>Sottoporre a profilatura applicazioni Web ASP.NET

|Attività|Contenuto correlato|
|----------|---------------------|
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilatura dell'allocazione di memoria e garbage collection**|-   [Raccogliere dati di memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Sottoporre a profilatura i conflitti di risorse e le attività dei thread**|-   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Profilare usando il metodo di strumentazione

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni client autonome**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Sottoporre a profilatura i servizi**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Analizzare visualizzazioni dati e report di strumentazione
- [Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)