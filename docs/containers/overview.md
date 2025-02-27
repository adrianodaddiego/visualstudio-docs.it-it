---
title: Strumenti contenitore di Visual Studio in Windows
description: Informazioni sugli strumenti disponibili in Visual Studio per l'uso di Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: fbe363e8f78cba9fa46f3634e59beb22e523ddfa
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65084041"
---
# <a name="container-tools-in-visual-studio"></a>Strumenti per contenitori in Visual Studio

Gli strumenti inclusi in Visual Studio per lo sviluppo con i contenitori sono facili da usare e semplificano notevolmente la compilazione, il debug e la distribuzione delle applicazioni in contenitori. È possibile usare un contenitore per un singolo progetto o usare l'orchestrazione dei contenitori con Docker Compose, Service Fabric o Kubernetes per operare con più servizi in contenitori.

> [!NOTE]
> Questo articolo si applica a Visual Studio in Windows e non a Visual Studio per Mac.

> [!TIP]
> Per altre informazioni sull'installazione di Docker per Windows, vedere [Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/) (Docker Desktop per Windows).

## <a name="docker-support-in-visual-studio"></a>Supporto di Docker in Visual Studio

Il supporto di Docker è disponibile per i progetti ASP.NET, i progetti ASP.NET Core e i progetti di console .NET Core e .NET Framework.

Il supporto per Docker in Visual Studio è cambiato nel corso di varie versioni in risposta alle esigenze dei clienti. Esistono due livelli di supporto di Docker che è possibile aggiungere a un progetto e le opzioni supportate variano a seconda del tipo di progetto e della versione di Visual Studio. Con alcuni tipi di progetto supportati, se si vuole semplicemente un contenitore per un singolo progetto, senza usare l'orchestrazione, è possibile farlo aggiungendo il supporto di Docker.  Il livello successivo è rappresentato dal supporto dell'orchestrazione dei contenitori, che aggiunge i file di supporto appropriati per lo specifico agente di orchestrazione scelto.  

::: moniker range="vs-2017"

