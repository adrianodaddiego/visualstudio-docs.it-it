---
title: 'Procedura: Raccogliere dati ETW (Event Tracing for Windows) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9734c75f078380649009d10da13ed8c926e5e16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973864"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Procedura: Raccogliere dati ETW (Event Tracing for Windows)

Event Tracing for Windows (ETW) è un'efficace funzionalità di traccia a livello di kernel che consente al profiler di registrare eventi definiti dall'applicazione o dal kernel. I dati raccolti dal provider di eventi possono essere visualizzati solo tramite l'opzione /**Summary:ETW** dello strumento da riga di comando [VSPerfReport](../profiling/vsperfreport.md). Questo rapporto può essere usato per determinare i punti nell'applicazione in cui si verificano problemi di prestazioni.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).

## <a name="to-enable-event-trace-providers"></a>Per abilitare i provider di traccia eventi

1. In **Esplora prestazioni**fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.

2. In **Pagine delle proprietà** fare clic sulle proprietà di **Eventi Windows**.

3. Dall'elenco **Selezionare i provider di traccia eventi per raccogliere dati da** selezionare i provider di eventi da usare per la profilatura dell'applicazione.

## <a name="see-also"></a>Vedere anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)