---
title: Carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati
description: Questo carico di lavoro di Visual Studio riunisce Python, F# e le rispettive distribuzioni di runtime, tra cui Anaconda. Visual Studio 2017 include anche R.
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: dbebf486680375622e6dc313a71e82f541107fc8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62958325"
---
# <a name="install-data-science-support-in-visual-studio"></a>Installare il supporto per l'analisi scientifica in Visual Studio

Il carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati, che può essere selezionato e installato tramite il programma di installazione di Visual Studio, riunisce diversi linguaggi e le rispettive distribuzioni di runtime:

::: moniker range="vs-2017"
- [Python e Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# con .NET Framework](/dotnet/fsharp/)
- [R e Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F# con .NET Framework](/dotnet/fsharp/)
::: moniker-end

![Carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati nel programma di installazione di Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python e R sono due dei principali linguaggi di scripting usati per le attività di data science. Entrambi i linguaggi sono facili da imparare e sono supportati da un nutrito ecosistema di pacchetti. Questi pacchetti soddisfano le esigenze di un'ampia gamma di scenari, ad esempio l'acquisizione e la pulizia dei dati, il training di modelli di dati, la distribuzione dei dati e i tracciati. F# è inoltre un linguaggio .NET potente e prima di tutto funzionale, adatto a una grande varietà di attività di elaborazione dati.
::: moniker-end

::: moniker range="vs-2019"
Python è un linguaggio di scripting fondamentale usato per le attività di data science. Python è facile da imparare ed è supportato da un nutrito ecosistema di pacchetti. Questi pacchetti soddisfano le esigenze di un'ampia gamma di scenari, ad esempio l'acquisizione e la pulizia dei dati, il training di modelli di dati, la distribuzione dei dati e i tracciati. F# è un potente linguaggio .NET di programmazione funzionale adatto a un'ampia varietà di attività di elaborazione dati. Per il linguaggio R, Microsoft consiglia [Azure Notebooks](https://notebooks.azure.com).
::: moniker-end

<!--Note link on the image because this one is large -->
[![Screenshot di Visual Studio con R, Python e F#](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Opzioni del carico di lavoro

Per impostazione predefinita, il carico di lavoro installa le opzioni seguenti, che è possibile modificare nella sezione di riepilogo per il carico di lavoro nel programma di installazione di Visual Studio:

::: moniker range="vs-2019"
- Supporto per il linguaggio F# desktop
- Python:
  - Supporto linguaggio Python
  - Supporto Web Python
::: moniker-end

::: moniker range="vs-2017"
- Supporto per il linguaggio F#
- Python:
  - Supporto linguaggio Python
  - [Anaconda3 a 64 bit](https://www.continuum.io), una distribuzione Python che include librerie di data science complete e un interprete Python.
  - Supporto Web Python
  - Supporto modello Cookiecutter
- R:
  - Supporto linguaggio R
  - Supporto runtime per strumenti di sviluppo R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (Interprete R di Microsoft supportato dalla community e completamente compatibile con librerie ScaleR per calcoli più veloci su singoli nodi o cluster. È anche possibile usare qualsiasi versione di R da [CRAN](https://cran.r-project.org/).)
::: moniker-end

## <a name="sql-server-integration"></a>Integrazione con SQL Server

::: moniker range="vs-2017"
SQL Server supporta l'uso di Python e R per eseguire attività di analisi avanzate direttamente all'interno di SQL Server. Il supporto di R è incluso in SQL Server 2016 e versioni successive, mentre il supporto di Python è disponibile in SQL Server 2017 CTP 2.0 e versioni successive.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server supporta l'uso di Python per eseguire attività di analisi avanzate direttamente all'interno di SQL Server. Il supporto di Python è disponibile in SQL Server 2017 CTP 2.0 e versioni successive.
::: moniker-end

L'esecuzione del codice nella posizione in cui si trovano già i dati offre i vantaggi seguenti:

- **Nessuno spostamento dei dati**: anziché spostare i dati dal database all'applicazione o al modello, è possibile compilare le applicazioni nel database. Questa funzionalità consente di evitare le barriere a livello di sicurezza, conformità, governance e integrità, oltre a una serie di problemi simili correlati allo spostamento di grandi quantità di dati. È anche possibile usare set di dati che non potrebbero essere gestiti con la memoria di un computer client.

- **Semplicità di distribuzione**: quando un modello è pronto, per la sua distribuzione nell'ambiente di produzione è sufficiente incorporarlo in uno script T-SQL. Qualsiasi applicazione client SQL scritta in qualsiasi linguaggio può quindi sfruttare modelli e intelligence tramite una chiamata di stored procedure. Non sono necessarie integrazioni specifiche del linguaggio.

- **Prestazioni e scalabilità di livello aziendale**: è possibile usare le funzionalità avanzate di SQL Server, ad esempio tabelle in memoria e indici columnstore, con le API scalabili a prestazioni elevate nei pacchetti RevoScale. Evitare gli spostamenti di dati significa anche evitare i vincoli di memoria client man mano che aumentano le dimensioni dei dati oppure se si desidera aumentare le prestazioni dell'applicazione.

- **Ampia estendibilità**: è possibile installare ed eseguire i pacchetti open source più recenti in SQL Server per compilare applicazioni per il Deep Learning e l'intelligenza artificiale che usano enormi quantità di dati in SQL Server. Installare un pacchetto in SQL Server è semplice come l'installazione di un pacchetto nel computer locale.

- **Disponibilità estesa senza costi aggiuntivi**: sono disponibili integrazioni di linguaggi in tutte le edizioni di SQL Server 2017 e versioni successive, inclusa la Express Edition.

Per sfruttare al meglio l'integrazione in SQL Server, usare il programma di installazione di Visual Studio per installare il carico di lavoro **Elaborazione ed archiviazione dati** con l'opzione **SQL Server Data Tools**. Questa opzione abilita SQL IntelliSense, l'evidenziazione della sintassi e la distribuzione.

![Carico di lavoro Elaborazione ed archiviazione dati](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Opzioni del carico di lavoro Elaborazione ed archiviazione dati](media/workload/data-storage-workload-options.png)

Per ulteriori informazioni:

::: moniker range="vs-2017"
- [Usare SQL Server ed R](../rtvs/integrating-sql-server-with-r.md)
- [In-database Advanced Analytics with R in SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/) (Analisi avanzata all'interno del database con R in SQL Server 2016)
::: moniker-end
- [Python in SQL Server 2017: enhanced in-database machine learning (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) (Python in SQL Server 2017: funzionalità avanzate di Machine Learning all'interno del database)

## <a name="additional-services-and-sdks"></a>Servizi aggiuntivi e SDK

Oltre ai componenti inclusi direttamente nel carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati, per le esigenze di data science sono utili anche il servizio Azure Notebooks e Azure SDK per Python.

Azure SDK per Python semplifica l'uso e la gestione dei servizi di Microsoft Azure dalle applicazioni eseguite in Windows, Mac e Linux. Per altre informazioni, vedere [Azure SDK per Python](../python/azure-sdk-for-python.md).

Azure Notebooks (attualmente in anteprima) consente l'accesso online gratuito ai notebook di Jupyter in esecuzione nel cloud in Microsoft Azure. Il servizio include notebook di esempio in Python, R e F# per iniziare. Visitare [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Screenshot di Azure Notebooks con l'esempio Introduction to R (Introduzione a R)](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
