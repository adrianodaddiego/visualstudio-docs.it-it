---
title: Quali sono le novità relative al Debugger di Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
ms.date: 01/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 9c6f2eb4be56be8cf5e25c3238a91819df3bc574
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901388"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Novità relative al debugger di Visual Studio 2017

Il debugger include queste nuove funzionalità:

- Novità della versione 15.5, il **Snapshot Debugger** crea uno snapshot delle App nell'ambiente di produzione quando viene eseguito codice che si è interessati. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

    La raccolta di snapshot è disponibile per le seguenti app Web in esecuzione in Servizio app di Azure:

  * Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
  * Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.

    Per altre informazioni, vedere [Debug live ASP.NET apps using the Snapshot Debugger](../debugger/debug-live-azure-applications.md) (Eseguire il debug di app ASP.NET attive usando Snapshot Debugger).

- Novità della versione 15.5 in Visual Studio Enterprise, solo **tornare indietro di IntelliTrace** crea automaticamente uno snapshot dell'applicazione in ogni punto di interruzione e il debugger di eventi di passaggio. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

    È possibile esplorare e visualizzare gli snapshot tramite i pulsanti **Vai indietro** e **Vai avanti** sulla barra degli strumenti di Debug. Questi pulsanti consentono di spostarsi tra gli eventi visualizzati nella scheda **Eventi** della finestra **Strumenti di diagnostica**.

    ![Pulsanti Passo indietro e Passo avanti](../debugger/media/intellitrace-step-back-icons-description.png  "Pulsanti Passo indietro e Passo avanti")

    Per altre informazioni, vedere la pagina [Visualizzare lo stato precedente dell'applicazione con IntelliTrace](../debugger/view-historical-application-state.md).

- Il **Helper eccezioni** sostituisce le informazioni sulle eccezioni e viene visualizzato in una finestra di dialogo non modale in cui si è verificato l'errore. Il **Helper eccezioni** fornisce un accesso più rapido per eventuali eccezioni interne, un'analisi aggiuntiva dal debugger (se disponibile) e accesso immediato al **impostazioni eccezioni** per l'eccezione. L'Helper eccezioni possono anche essere trascinata in una vista mobile se sta bloccando un elemento che si desidera vedere.

    Ad esempio, un **NullReferenceException** Mostra ora la variabile contenente il riferimento null (informazioni aggiuntive).

    ![Helper eccezioni del debugger](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Per altre informazioni, vedere il post del blog relativo all'[uso del nuovo supporto eccezione in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

- È ora possibile eseguire una riga di codice durante la pausa del debugger selezionando il **usare l'esecuzione a qui** icona della freccia verde (l'icona viene visualizzata al passaggio del mouse su una riga di codice). Ciò consente di eliminare la necessità di impostare punti di interruzione temporanei.

    ![Esecuzione del debugger a clic](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- È possibile impostare le condizioni per le eccezioni nel **impostazioni eccezioni** finestra di dialogo (tale scopo, è possibile utilizzare il **modifica condizione** icona nella finestra di dialogo Impostazioni eccezioni o tramite il menu di scelta rapida nel eccezione.) Attualmente sono supportati le condizioni includono i nomi di modulo da includere o escludere per l'eccezione.

    ![Le condizioni per un'eccezione](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Connetti a processo nella finestra di dialogo include una nuova funzionalità di ricerca che può identificare più rapidamente il processo che è necessario collegare a.

    ![Ricerca in Connetti a processo](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Per altre informazioni su queste nuove funzionalità, vedere la [note sulla versione per [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Vedere anche

- [Debug in Visual Studio](../debugger/index.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)