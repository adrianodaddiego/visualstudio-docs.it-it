---
title: JavaScript e TypeScript in Visual Studio 2019
ms.date: 03/27/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 3000510c6bb6079629a3df05909417593569c932
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553255"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript e TypeScript in Visual Studio 2019

## <a name="overview"></a>Panoramica

Visual Studio 2019 offre supporto avanzato per lo sviluppo in JavaScript, sia usando JavaScript direttamente che tramite il [linguaggio di programmazione TypeScript](http://www.typescriptlang.org), che è stato sviluppato per offrire un'esperienza di sviluppo JavaScript più produttiva e piacevole, in particolare per lo sviluppo di progetti su larga scala. È possibile scrivere codice JavaScript o TypeScript in Visual Studio per molti tipi di applicazioni e servizi.

## <a name="javascript-language-service"></a>JavaScript Language Service

L'esperienza JavaScript in Visual Studio 2019 si basa sullo stesso motore che fornisce il supporto di TypeScript. Ciò consente supporto delle funzionalità, completezza e integrazione migliori, direttamente nella versione predefinita.

L'opzione per ripristinare il servizio di linguaggio JavaScript legacy non è più disponibile. Il servizio di linguaggio JavaScript è ora disponibile per impostazione predefinita. Il nuovo servizio di linguaggio si basa esclusivamente sul servizio di linguaggio TypeScript, supportato dall'analisi statica. Ciò consente di mettere a disposizione strumenti migliori, in modo che il codice JavaScript possa trarre vantaggio da un'esecuzione di IntelliSense più completa in base alle definizioni dei tipi. Il nuovo servizio è leggero e utilizza meno memoria rispetto al servizio legacy, offrendo agli utenti prestazioni migliori a seconda delle dimensioni del codice. Sono state anche migliorate le prestazioni del servizio di linguaggio per gestire progetti di grandi dimensioni.

## <a name="typescript-support"></a>Supporto di TypeScript

Visual Studio 2019 offre diverse opzioni per l'integrazione della compilazione TypeScript nel progetto:

* [Pacchetto NuGet di TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Quando si installa il pacchetto NuGet per TypeScript 3.2 o versione successiva nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.
* TypeScript SDK, disponibile per impostazione predefinita nel programma di installazione di Visual Studio, nonché come download dell'SDK autonomo da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).
* [Pacchetto npm di TypeScript](https://www.npmjs.com/package/typescript). Quando il pacchetto npm per TypeScript 2.1 o versione successiva è installato nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.

Per i progetti sviluppati in Visual Studio 2019, si consiglia di usare i pacchetti npm e NuGet di TypeScript per maggiore portabilità in piattaforme e ambienti e diversi.

## <a name="projects"></a>Progetti

Le app UWP JavaScript non sono più supportate in Visual Studio 2019. Non è possibile creare o aprire progetti UWP JavaScript (file con estensione *jsproj*). Per altre informazioni, vedere la documentazione sulla [ creazione delle app Web progressive](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/get-started) eseguite in modo corretto in Windows.
