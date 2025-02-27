---
title: Aggiornare Visual Studio
titleSuffix: ''
description: Informazioni sulla procedura dettagliata di aggiornamento di Visual Studio alla versione più recente.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e1fbc0bf5412888f246a1f396b146780013b6c6
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263058"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Aggiornare Visual Studio alla versione più recente

::: moniker range="vs-2017"

Si consiglia di eseguire l'aggiornamento alla [versione più recente](/visualstudio/releasenotes/vs2017-relnotes/) di Visual Studio 2017, in modo da avere sempre a disposizione le funzionalità, le correzioni e i miglioramenti più recenti.

Se si vuole provare la prossima versione, è anche possibile scaricare la [versione finale candidata](/visualstudio/releases/2019/release-notes/) di Visual Studio 2019.

> [!IMPORTANT]
> Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Aggiornare Visual Studio per Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Eseguire l'aggiornamento a Visual Studio 2017 versione 15.6 o successiva

L'esperienza di installazione e aggiornamento è stata migliorata per semplificarne l'uso direttamente dall'interno dell'IDE. Di seguito viene illustrato come eseguire l'aggiornamento dalla versione 15.6 e versioni successive alle versioni più recenti di Visual Studio.

### <a name="using-the-notifications-hub"></a>Uso dell'hub Notifiche

Quando è disponibile un aggiornamento, in Visual Studio viene visualizzato un flag di notifica corrispondente.

1. Salvare il lavoro.

