---
title: Contenitori R e Docker
description: Come configurare i contenitori Docker per R e connettersi a tali contenitori con Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c5b4278ab50aac96703f03e74c014d29831f22e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810182"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Usare i contenitori Docker con R Tools per Visual Studio

R Tools per Visual Studio (RTVS) versione 1.3+, insieme a un'installazione di [Docker per Windows](https://www.docker.com/docker-windows), supportano l'utilizzo di contenitori Docker.

## <a name="create-a-container"></a>Creare un contenitore

1. Selezionare il pulsante **Contenitori** nell'angolo destro della finestra **Aree di lavoro** (**R Tools** > **Finestre** > **Aree di lavoro**). La finestra segnala se Docker per Windows non è installato e offre un collegamento per il download. L'installazione di Docker potrebbe richiedere il riavvio del computer.

    ![Finestra Aree di lavoro in R Tools per Visual Studio (VS2017) con il comando Contenitori](media/container-workspaces-window.png)

1. Nella finestra **Contenitori** selezionare **Crea**:

    ![Comando Crea nella finestra contenitori](media/containers-window-create.png)

1. Completare le informazioni richieste nella finestra di dialogo e selezionare **Crea**. Le credenziali immesse vengono usate anche per creare un account in Linux, che verrà usato in seguito per l'accesso.

    ![Immissione del nome del contenitore e delle credenziali durante la creazione di un contenitore](media/containers-window-create-fill.png)

1. La creazione dell'immagine con RTVS potrebbe richiedere tempo. La finestra **Output** in Visual Studio mostra lo stato, ma potrebbe sembrare che non accada nulla durante i download dell'immagine di lunga durata. Dopo aver compilato l'immagine, RTVS avvia il contenitore che viene poi visualizzato nella finestra **Contenitori**. I controlli a destra consentono di arrestare, rimuovere o riavviare il contenitore.

    ![Finestra Contenitori che mostra un contenitore completato](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Connettersi a un contenitore

1. La sezione **Contenitori in esecuzione locali** della finestra **Aree di lavoro** visualizza i contenitori che eseguono il daemon RTVS sulla porta 5444. Vedere [Remote R Service per Linux](setting-up-remote-r-service-on-linux.md) per informazioni dettagliate sulla configurazione del daemon.

    ![Finestra Aree di lavoro che mostra i contenitori disponibili](media/workspaces-window-running-containers.png)

1. Per connettersi a un contenitore, fare doppio clic sul nome del contenitore o selezionare il pulsante freccia destra, a destra del nome. Dopo aver stabilito la connessione viene visualizzata una finestra **R interattivo** (vedere [Usare la finestra R interattivo](interactive-repl-for-r-in-visual-studio.md)):

    ![Finestra Aree di lavoro con la finestra REPL aperta per un contenitore](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Usare immagini personalizzate

RTVS rileva e consente la gestione dei contenitori creati con immagini personalizzate, come l'immagine microsoft/rtvs descritta nel file Docker di seguito. Nell'immagine di base usata in questo esempio sono preinstallati rtvs-daemon, R 3.4.2 e i pacchetti R comuni. **Nota**: sostituire nome utente e password con i valori appropriati.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Usare il comando seguente per compilare l'immagine, sostituendo il nome del contenitore (argomento `--name`) con il nome desiderato:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

L'argomento `-p 6056:5444` esegue il mapping della porta 6056 alla porta interna 5444, usata da RTVS per il rilevamento di rtvs-daemon. Tutti i contenitori che espongono la porta 5444 vengono elencati nella finestra **Aree di lavoro**. È quindi possibile usare la finestra **Aree di lavoro** per connettersi a un contenitore con `<<unix>>\ruser1` come nome utente e "foobar" come password, a meno che non siano state specificate credenziali diverse nel file Docker.
