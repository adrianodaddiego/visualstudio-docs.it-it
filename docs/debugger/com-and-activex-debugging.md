---
title: Debug di COM e ActiveX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- COM, debugging
- debugging ActiveX applications
- debugging [Visual Studio], COM
- debugging COM containers
- ActiveX controls, debugging
ms.assetid: 3260b2a7-3239-493d-9271-aedf705c13c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b37522fec0438278f8cf063637132b146b3d3748
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563907"
---
# <a name="com-and-activex-debugging"></a>Debug di COM e ActiveX
In questa sezione vengono forniti suggerimenti sul debug di applicazioni COM e di controlli ActiveX.

## <a name="in-this-section"></a>In questa sezione
 [Server COM e il contenitore debug](../debugger/com-server-and-container-debugging.md) vengono citate particolari considerazioni durante il debug di applicazioni COM. I problemi includono: debug di un server e di un contenitore COM tramite due progetti all'interno della stessa soluzione, traccia di chiamate che attraversano i limiti dei processi, impostazione di punti di interruzione in funzioni di callback ed esecuzione delle istruzioni attraverso e all'interno di contenitori e server.

 [Procedura: Eseguire il debug di un controllo ActiveX](../debugger/how-to-debug-an-activex-control.md) contiene informazioni sul debug dei controlli ActiveX. quali: specifica di un contenitore relativo alla sessione di debug per visualizzare come viene eseguito il codice nel controllo ActiveX, debug di un controllo ActiveX con associazione a dati, simulazione di un particolare contenitore ed esecuzione passo passo del codice del contenitore.

 [Strumenti di debug COM](../debugger/com-debugging-tools.md) Elenca visualizzatori e applicazioni di esempio che possono essere utile nel debug di applicazioni COM.

## <a name="related-sections"></a>Sezioni correlate
 [Presentazione di debugger](../debugger/debugger-feature-tour.md) vengono forniti collegamenti a sezioni più ampie della documentazione sul debug. Vengono fornite informazioni sui seguenti aspetti: novità del debugger, impostazione e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice gestito, debug di progetti Visual C++, debug di COM e ActiveX, debug di DLL, debug di SQL e riferimenti all'interfaccia utente.

## <a name="see-also"></a>Vedere anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Introduzione a COM](/cpp/atl/introduction-to-com)
- [Controlli ActiveX](/cpp/mfc/activex-controls)
- [Applicazioni server SDI](../debugger/sdi-server-applications.md)