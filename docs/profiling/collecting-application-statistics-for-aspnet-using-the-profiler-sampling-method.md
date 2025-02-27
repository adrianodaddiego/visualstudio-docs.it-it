---
title: Raccogliere statistiche per le app Web ASP.NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 6ff7f1596d9b3336cb7fdbc02de7d1bc10172f94
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405757"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Raccogliere statistiche per le app Web ASP.NET

Questa sezione descrive le procedure e le opzioni per la raccolta di statistiche sulle prestazioni per un'applicazione Web ASP.NET tramite gli strumenti da riga di comando **VSPerfASPNETCmd** e **VSPerfCmd** e il metodo di profilatura del campionamento.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).

> [!NOTE]
> Anche se lo strumento **VSPerfCmd** consente l'accesso completo alle funzionalità degli strumenti di profilatura che consentono la sospensione e la ripresa della profilatura e la raccolta di dati aggiuntivi dal processore e dai contatori delle prestazioni di Windows, quando queste funzionalità non sono necessarie è consigliabile usare lo strumento da riga di comando **VSPerfASPNETCmd**. Lo strumento da riga di comando **VSPerfASPNETCmd** è il metodo preferito per la profilatura di siti Web ASP.NET tramite il profiler autonomo. Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), non è necessario impostare variabili di ambiente né riavviare il computer. Per altre informazioni, vedere [Profilatura rapida di sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Connettere il profiler a un'applicazione ASP.NET**|-   [Procedura: Connettere il profiler a un'applicazione Web ASP.NET per raccogliere statistiche sull'applicazione tramite la riga di comando](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Attività correlate

### <a name="profile-aspnet-web-applications"></a>Sottoporre a profilatura applicazioni Web ASP.NET

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura tramite il metodo di strumentazione**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profilatura dell'allocazione di memoria e garbage collection**|-   [Raccogliere dati di memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Sottoporre a profilatura i conflitti di risorse e le attività dei thread**|-   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Metodo di campionamento

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni client autonome**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Sottoporre a profilatura i servizi**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizzare visualizzazioni dati e report di campionamento
- [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)