Con Visual Studio 2017, è possibile usare Docker Compose e Service Fabric come servizi di orchestrazione dei contenitori.  È anche possibile usare Kubernetes se si installa [Visual Studio Tools per Kubernetes](https://aka.ms/get-vsk8stools).

> [!NOTE]
> Se si usa una versione di Visual Studio 2017 precedente alla 15.8 o si usa il modello di progetto .NET Framework (non .NET Core), quando si aggiunge il supporto di Docker viene aggiunto automaticamente il supporto dell'orchestrazione con Docker Compose. Il supporto dell'orchestrazione dei contenitori, tramite Docker Compose, viene aggiunto automaticamente in Visual Studio 2017 dalla versione 15.0 alla versione 15.7 e per i progetti .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

Con Visual Studio 2019 è possibile usare Docker Compose, Kubernetes e Service Fabric come servizi di orchestrazione dei contenitori.

> [!NOTE]
> Se si usa il modello di progetto console completo di .NET Framework, quando si aggiunge il supporto di Docker viene aggiunto automaticamente il supporto per l'orchestrazione con Docker Compose.
::: moniker-end

### <a name="adding-docker-support"></a>Aggiunta del supporto per Docker

È possibile abilitare il supporto di Docker durante la creazione del progetto selezionando **Abilita supporto Docker** quando si crea un nuovo progetto, come illustrato nello screenshot seguente:

::: moniker range="vs-2017"
![Abilitare il supporto di Docker per la nuova app Web ASP.NET Core in Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Abilitare il supporto di Docker per la nuova app Web ASP.NET Core in Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Per i progetti .NET Framework (non .NET Core) sono disponibili solo i contenitori di Windows.

È possibile aggiungere il supporto di Docker a un progetto esistente selezionando **Aggiungi** > **Supporto Docker** in **Esplora soluzioni**. I comandi **Aggiungi > Supporto Docker** e **Aggiungi > Supporto per l'agente di orchestrazione del contenitore** sono disponibili nel menu di scelta rapida del nodo di progetto per un progetto ASP.NET Core in **Esplora soluzioni**, come illustrato nello screenshot seguente:

![Opzione di menu Aggiungi Supporto Docker in Visual Studio](./media/overview/add-docker-support-menu.png)

Quando si aggiunge o si abilita il supporto di Docker, Visual Studio aggiunge quanto segue al progetto:

- Un file *Dockerfile*
- Un file con estensione dockerignore
- Un riferimento al pacchetto NuGet per Microsoft.VisualStudio.Azure.Containers.Tools.Targets

::: moniker range=">=vs-2019"
La soluzione ha l'aspetto seguente quando si aggiunge il supporto di Docker:

![Screenshot di Esplora soluzioni con file Dockerfile e dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Quando si abilita il supporto di Docker durante la creazione del progetto per un progetto ASP.NET (.NET Framework, non un progetto .NET Core), come illustrato nello screenshot seguente, viene aggiunto anche il supporto dell'orchestrazione dei contenitori.

![Abilitare il supporto di Docker Compose per un progetto ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Supporto di Docker Compose

Quando si vuole comporre una soluzione con più contenitori tramite Docker Compose, aggiungere il supporto dell'orchestrazione dei contenitori ai progetti. Ciò consente di eseguire un gruppo di contenitori (un'intera soluzione o un gruppo di progetti) e di eseguirne il debug contemporaneamente, se sono definiti nello stesso file *docker-compose.yml*.

Per aggiungere il supporto dell'orchestrazione dei contenitori tramite Docker Compose, fare clic con il pulsante destro del mouse sul nodo della soluzione o del progetto in **Esplora soluzioni**, scegliere **Aggiungi > Supporto dell'orchestrazione del contenitore**. Scegliere quindi **Docker Compose** per gestire i contenitori.

Dopo aver aggiunto il supporto dell'orchestrazione dei contenitori al progetto, si noteranno un *Dockerfile* aggiunto al progetto (se non esisteva già) e una cartella **docker-compose** aggiunta alla soluzione in  **Esplora soluzioni**, come illustrato di seguito:

![File di Docker in Esplora soluzioni in Visual Studio](media/overview/docker-support-solution-explorer.png)

Se il file *docker-compose.yml* esiste già, Visual Studio aggiunge solo le righe del codice di configurazione necessarie in tale file.

Ripetere il processo con gli altri progetti che si vuole controllare tramite Docker Compose.

## <a name="kubernetes-support"></a>Supporto di Kubernetes

::: moniker range="vs-2017"
Per aggiungere il supporto di Kubernetes, installare [Visual Studio Tools per Kubernetes](https://aka.ms/get-vsk8stools).
::: moniker-end

Con il supporto di Kubernetes, è possibile abilitare una connessione tra il progetto locale e un cluster di Kubernetes in esecuzione nel [servizio Azure Kubernetes](/azure/aks), riuscendo così a modificare ed eseguire il debug dei servizi in esecuzione nel servizio Azure Kubernetes con Visual Studio.  Questo servizio viene fornito da [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio). Azure Dev Spaces consente anche di configurare rami separati dei servizi Kubernetes chiamati *spazi di Azure Dev Spaces* per scopi di sviluppo. È quindi possibile isolare in modo efficiente i servizi di produzione dalle versioni attive in fase di sviluppo e mantenere nettamente separate modifiche distinte.

Per aggiungere il supporto di Kubernetes ai progetti, scegliere **Kubernetes/Helm** quando si aggiunge il supporto dell'orchestrazione dei contenitori. Vengono aggiunti vari file al progetto, tra i quali *azds.yaml*, che consente di configurare Azure Dev Spaces, e grafici Helm che descrivono la struttura dei servizi Kubernetes.

## <a name="service-fabric-support"></a>Supporto di Service Fabric

Con gli strumenti di Service Fabric in Visual Studio è possibile occuparsi dello sviluppo e del debug per Azure Service Fabric, gestire l'esecuzione e il debug in locale ed eseguire la distribuzione in Azure.

::: moniker range="vs-2017"
Visual Studio 2017 versione 15.9 e versioni successive con il carico di lavoro Sviluppo di Azure supportano lo sviluppo di microservizi in contenitori usando i contenitori Windows e l'orchestrazione di Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 supporta lo sviluppo di microservizi in contenitori usando i contenitori Windows e l'orchestrazione di Service Fabric.
::: moniker-end

Per un'esercitazione dettagliata, vedere [Esercitazione: Distribuire un'applicazione .NET in un contenitore Windows in Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Per altre informazioni su Azure Service Fabric, vedere [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Recapito continuo e integrazione continua (CI/CD)

Visual Studio si integra facilmente con Azure Pipelines per l'integrazione e il recapito continui e automatizzati delle modifiche al codice e alla configurazione del servizio. Per iniziare, vedere [Creare la prima pipeline](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2).

Per Service Fabric, vedere [Esercitazione: Distribuire l'app ASP.NET Core in Azure Service Fabric usando Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric).

Per Kubernetes, vedere [Deploy a Docker container app to Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops) (Distribuire un'app contenitore Docker nel servizio Azure Kubernetes).

## <a name="next-steps"></a>Passaggi successivi

Per altri dettagli sull'implementazione dei servizi e l'uso degli strumenti di Visual Studio per usare i contenitori, vedere gli articoli seguenti:

[Debug delle applicazioni in un contenitore Docker locale](vs-azure-tools-docker-edit-and-refresh.md)

[Distribuire un contenitore ASP.NET in un registro contenitori con Visual Studio](vs-azure-tools-docker-hosting-web-apps-in-docker.md)