1. Scegliere il flag di notifica per aprire l'hub **Notifiche** e quindi scegliere l'aggiornamento che si vuole installare.

   ![Aggiornare Visual Studio 2017 tramite l'hub Notifiche](media/vs-install-notifications-hub-15dot6.png "Hub Notifiche in Visual Studio 2017")

      > [!TIP]
      > Un aggiornamento per un'edizione di Visual Studio 2017 è cumulativo, quindi scegliere sempre di installare quello con il numero di versione più recente.

1. Quando viene visualizzata la finestra di dialogo **Aggiorna** scegliere **Aggiorna adesso**.

    ![Aggiornare Visual Studio 2017 tramite la finestra di dialogo Aggiorna dall'hub Notifiche](media/vs-update-now-from-notifications-hub.png "Finestra di dialogo Aggiorna dall'hub Notifiche in Visual Studio")

     Se si apre una finestra di dialogo di controllo dell'accesso utente, scegliere **Sì**. È possibile che venga visualizzata brevemente una finestra di dialogo "Attendere" e quindi viene aperto il programma di installazione di Visual Studio per avviare l'aggiornamento.

     ![Nuova esperienza del programma di installazione di Visual Studio nella versione 15.6](media/visual-studio-15dot6-installer.png "Nuova esperienza del programma di installazione di Visual Studio nella versione 15.6")

     L'aggiornamento continua. Al termine, verrà riavviato Visual Studio.

     > [!NOTE]
     > Quando si esegue Visual Studio in modalità amministratore, dopo l'aggiornamento è necessario riavviare manualmente Visual Studio.

### <a name="using-the-ide"></a>Utilizzo di IDE

È possibile verificare la disponibilità di un aggiornamento e quindi installarlo dalla barra dei menu in Visual Studio.

1. Salvare il lavoro.

1. Scegliere **Guida** > **Controlla la disponibilità di aggiornamenti**.

     ![Nuovo menu della Guida in Visual Studio versione 15.6](media/vs-help-menu-check-for-updates.png "Nuovo menu della Guida in Visual Studio versione 15.6")

1. Quando viene visualizzata la finestra di dialogo **Aggiorna** scegliere **Aggiorna adesso**.

   L'aggiornamento procede come descritto nella sezione precedente e Visual Studio viene riavviato dopo il corretto completamento dell'aggiornamento.

   > [!NOTE]
   > Quando si esegue Visual Studio in modalità amministratore, dopo l'aggiornamento è necessario riavviare manualmente Visual Studio.

### <a name="using-the-visual-studio-installer"></a>Uso del programma di installazione di Visual Studio

Come nelle versioni precedenti di Visual Studio, è possibile usare il programma di installazione di Visual Studio per installare un aggiornamento.

1. Salvare il lavoro.

1. Aprire il programma di installazione. Il programma di installazione di Visual Studio potrebbe richiedere l'aggiornamento prima di continuare.

   > [!NOTE]
   > In un computer che esegue Windows 10, il programma di installazione si trova sotto la lettera **V** come il **Programma di installazione di Visual Studio** o sotto la lettera **M** come il **Programma di installazione di Microsoft Visual Studio**.

1. Nella pagina **Prodotto** del programma di installazione cercare l'edizione di Visual Studio installata.

1. Se è disponibile un aggiornamento, viene visualizzato un pulsante **Aggiorna**. La verifica della disponibilità di un aggiornamento potrebbe richiedere alcuni secondi.

   Scegliere il pulsante **Aggiorna** per installare gli aggiornamenti.

     ![Aggiornare Visual Studio 2017 tramite il programma di installazione di Visual Studio](media/update-visual-studio.png "Aggiornare Visual Studio 2017 tramite il programma di installazione di Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aggiornare Visual Studio 2017 versione 15.5 o versioni precedenti

Se si usa una versione precedente, di seguito viene descritto come eseguire l'aggiornamento da Visual Studio 2017 versione 15.0 fino alla versione 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Eseguire gli aggiornamenti tramite l'hub Notifiche

1. Quando sono disponibili aggiornamenti, in Visual Studio viene visualizzato un flag di notifica corrispondente.

   ![Aggiornare Visual Studio 2017 tramite l'hub di notifica](media/notification-flag.png "Flag di notifica aggiornamento in Visual Studio")

   Scegliere il flag di notifica per aprire l'hub **di notifica**.

   ![Aggiornare Visual Studio 2017 tramite l'hub Notifiche](media/notifications-hub.png "Hub Notifiche in Visual Studio")

      > [!TIP]
      > Un aggiornamento per un'edizione di Visual Studio 2017 è cumulativo, quindi scegliere sempre di installare quello con il numero di versione più recente.

1. Scegliere **"Visual Studio Update" è disponibile**. Verrà aperta la finestra di dialogo **Estensioni e aggiornamenti**.

   ![Aggiornare Visual Studio 2017 tramite l'hub Notifiche](media/notifications-hub-select.png "Hub Notifiche in Visual Studio")

1. Nella finestra di dialogo **Estensioni e aggiornamenti** scegliere il pulsante **Aggiorna**.

   ![Aggiornare Visual Studio 2017 tramite l'hub Notifiche](media/notifications-extensions-and-updates.png "Finestra di dialogo Estensioni e aggiornamenti in Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Altre informazioni sulle notifiche di Visual Studio

Visual Studio invia una notifica all'utente quando è disponibile un aggiornamento di Visual Studio stesso o di uno o più componenti, nonché quando si verificano eventi specifici nell'ambiente di Visual Studio.

* Se il flag di notifica è giallo, un aggiornamento del prodotto Visual Studio è disponibile per l'installazione.
* Se il flag di notifica è rosso, la licenza presenta un problema.
* Se il flag di notifica è nero, sono presenti messaggi informativi o facoltativi.

Scegliere il flag di notifica per aprire l'hub di **notifica** e quindi scegliere le notifiche su cui si vuole agire. In alternativa, è possibile scegliere di ignorare o eliminare una notifica.

 ![Visualizzare un messaggio informativo o facoltativo nell'hub di notifica](media/notification-flag-optional.png "Flag di notifica di messaggi informativi o facoltativi in Visual Studio")

Se si sceglie di ignorare una notifica, questa non viene più visualizzata da Visual Studio. Se si vuole reimpostare l'elenco delle notifiche ignorate, scegliere il pulsante **Impostazioni** nell'hub Notifiche.

   ![Scegliere il pulsante Impostazioni nell'hub di notifica per visualizzare le opzioni di notifica](media/vs-notifications-hub-settings-button.png "Scegliere il pulsante Impostazioni nell'hub di notifica per visualizzare le opzioni di notifica")

### <a name="update-by-using-the-visual-studio-installer"></a>Eseguire gli aggiornamenti tramite il programma di installazione di Visual Studio

1. Aprire il programma di installazione. Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In tal caso, viene richiesto di effettuare questa operazione.

   > [!NOTE]
   > In un computer che esegue Windows 10, il programma di installazione si trova sotto la lettera **V** come il **Programma di installazione di Visual Studio** o sotto la lettera **M** come il **Programma di installazione di Microsoft Visual Studio**.

1. Nella pagina **Prodotto** del programma di installazione cercare l'edizione di Visual Studio installata.

1. Se è disponibile un aggiornamento, viene visualizzato un pulsante **Aggiorna**. La verifica della disponibilità di un aggiornamento potrebbe richiedere alcuni secondi.

   Scegliere il pulsante **Aggiorna** per installare gli aggiornamenti.

     ![Aggiornare Visual Studio 2017 tramite il programma di installazione di Visual Studio](media/update-visual-studio.png "Aggiornare Visual Studio tramite il programma di installazione di Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

È consigliabile eseguire l'aggiornamento alla [versione più recente](/visualstudio/releases/2019/release-notes/) di Visual Studio 2019, in modo da avere sempre a disposizione le funzionalità, le correzioni e i miglioramenti più recenti.

> [!IMPORTANT]
> Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Aggiornare Visual Studio per Mac](/visualstudio/mac/update).

Di seguito viene illustrato come aggiornare Visual&nbsp;Studio&nbsp;2019&nbsp;Preview o Visual&nbsp;Studio&nbsp;2019&nbsp;RC.

## <a name="use-the-visual-studio-installer"></a>Usare il programma di installazione di Visual Studio

1. Aprire il programma di installazione.

     ![Aprire il programma di installazione di Visual Studio](media/vs2019-visual-studio-installer.png "Aprire il programma di installazione di Visual Studio")

   Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata.

   Se ad esempio è stato precedentemente installato Visual&nbsp;Studio Community&nbsp;2019&nbsp;RC ed è disponibile un aggiornamento, nel programma di installazione verrà visualizzato un messaggio **Aggiornamento disponibile**.

     ![Selezionare l'edizione di Visual Studio 2019 che si vuole aggiornare](media/vs2019-update-visual-studio-community-rc.png "Selezionare l'edizione di Visual Studio 2019 che si vuole aggiornare")

1. Scegliere **Aggiorna** per installare gli aggiornamenti.

    ![Selezionare il pulsante Aggiorna per installare gli aggiornamenti](media/vs2019-choose-update-visual-studio-community-rc.png "Selezionare il pulsante Aggiorna per installare gli aggiornamenti")

1. Dopo aver completato l'aggiornamento scegliere **Avvia** per avviare Visual Studio.

    ![Selezionare il pulsante Avvia per avviare Visual Studio](media/vs2019-choose-launch-visual-studio-community-rc.png "Selezionare il pulsante Avvia per avviare Visual Studio")

## <a name="use-the-ide"></a>Usare l'IDE

È possibile verificare la disponibilità di un aggiornamento e quindi installarlo dalla barra dei menu o dalla casella di ricerca in Visual Studio 2019.

### <a name="open-visual-studio"></a>Aprire Visual Studio

1. Dal menu **Start** di Windows scegliere **Visual Studio 2019**.

    ![Aprire Visual Studio 2019 RC](media/vs2019-visual-studio-rc.png "Aprire Visual Studio 2019 da Windows")

1. Sotto **Inizia** scegliere un'opzione qualsiasi per aprire l'IDE.

    ![Aprire il programma di installazione di Visual Studio](media/vs2019-choose-option-from-get-started.png "Aprire il programma di installazione di Visual Studio")

    Viene aperto Visual Studio. Nell'IDE viene visualizzato un messaggio **Aggiornamento Visual Studio 2019**.

    ![Messaggio "Aggiornamento Visual Studio 2019" nell'IDE](media/vs2019-update-visual-studio-ide-message.png "Messaggio \"Aggiornamento Visual Studio 2019\" nell'IDE")

1. Nel messaggio **Aggiornamento Visual Studio 2019** scegliere **Visualizza dettagli**.

   ![Scegliere il pulsante Visualizza dettagli nel messaggio Aggiornamento Visual Studio 2019 dell'IDE](media/vs2019-update-visual-studio-ide-view-details.png "Scegliere il pulsante Visualizza dettagli nel messaggio Aggiornamento Visual Studio 2019")

1. Nella finestra di dialogo **Aggiornamento scaricato e pronto per l'installazione** scegliere **Aggiorna**.

     ![Scegliere il pulsante Aggiorna nella finestra di dialogo "Aggiornamento scaricato e pronto per l'installazione"](media/vs2019-update-visual-studio-community-rc-from-ide.png "Scegliere il pulsante Aggiorna nella finestra di dialogo \"Aggiornamento scaricato e pronto per l'installazione\"")

   Visual Studio viene aggiornato, chiuso e quindi riaperto.

### <a name="in-visual-studio"></a>In Visual Studio

1. Dalla barra dei menu scegliere **?** e quindi scegliere **Controlla aggiornamenti**.

     ![Scegliere 'Controlla aggiornamenti' dal menu ?](media/vs-2019/vs-ide-check-updates-help-menu.png "Scegliere 'Controlla aggiornamenti' dal menu ?")

    > [!NOTE]
    > È anche possibile usare la casella di ricerca nell'IDE per controllare se sono disponibili aggiornamenti. Premere **CTRL**+**Q**, digitare "controlla aggiornamenti" e quindi scegliere il risultato di ricerca corrispondente.

1. Nella finestra di dialogo **Aggiornamento scaricato e pronto per l'installazione** scegliere **Aggiorna**.

     ![Scegliere il pulsante Aggiorna nella finestra di dialogo "Aggiornamento scaricato e pronto per l'installazione"](media/vs2019-update-visual-studio-community-rc-from-ide.png "Scegliere il pulsante Aggiorna nella finestra di dialogo \"Aggiornamento scaricato e pronto per l'installazione\"")

   Visual Studio viene aggiornato, chiuso e quindi riaperto.

## <a name="use-the-notifications-hub"></a>Usare l'hub Notifiche

1. In Visual Studio salvare il lavoro.

1. Scegliere l'icona di notifica nell'angolo in basso a destra dell'IDE di Visual Studio per aprire l'hub **Notifiche**.

   ![Icona di notifica nell'IDE di Visual Studio](media/vs-2019/notification-bar.png "Icona di notifica nell'IDE di Visual Studio")

1. Nell'**hub Notifiche** scegliere l'aggiornamento che si vuole installare e quindi scegliere **Visualizza dettagli**.

     ![Hub Notifiche in Visual Studio 2019](media/vs-2019/notification-hub-update.png "Hub Notifiche in Visual Studio 2019")

      > [!TIP]
      > Un aggiornamento per un'edizione di Visual Studio 2019 è cumulativo, quindi scegliere sempre di installare quello con il numero di versione più recente.

1. Nella finestra di dialogo **Aggiornamento scaricato e pronto per l'installazione** scegliere **Aggiorna**.

   Visual Studio viene aggiornato, chiuso e quindi riaperto.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aggiornare Visual Studio per Mac](/visualstudio/mac/update)
* [Modificare Visual Studio](modify-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
