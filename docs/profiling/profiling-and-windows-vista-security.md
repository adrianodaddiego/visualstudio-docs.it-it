---
title: Profilatura e sicurezza in Windows Vista | Microsoft Docs
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 091961f3425714c0dc5ddabfac847c76339ab064
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994947"
---
# <a name="profiling-and-windows-vista-security"></a>Profilatura e sicurezza in Windows Vista

A seconda delle impostazioni delle autorizzazioni di accesso utente di [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] rese disponibili dall'amministratore di un computer, un singolo utente potrebbe disporre dell'autorizzazione di sicurezza necessaria per profilare un processo in quel computer. Gli esempi seguenti illustrano le possibili differenze tra i diversi tipi di utenti:

- Se l'amministratore ha impostato l'avvio del driver e del servizio, alcuni utenti possono accedere a funzionalità di profilatura avanzate.

- Gli utenti di dominio possono accedere soltanto ad esempi di profilatura.

- Alcuni utenti possono negare l'accesso alla profilatura a tutti gli altri utenti.

  Per altre informazioni, vedere le opzioni ADMIN in [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilatura tra sessioni

La *profilatura tra sessioni* è una funzionalità per la profilatura di un processo eseguito in una sessione utente diversa. Ad esempio, la maggior parte dei servizi viene eseguita nella sessione 0 e gli utenti non possono effettuare esecuzioni direttamente nella sessione 0. Usando il pulsante **Associa a processo** nella barra degli strumenti di Esplora prestazioni o l'opzione `/attach` dello strumento della riga di comando VSPerfCmd, è possibile profilare la maggior parte dei processi in sessioni utente diverse.

È possibile visualizzare un elenco dei processi disponibili impostando le opzioni di visibilità relative alla profilatura tra processi. Queste opzioni sono disponibili nella finestra **Associa a processo** visualizzata quando si seleziona **Associa a processo**:

- **Mostra i processi di tutti gli utenti**

  Quando questa opzione non è selezionata, nell'elenco vengono visualizzati solo i processi di proprietà dell'utente corrente. Altrimenti l'elenco visualizza i processi di tutti gli utenti.

- **Mostra processi in tutte le sessioni**

  Quando questa opzione non è selezionata, nell'elenco vengono visualizzati i processi della sessione corrente. Altrimenti l'elenco visualizza i processi di tutte le sessioni.

## <a name="see-also"></a>Vedere anche

- [Panoramiche](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Procedura: Connettersi a un processo in esecuzione](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
