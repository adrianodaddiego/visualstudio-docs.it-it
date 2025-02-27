---
title: Controllo della versione di Team Foundation
description: Connessione a Team Foundation Server o ad Azure DevOps Services con il controllo della versione di Team Foundation.
author: conceptdev
ms.author: crdun
ms.date: 09/05/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 1d560e3fd383e3db19c664bf027470c8da224fd2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62987655"
---
# <a name="connecting-to-team-foundation-version-control"></a>Connessione al controllo della versione di Team Foundation

> [!NOTE]
> Il supporto del controllo della versione di Team Foundation è attualmente in anteprima e alcune funzionalità non sono ancora completamente operative. Inviare il proprio feedback su eventuali problemi riscontrati alla [community degli sviluppatori](https://developercommunity.visualstudio.com/spaces/41/index.html). Presto saranno disponibili altre modifiche.

Azure Repos offre due modelli di controllo della versione: Git, un controllo della versione distribuito, e il controllo della versione di Team Foundation, un controllo della versione centralizzato. Questo articolo offre una panoramica del controllo della versione di Team Foundation con Visual Studio per Mac e rappresenta un punto di partenza per l'uso di questo strumento.

## <a name="requirements"></a>Requisiti

* Visual Studio Community, Professional o Enterprise per Mac versione 7.5 o successiva.
* Azure DevOps Services o Team Foundation Server 2013 e versioni successive.
* Un progetto in Azure DevOps Services o Team Foundation Server configurato per l'uso del controllo della versione di Team Foundation.

## <a name="installation"></a>Installazione

In Visual Studio per Mac scegliere **Visual Studio > Estensioni** dal menu. Nella scheda **Raccolta** selezionare **Controllo della versione > Controllo della versione di Team Foundation per TFS e VSTS** e fare clic su **Installa**:

![Gestione estensioni](media/tfvc-install.png)

Seguire i prompt per installare l'estensione. Al termine dell'installazione, riavviare l'IDE.

## <a name="updating-the-extension"></a>Aggiornamento dell'estensione

Periodicamente vengono rilasciati aggiornamenti per l'estensione TFVC. Per accedere agli aggiornamenti, scegliere **Visual Studio > Estensioni...**  dal menu e selezionare la scheda **Aggiornamenti**. Selezionare l'estensione nell'elenco e premere il pulsante **Aggiorna**:

![Visualizzazione dell'aggiornamento in Gestione estensioni](media/tfvc-update.png)

Scegliere **Installa** nella finestra di dialogo successiva per disinstallare il pacchetto precedente e installare quello nuovo.

## <a name="using-the-add-in"></a>Uso del componente aggiuntivo

Dopo aver installato l'estensione, selezionare la voce di menu **Version Control > TFS/Azure DevOps > Open from Remote Repository** (Controllo della versione > TFS/Azure DevOps > Apri da repository remoto).

![Voce di menu per aprire l'estensione](media/tfvc-source-control-explorer-devops.png)

Scegliere VSTS o Team Foundation Server per iniziare e premere **Continue** (Continua):

![Connettersi con un server](media/tfvc-choose-server-type-devops.png)

### <a name="azure-repos-authentication"></a>Autenticazione Azure Repos

Quando si seleziona un progetto ospitato in Azure Repos, viene richiesto di immettere i dati dell'account Microsoft:

![Connettersi con Azure Repos](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>Autenticazione TFS

Per connettersi a TFS, immettere i dettagli del server e le credenziali dell'account. Immettere un dominio per usare l'autenticazione NTLM oppure lasciare il campo vuoto per usare l'autenticazione di base. Selezionare **Aggiungi server**:

![Accedere a un server TFS](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Selezione di un progetto

Dopo aver eseguito l'autenticazione, è possibile visualizzare un elenco dei repository associati all'account nella finestra di dialogo **Apri dal controllo del codice sorgente**:

![Finestra di dialogo Apri dal controllo del codice sorgente con progetti visualizzati](media/tfvc-vsts-projects.png)

Questa finestra di dialogo è suddivisa nei nodi seguenti:

- Organizzazione o raccolta di Azure DevOps: vengono visualizzate tutte le organizzazioni connesse all'account Microsoft usato per eseguire l'accesso.
- Progetti: ogni organizzazione o raccolta può contenere una serie di progetti. Il progetto è la posizione in cui sono ospitati il codice sorgente, gli elementi di lavoro e le compilazioni automatiche.

È possibile eseguire ricerche e applicare filtri in base al nome di un progetto o di un'organizzazione.

### <a name="adding-a-new-server"></a>Aggiunta di un nuovo server

Per aggiungere un nuovo server all'elenco, scegliere il pulsante **Aggiungi host** nella finestra di dialogo **Apri dal controllo del codice sorgente**:

![Pulsante Aggiungi per l'aggiunta di un nuovo server all'elenco](media/tfvc-add-new-server.png)

Selezionare il provider dall'elenco e immettere le credenziali:

![Finestra di dialogo con l'opzione per il provider del controllo del codice sorgente](media/tfvc-add-new-creds-devops.png)

## <a name="creating-a-new-workspace"></a>Creazione di una nuova area di lavoro

Per iniziare a lavorare con un progetto, è necessaria un'_area di lavoro_. Se non è già disponibile un'area di lavoro, è possibile crearne una dalla casella combinata **Area di lavoro** nella finestra di dialogo **Apri dal controllo del codice sorgente**:

![Creare una nuova opzione di casella combinata dell'area di lavoro](media/tfvc-create-new-workspace.png)

Impostare il nome e il percorso locale per la nuova area di lavoro e selezionare **Crea area di lavoro**:

![Immettere un nome e un percorso locale per la nuova area di lavoro](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Uso di Esplora controllo codice sorgente

Dopo aver creato un'area di lavoro e aver eseguito il mapping del progetto, è possibile iniziare a usare _Esplora controllo codice sorgente_.

Per aprire Esplora controllo codice sorgente, selezionare **Controllo della versione > TFS/Azure DevOps > Esplora controllo codice sorgente**.

Esplora controllo codice sorgente consente di esplorare tutti i progetti mappati e i relativi file e cartelle. Consente anche di eseguire tutte le azioni di base per il controllo del codice sorgente, ad esempio:

- Ottenere la versione più recente
- Ottenere una versione specifica
- Archiviare ed estrarre file
- Bloccare e sbloccare i file
- Aggiungere, eliminare e rinominare i file
- Visualizza cronologia
- Confronto delle modifiche.

Molte di queste azioni sono disponibili tramite i menu di scelta rapida del progetto:

![Azioni dei menu di scelta rapida di un progetto](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>Gestione delle aree di lavoro

Se non è ancora stata creata un'area di lavoro, come descritto nella sezione [Creazione di una nuova area di lavoro](#creating-a-new-workspace), Esplora controllo codice sorgente è vuoto:

![Esplora controllo codice sorgente vuoto](media/tfvc-setup-empty-sce.png)

Per configurare il progetto remoto con un'area di lavoro locale, seguire questa procedura:

1. Selezionare il **Server** dalla casella combinata.
1. Si noti che non sono presenti aree di lavoro e che il percorso locale non è mappato. Selezionare il collegamento **Non mappato** per visualizzare la finestra di dialogo **Crea nuova area di lavoro**.
1. Specificare un nome per l'area di lavoro e quindi fare clic su **Aggiungi Cartella di lavoro**  per eseguire il mapping del progetto in una cartella locale nel computer:

    ![Creare una nuova finestra dell'area di lavoro con le opzioni predefinite](media/tfvc-workspace1.png)

1. Selezionare la cartella "$" per eseguire il mapping di tutti i progetti del server alla stessa area di lavoro o selezionare un singolo progetto e fare clic su **OK**:

    ![Finestra di dialogo Cerca cartella con tutti i progetti visualizzati](media/tfvc-workspace2.png)

1. Selezionare il percorso del computer locale a cui si vuole mappare il progetto o i progetti e fare clic su **Seleziona cartella**.
1. Confermare i dettagli della nuova area di lavoro scegliendo **OK**

    ![Creare una nuova finestra dell'area di lavoro con la cartella di lavoro aggiunta](media/tfvc-workspace3.png)

Dopo aver configurato l'area di lavoro, è possibile modificarla o rimuoverla facendo clic sul pulsante **Gestisci aree di lavoro** in Esplora controllo codice sorgente.

![Gestisci aree di lavoro](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="problems-using-basic-authentication"></a>Problemi relativi all'uso dell'autenticazione di base

Le opzioni seguenti possono essere usate eseguire l'autenticazione in un server:

- Oauth
- Basic
- Ntlm

Per usare l'autenticazione di base è necessario abilitare le **credenziali di autenticazione alternative** in Azure DevOps Services seguendo questa procedura:

1. Accedere all'organizzazione di Azure DevOps come proprietario (https://dev.azure.com/{organization}/{project}).

2. Dalla barra degli strumenti dell'organizzazione selezionare l'icona a forma di ingranaggio, quindi **Policy** (Criteri):

    ![Opzione delle impostazioni dei criteri selezionata](media/tfvc-auth2.png)

3. Verificare le impostazioni di connessione dell'applicazione. Modificare queste impostazioni in base ai propri criteri di sicurezza:

    ![Opzione delle impostazioni dei criteri selezionata](media/tfvc-auth.png)

### <a name="i-do-not-see-anything-in-tfvc"></a>Nel controllo della versione di Team Foundation non viene visualizzato nulla

Per configurare il controllo della versione di Team Foundation nel computer di sviluppo, **è necessario** creare un'area di lavoro, come descritto nella sezione [Gestione delle aree di lavoro](#managing-workspaces).

In Esplora controllo codice sorgente premere il pulsante **Gestisci aree di lavoro**. Seguire la procedura per eseguire il mapping del progetto team a una cartella sul computer di sviluppo.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Non viene visualizzato alcun progetto

Dopo l'autenticazione viene visualizzato l'elenco dei progetti. Per impostazione predefinita, vengono visualizzati solo i progetti Team Foundation Server. Per visualizzare altri tipi di progetti, selezionare la casella "See all projects" (Visualizza tutti i progetti).

Tenere presente che i progetti contenuti nel server non verranno visualizzati se non si hanno i privilegi corretti.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Viene visualizzato l'errore "Cannot create the workspace. Please, try again" (Impossibile creare l'area di lavoro. Riprovare.)

Quando si tenta di [creare una nuova area di lavoro](#creating-a-new-workspace), verificare che siano soddisfatte le condizioni seguenti:

- Il nome dell'area di lavoro non deve contenere caratteri non validi.
- Il nome deve essere composto da un massimo di 64 caratteri.
- Il percorso locale non può essere usato da altre aree di lavoro.

## <a name="see-also"></a>Vedere anche

- [Sviluppare e condividere il codice in TFVC usando Visual Studio (in Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)