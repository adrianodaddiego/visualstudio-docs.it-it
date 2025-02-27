---
title: 'Scenario: Modificare la progettazione mediante gli strumenti di visualizzazione e modellazione'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f2e31e74ba89c30cfbacc46d1b72428372191ae
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476586"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenario: Modificare la progettazione mediante gli strumenti di visualizzazione e modellazione

Per assicurarsi che il sistema software soddisfi le esigenze degli utenti, usare gli strumenti di visualizzazione e di modellazione in Visual Studio.
Usare strumenti quali mappe codici, diagrammi delle dipendenze e i diagrammi classi per:

Per individuare le versioni di Visual Studio che supportano i singoli strumenti, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Definire le esigenze degli utenti e i processi aziendali.

- Visualizzare ed esplorare il codice esistente.

- Descrivere le modifiche a un sistema esistente.

- Verificare che il sistema soddisfi i propri requisiti.

- Mantenere la coerenza del codice con la progettazione.

Questa procedura dettagliata:

- Descrive i possibili vantaggi di questi strumenti per un progetto software.

- Illustra come usare questi strumenti, indipendentemente dall'approccio di sviluppo, con uno scenario di esempio.

Per altre informazioni su questi strumenti e sugli scenari supportati, vedere:

- [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)

- [Visualizzare il codice](../modeling/visualize-code.md)

## <a name="scenario-overview"></a>Panoramica dello scenario

Questo scenario descrive alcuni episodi dei cicli di vita di sviluppo software di due società fittizie: Dinner Now e Lucerne Publishing. Dinner Now fornisce un servizio di consegna pasti basato sul Web per l'area di Milano. I clienti possono ordinare pasti e pagare nel sito Web Dinner Now. Gli ordini vengono quindi inviati al ristorante locale di pertinenza per la consegna. Lucerne Publishing, una società con sede a Roma, gestisce varie attività offline e sul Web. Ad esempio, vengono eseguiti un sito Web in cui i clienti possono inserire recensioni di ristoranti.

Lucerne ha recentemente acquisito Dinner Now e vuole apportare le modifiche seguenti:

- Integrare i propri siti Web mediante l'aggiunta di funzionalità di recensione dei ristoranti a Dinner Now.

- Sostituire il sistema di pagamento di Dinner Now con il sistema di Lucerne.

- Espandere il servizio di Dinner Now nell'area.

Dinner Now usa le metodologie SCRUM e eXtreme Programming. Dispone di un code coverage dei test molto elevato e di una quantità estremamente ridotta di codice non supportato. Per ridurre al minimo i rischi, crea versioni ridotte ma funzionali di un sistema, aggiungendo quindi le funzionalità in modo incrementale. Lo sviluppo del codice avviene sulla base di iterazioni brevi e frequenti. Ciò consente all'azienda di gestire le modifiche nella massima sicurezza, di effettuare spesso il refactoring del codice ed evitare un eccessivo impegno iniziale di scrittura del codice.

Lucerne gestisce un insieme di sistemi molto più ampio e complesso, alcuni dei quali risalenti a oltre 40 anni fa. Le modifiche vengono apportate con estrema cautela a causa della complessità e dell'ambito del codice legacy. Segue un processo di sviluppo più rigoroso, in cui si preferisce progettare soluzioni dettagliate e documentare la progettazione e le modifiche apportate durante lo sviluppo.

Entrambi i team usano i diagrammi di modellazione in Visual Studio per sviluppare sistemi che soddisfino le esigenze degli utenti. Usano Team Foundation Server insieme ad altri strumenti per pianificare, organizzare e gestire il lavoro.

Per altre informazioni su Team Foundation Server, vedere:

- [Pianificare e tenere traccia del lavoro](#plan-and-track-work)

- [Test, convalida e archiviazione del codice aggiornato](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a> Ruoli dei diagrammi dell'architettura e della modellazione nello sviluppo del software

La tabella seguente descrive i ruoli che questi strumenti possono svolgere in diverse fasi del ciclo di vita dello sviluppo del software.

||**Modellazione dei requisiti utente**|**Modellazione dei processi aziendali**|**Architettura e progettazione di sistemi**|**Visualizzazione ed esplorazione del codice**|**Verifica**|
|------|-|-|-|-|-|
|Diagramma DSL (Domain-Specific Language)|Yes|Yes|Yes|||
|Diagramma delle dipendenze, la convalida dei livelli|||Yes|Yes|Yes|
|Mappa codice|||Yes|Yes|Yes|
|Progettazione classi (basata su codice)||||Yes||

Per disegnare i diagrammi delle dipendenze, è necessario creare un progetto di modellazione come parte di una soluzione esistente o nuovo. Questi diagrammi devono essere creati nel progetto di modellazione.
Gli elementi dei diagrammi delle dipendenze si trovano nel progetto di modellazione, ma non vengono archiviati nel modello comune. Mappe codice e diagrammi classi .NET creati dal codice esistono al di fuori del progetto di modellazione.

Vedere:

- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)

- [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Entrambi i team usano anche la convalida delle dipendenze per verificare che rimanga coerente con la progettazione di codice in fase di sviluppo. Vedere:

- [Coerenza del codice con la progettazione](#ValidatingCode)

- [Descrivere l'architettura logica: Diagrammi delle dipendenze](#DescribeLayers)

- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Alcune versioni di Visual Studio supportano la convalida delle dipendenze e le versioni di sola lettura di mappe codice per la visualizzazione e modellazione. Per informazioni su quali edizioni di Visual Studio supportano questa funzionalità, vedere [supporto di edizione per un'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Comprendere e comunicare le informazioni relative al sistema

Non è necessario usare i diagrammi di modellazione di Visual Studio in base a un ordine stabilito; possono essere usati in base alle proprie esigenze o all'approccio preferito. In genere i team rivedono i propri modelli in modo frequente e iterativo nel corso di un progetto. Ogni diagramma offre specifici punti di forza che consentono di comprendere, descrivere e comunicare i diversi aspetti del sistema in fase di sviluppo.

Dinner Now e Lucerne comunicano tra loro e con gli stakeholder progetto tramite i diagrammi come linguaggio di comuni. Ad esempio, Dinner Now usa i diagrammi per eseguire queste attività:

- Visualizzare il codice esistente.

- Comunicare con Lucerne riguardo a storie utente nuove o aggiornate.

- Identificare le modifiche necessarie per supportare le storie utente nuove o aggiornate.

Lucerne usa i diagrammi per eseguire queste attività:

- Acquisire informazioni sui processi aziendali di Dinner Now.

- Comprendere la progettazione del sistema.

- Comunicare con Dinner Now riguardo a requisiti utente nuovi o aggiornati.

- Documentare gli aggiornamenti di sistema.

I diagrammi sono integrati con Team Foundation Server per consentire ai team di pianificare, gestire e tenere traccia del proprio lavoro più facilmente. Ad esempio, i team usano i modelli per identificare test case e attività di sviluppo e per stimare il lavoro. Lucerne collega gli elementi di lavoro di Team Foundation Server a elementi del modello in modo da poter monitorare lo stato di avanzamento e assicurarsi che il sistema soddisfi i requisiti degli utenti. Ad esempio, collega i casi d'uso agli elementi di lavoro dei test case in modo da poter verificare che i casi d'uso siano soddisfatti quando tutti i test vengono superati.

Prima che i team archiviano le modifiche, convalidano il codice in base a test e alla progettazione eseguendo compilazioni che includono la convalida delle dipendenze e i test automatizzati. Questo garantisce che il codice aggiornato non sia in conflitto con la progettazione e non interferisca con funzionalità precedentemente funzionanti.

### <a name="identify-changes-to-the-existing-system"></a>Identificare le modifiche apportate al sistema esistente

Dinner Now deve stimare i costi da sostenere per soddisfare il nuovo requisito. Il costo dipende in parte dall'impatto che tale modifica avrà su altre parti del sistema. Per facilitare il compito, uno degli sviluppatori di Dinner Now crea queste mappe e questi diagrammi dal codice esistente:

|**Mappa o diagramma**|**Mostra**|
|-|-|
|*Mappa codice*<br /><br /> Vedere:<br /><br /> - [Mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />- [Cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md)<br />- [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Dipendenze e altre relazioni nel codice.<br /><br /> Ad esempio, Dinner Now potrebbe iniziare esaminando le mappe codice assembly per avere una panoramica degli assembly e delle relative dipendenze. Può analizzare in dettaglio le mappe per esplorare gli spazi dei nomi e le classi in tali assembly.<br /><br /> Dinner Now può anche creare mappe per esplorare aree specifiche e altri tipi di relazioni nel codice. Usa Esplora soluzioni per trovare e selezionare le aree e le relazioni di suo interesse.|
|*Diagramma classi basato su codice*<br /><br /> Vedere [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Classi presenti nel codice|

 Ad esempio, lo sviluppatore crea una mappa codice. Modifica l'ambito per concentrarsi sulle aree che saranno interessate dal nuovo scenario. Queste aree sono selezionate ed evidenziate nella mappa:

 ![Grafico delle dipendenze dello spazio dei nomi](../modeling/media/namespace_reviewsystem.png)

 **Mappa codice degli spazi dei nomi**

 Lo sviluppatore espande gli spazi dei nomi selezionati per visualizzarne le classi, i metodi e le relazioni:

 ![Grafico delle dipendenze dello spazio dei nomi espanso](../modeling/media/dep_reviewsystem.png)

 **Mappa codice degli spazi dei nomi espansi con i collegamenti tra gruppi visibili**

 Lo sviluppatore esamina il codice per trovare le classi e i metodi interessati. Per visualizzare gli effetti di ogni modifica nel momento stesso in cui viene effettuata, rigenerare le mappe codice dopo ogni modifica. Visualizzare [visualizzare il codice](../modeling/visualize-code.md).

 Per descrivere le modifiche ad altre parti del sistema, ad esempio componenti o interazioni, il team potrebbe disegnare questi elementi su una lavagna. Potrebbe anche creare i diagrammi seguenti in Visual Studio affinché i dettagli possano essere acquisiti, gestiti e riconosciuti da entrambi i team:

|**Diagrammi**|**Oggetto della descrizione**|
|-|-|
|*Diagramma classi basato su codice*<br /><br /> Vedere [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Classi presenti nel codice.|

### <a name="ValidatingCode"></a> Mantenere il codice coerente con la progettazione
 Dinner Now deve assicurarsi che il codice aggiornato rimanga coerente con la progettazione. Creano i diagrammi delle dipendenze che descrivono i livelli di funzionalità nel sistema, specificare le dipendenze consentite tra gli elementi di soluzione e associano su tali livelli.

|**Diagramma**|**Oggetto della descrizione**|
|-|-|
|*Diagramma delle dipendenze*<br /><br /> Vedere:<br /><br /> - [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagrammi delle dipendenze: Riferimento](../modeling/layer-diagrams-reference.md)<br />- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)<br />- [Convalidare il codice con diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)|L'architettura logica del codice.<br /><br /> Un diagramma di dipendenza organizza e mappa gli elementi di una soluzione di Visual Studio per astrarre gruppi denominati *livelli*. Questi livelli identificano i ruoli, le attività o le funzioni che questi elementi eseguono nel sistema.<br /><br /> I diagrammi delle dipendenze sono utili per descrivere la progettazione desiderata del sistema e convalidare il codice dinamico in base a questa progettazione.<br /><br /> Per creare livelli, trascinare elementi da Esplora soluzioni, mappe codice, Visualizzazione classi e Visualizzatore oggetti. Per disegnare nuovi livelli, usare la casella degli strumenti o fare clic con il pulsante destro del mouse sulla superficie del diagramma.<br /><br /> Per visualizzare le dipendenze esistenti, fare doppio clic sulla superficie del diagramma delle dipendenze e quindi fare clic su **genera dipendenze**. Per specificare le dipendenze desiderate, disegnare nuove dipendenze.|

Ad esempio, il diagramma di dipendenza seguente descrive le dipendenze tra livelli e il numero di elementi che sono associati a ogni livello:

![Diagramma delle dipendenze di sistema di pagamenti integrato](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagramma delle dipendenze**

Per assicurarsi che non si verificano conflitti con la progettazione durante lo sviluppo di codice, i team usano la convalida delle dipendenze su compilazioni che vengono eseguiti in Azure DevOps. È anche possibile creare un'attività personalizzata MSBuild per richiedere la convalida delle dipendenze nelle operazioni check-in. Per raccogliere gli errori di convalida, usano report di compilazione.

Vedere:

- [Utilizzare la finestra di progettazione visiva](/azure/devops/pipelines/get-started-designer)

- [TFVC l'archiviazione gestita](/azure/devops/pipelines/build/triggers#gated)

- [Compilare e rilasciare le attività](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Suggerimenti generali per la creazione e l'uso di modelli

- La maggior parte dei diagrammi è costituita da nodi connessi tramite linee. Per ogni tipo di diagramma, nella casella degli strumenti sono disponibili nodi e linee di vario tipo.

   Per aprire la casella degli strumenti, fare clic su **Casella degli strumenti** nel menu **Visualizza**.

- Per creare un nodo, trascinarlo dalla casella degli strumenti nel diagramma. Alcuni tipi di nodi devono essere trascinati nei nodi esistenti. Ad esempio, in un diagramma dei componenti è necessario aggiungere una nuova porta a un componente esistente.

- Per creare una linea o una connessione, fare clic sullo strumento appropriato nella casella degli strumenti, quindi sul nodo di origine e infine sul nodo di destinazione. Alcune linee possono essere create solo tra determinati tipi di nodi. Quando si sposta il puntatore su una possibile origine o destinazione, il puntatore indica se è possibile creare una connessione.

### <a name="plan-and-track-work"></a>Pianificare e rilevare lavoro

I diagrammi di modellazione di Visual Studio sono integrati con Team Foundation Server per consentire di pianificare, gestire e tenere traccia del proprio lavoro più facilmente. Entrambi i team usano i modelli per identificare test case e attività di sviluppo e per stimare il lavoro. Lucerne crea e collega gli elementi di lavoro di Team Foundation Server agli elementi del modello, come casi d'uso o componenti. In questo modo è in grado di monitorare lo stato di avanzamento e di tenere traccia del lavoro tenendo conto dei requisiti degli utenti. Ciò consente di verificare che le modifiche continuino a soddisfare tali requisiti.

Durante il lavoro, i team aggiornano gli elementi di lavoro in modo da riflettere il tempo dedicato alle varie attività. Inoltre, monitorano e segnalano lo stato del lavoro usando le funzionalità di Team Foundation Server seguenti:

- Giornaliero *burn-down report* che mostrano se verrà completato il lavoro pianificato nel tempo previsto. Altri rapporti analoghi vengono generati da Team Foundation Server per tenere traccia dello stato di avanzamento dei bug.

- Un *foglio di lavoro delle iterazioni* che usa Microsoft Excel per consentire al team di monitorare e bilanciare il carico di lavoro tra i membri. Questo foglio di lavoro è collegato a Team Foundation Server e fornisce contenuti sui quali incentrare la discussione durante le riunioni periodiche sullo stato di avanzamento.

- Un *dashboard di sviluppo* che usa Office Project per consentire al team di tenersi al corrente sulle informazioni importanti del progetto.

Vedere:

- [Sugli strumenti Agile e gestione dei progetti Agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts)

- [I grafici, dashboard e widget (servizi di Azure DevOps)](/azure/devops/report/dashboards/overview?view=vsts)

- [Creare il backlog e le attività tramite Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="TestValidateCheckInCode"></a> Test, convalida e archiviazione del codice

Quando i team completano ogni attività, archiviano il proprio codice in controllo del codice sorgente e ricevono un promemoria da Team Foundation Server, qualora se ne dimenticassero. Prima che Team Foundation Server accetti le archiviazioni, i team devono eseguire gli unit test e convalida delle dipendenze per verificare il codice in base ai test case e la progettazione. Usano Team Foundation Server per eseguire le compilazioni, unit test automatizzati e convalida delle dipendenze regolarmente. Questo permette di verificare che il codice soddisfi i criteri seguenti:

- Viene eseguito correttamente.

- Non impedisce l'esecuzione di codice precedentemente funzionante.

- Non è in conflitto con la progettazione.

Dinner Now dispone di un'ampia raccolta di test automatizzati, che possono essere riutilizzati da Lucerne in quanto ancora applicabili ai nuovi scenari. Lucerne può inoltre estendere questi test e aggiungerne altri per analizzare nuove funzionalità. Entrambi i team usano Visual Studio per eseguire i test manuali.

Per assicurarsi che il codice sia conforme alla progettazione, i team configurano le compilazioni in DevOps di Azure per includere la convalida delle dipendenze. In caso di conflitti, viene generato un report con i dettagli.

Vedere:

- [Test dell'applicazione](/azure/devops/test/overview?view=vsts)

- [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)

- [Utilizzare il controllo della versione](http://go.microsoft.com/fwlink/?LinkID=525605)

- [Pipeline di Azure](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aggiornare il sistema mediante visualizzazione e modellazione

Lucerne e Dinner Now devono integrare i propri sistemi di pagamento. Le sezioni seguenti mostrano i diagrammi di modellazione in Visual Studio per eseguire questa attività:

- [Visualizzare il codice esistente: Mappe codice](#VisualizeCode)

- [Definire un glossario dei tipi: Diagrammi classi](#DefineClasses)

- [Descrivere l'architettura logica: Diagrammi delle dipendenze](#DescribeLayers)

Vedere:

- [Visualizzare il codice](../modeling/visualize-code.md)

- [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)

- [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)

### <a name="VisualizeCode"></a> Visualizzare il codice esistente: Mappe codice

Le mappe codice mostrano l'organizzazione e le relazioni correnti nel codice. Gli elementi sono rappresentati da *nodi* sulla mappa e le relazioni sono rappresentate da *collegamenti*. Le mappe codice consentono di effettuare i tipi di attività seguenti:

- Esplorare codice con cui si ha poca familiarità.

- Comprendere dove e in che modo una modifica proposta potrebbe influire sul codice esistente.

- Trovare aree di complessità, le dipendenze naturali o modelli o altre aree suscettibili di miglioramento.

Ad esempio, si supponga che Dinner Now debba stimare il costo dell'aggiornamento del componente ElaborazionePagamenti. Il costo dipende in parte dall'impatto che tale modifica avrà su altre parti del sistema. Per facilitare il compito, uno degli sviluppatori di Dinner Now genera le mappe codice dal codice e ne modifica l'ambito limitandolo alle aree che potrebbero essere interessate dalla modifica.

Il seguente grafico mostra le dipendenze tra la classe ElaborazionePagamenti e le altre parti del sistema di Dinner Now, che appaiono selezionate:

![Grafico delle dipendenze per il sistema di pagamento di Dinner Now](../modeling/media/dep_dnpayment.png)

**Mappa codice per il sistema di pagamento di Dinner Now**

Lo sviluppatore esplora la mappa espandendo la classe ElaborazionePagamenti e selezionandone i membri per visualizzare le aree potenzialmente interessate:

![Metodi interni a ElaborazionePagamenti e dipendenze](../modeling/media/depgraph_expandeddn.png)

**Metodi interni alla classe ElaborazionePagamenti e relative dipendenze**

Viene generata la mappa seguente per consentire il controllo delle classi, dei metodi e delle dipendenze del sistema di pagamento di Lucerne. Il team si rende conto che potrebbe essere necessario apportare modifiche anche al sistema di Lucerne, per consentirne l'interazione con le altre parti di Dinner Now:

![Grafico delle dipendenze per il sistema di pagamento di Lucerne](../modeling/media/depgraph_lucernepay.png)

**Mappa codice per il sistema di pagamento di Lucerne**

Entrambi i team collaborano per determinare le modifiche necessarie per integrare i due sistemi e decidono di effettuare il refactoring di parte del codice per facilitarne l'aggiornamento. La classe RespApprovazionePagamenti verrà spostata nello spazio dei nomi DinnerNow.Business e richiederà alcuni nuovi metodi. Le classi di Dinner Now che gestiscono le transazioni avranno uno spazio dei nomi distinto. I team creano e usano elementi di lavoro per pianificare, organizzare e tenere traccia del lavoro. Ove sia utile, collegano gli elementi di lavoro agli elementi del modello.

Dopo avere riorganizzato il codice, i team generano una nuova mappa codice per visualizzare la struttura aggiornata e le relazioni:

![Grafico delle dipendenze con codice riorganizzato](../modeling/media/depgraph_integrated.png)

**Mappa codice con codice riorganizzato**

Questa mappa mostra che la classe RespApprovazionePagamenti ora si trova nello spazio dei nomi DinnerNow.Business e ha alcuni nuovi metodi. Le classi di transazione di Dinner Now ora hanno uno spazio dei nomi SistemaPagamento distinto, che semplificherà in seguito la gestione del codice.

#### <a name="creating-a-code-map"></a>Creazione di una mappa codice

- Per una rapida panoramica del codice sorgente, seguire questa procedura per generare una mappa codice:

     Nel menu **Architettura** fare clic su **Genera mappa codici per la soluzione**.

     Per una rapida panoramica del codice compilato, creare una mappa codice vuota, quindi trascinare file di assembly o file binari sulla superficie della mappa.

- Per esplorare elementi specifici del codice o della soluzione, usare Esplora soluzioni per selezionare gli elementi e le relazioni da visualizzare. È possibile quindi generare una nuova mappa o aggiungere gli elementi selezionati a una mappa esistente. Vedere [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

- Per esplorare agevolmente la mappa, ridisporre il layout in base ai tipi di attività da eseguire.

     Ad esempio, per visualizzare i livelli nel codice, selezionare un layout con una struttura ad albero. Visualizzare [cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Riepilogo: Vantaggi delle mappe codice
 Le mappe codice consentono di:

- Ottenere informazioni sull'organizzazione e sulle relazioni nel codice esistente.

- Identificare le aree sulle quali potrebbe influire una modifica proposta.

- Trovare aree di complessità, modelli, livelli o altre aree suscettibili di miglioramento, per rendere il codice più facile da gestire, modificare e riutilizzare.

#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi

|**Diagramma**|**Oggetto della descrizione**|
|-|-|
|Diagramma delle dipendenze|L'architettura logica del sistema. Utilizzare la convalida delle dipendenze per assicurarsi che il codice rimanga coerenza con la progettazione.<br /><br /> Per identificare le dipendenze esistenti o le dipendenze desiderate, creare una mappa codice e raggruppare gli elementi correlati. Per creare un diagramma delle dipendenze, vedere:<br /><br /> - [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)|
|Diagramma classi (basato su codice)|Classi presenti nel codice per un progetto specifico.<br /><br /> Per visualizzare e modificare una classe esistente nel codice, usare Progettazione classi.<br /><br /> Vedere [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="DefineClasses"></a> Definire un glossario dei tipi: Diagrammi classi
 I diagrammi classi definiscono le entità, i termini o i concetti che fanno parte del sistema e le reciproche relazioni. Ad esempio, è possibile usare questi diagrammi durante lo sviluppo per descrivere gli attributi e le operazioni per ogni classe, indipendentemente dal linguaggio o stile di implementazione.

 Per aiutare Lucerne a descrivere e discutere le entità che partecipano al caso d'uso Elaborazione dei pagamenti, viene creato il diagramma classi seguente:

 ![Entità Elabora pagamento nel diagramma classi](../modeling/media/uml_payentities.png)

 **Entità di Elaborazione dei pagamenti in un diagramma classi**

 Questo diagramma mostra che a un cliente possono essere associati più ordini e modalità di pagamento differenti. ContoBancario e CartaDiCredito ereditano da Pagamento.

 Durante lo sviluppo, Lucerne usa il seguente diagramma classi per descrivere e discutere i dettagli di ogni classe:

 ![Dettagli dell'entità Elabora pagamento in un diagramma classi](../modeling/media/uml_payment.png)

 **Dettagli di Elaborazione dei pagamenti nel diagramma classi**

#### <a name="drawing-a-class-diagram"></a>Creazione di un diagramma classi

Le caratteristiche principali di un diagramma classi sono le seguenti:

- Tipi quali classi, interfacce ed enumerazioni:

    - *Classe* : la definizione di oggetti che condividono caratteristiche strutturali o comportamentali specifiche.

    - *Interfaccia* : la definizione di una parte del comportamento esternamente visibile di un oggetto.

    - *Enumerazione* : un classificatore che contiene un elenco di valori letterali.

- *Attributi* : valori di un determinato tipo che descrivono ogni istanza di un *classificatore*. Un classificatore è un nome generale per tipi, componenti, casi d'uso e persino attori.

- *Operazioni* : metodi o funzioni che possono essere eseguite dalle istanze di un classificatore.

- *Associazione* : indica un tipo di relazione tra due classificatori.

  - *Aggregazione* : un'associazione che indica una proprietà condivisa tra classificatori.

  - *Composizione* : un'associazione che indica una relazione di una parte con il tutto tra classificatori.

    Per mostrare aggregazioni o composizioni, impostare la proprietà **Aggregazione** su un'associazione. **Condiviso** mostra le aggregazioni e **Composito** mostra le composizioni

- *Dipendenza* : indica che la modifica della definizione di un classificatore potrebbe comportare la modifica della definizione di un altro classificatore.

- *Generalizzazione* : indica che uno specifico classificatore eredita parte della definizione da un classificatore generale. *Realizzazione* : indica che una classe implementa le operazioni e gli attributi offerti da un'interfaccia.

     Per creare le relazioni, usare lo strumento **Ereditarietà** . In alternativa, una realizzazione può essere rappresentata come *simbolo*.

- *Pacchetti* : gruppi di classificatori, associazioni, linee di vita, componenti e altri pacchetti. *Importazione* : relazioni indicanti che un pacchetto include tutte le definizioni di un altro pacchetto.

Come punto di partenza per esplorare e discutere le classi esistenti, è possibile usare Progettazione classi per creare diagrammi classi dal codice.

- [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Riepilogo: Vantaggi dei diagrammi classi
 I diagrammi classi consentono di definire:

- Un glossario comune di termini da usare quando si discutono le esigenze degli utenti e le entità che partecipano al sistema. Visualizzare [modellare i requisiti utente](../modeling/model-user-requirements.md).

- Tipi usati da parti del sistema, come i componenti, indipendentemente dalla relativa implementazione. Visualizzare [modellare l'architettura dell'applicazione](../modeling/model-your-app-s-architecture.md).

- Le relazioni tra tipi, quali le dipendenze. Ad esempio, è possibile mostrare che un tipo può essere associato a più istanze di un altro tipo.

#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi

|**Diagramma**|**Descrizione**|
|-|-|
|Diagramma delle dipendenze|Definizione dell'architettura logica del sistema in relazione alle classi.<br /><br /> Utilizzare la convalida delle dipendenze per assicurarsi che il codice rimanga coerenza con la progettazione.<br /><br /> Vedere:<br /><br /> - [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagrammi delle dipendenze: Riferimento](../modeling/layer-diagrams-reference.md)<br />- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)<br />- [Convalidare il codice con diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)|
|Mappa codice|Visualizzazione dell'organizzazione e delle relazioni nel codice esistente.<br /><br /> Per identificare le classi e le relative relazioni e metodi, creare una mappa codice che mostra quegli elementi.<br /><br /> Vedere:<br /><br /> - [Mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="DescribeLayers"></a> Descrivere l'architettura logica: diagrammi delle dipendenze
 I diagrammi delle dipendenze descrivono l'architettura logica di un sistema organizzando gli elementi nella soluzione in gruppi astratti o *livelli*. Gli elementi possono essere di vario tipo, ad esempio spazi dei nomi, progetti, classi, metodi e così via. I livelli rappresentano i ruoli o le attività svolte nel sistema da tali elementi. È anche possibile includere la convalida dei livelli nelle operazioni di compilazione e archiviazione per assicurare la coerenza del codice con la progettazione.

 Per mantenere il codice coerente con la progettazione, Dinner Now e Lucerne usano il seguente diagramma di dipendenze per convalidare il codice evolve:

 ![Diagramma delle dipendenze di sistema di pagamenti integrato](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagramma delle dipendenze di Dinner Now integrato con Lucerne**

 I livelli di questo diagramma sono collegati ai corrispondenti elementi delle soluzioni di Dinner Now e Lucerne. Ad esempio, il livello Business è collegato allo spazio dei nomi DinnerNow.Business e ai relativi membri, che ora includono la classe RespApprovazionePagamenti. Il livello Accesso risorse è collegato allo spazio dei nomi DinnerNow.Dati. Le frecce, o *dipendenze*, specificano che solo il livello Business può usare le funzionalità del livello Accesso risorse. Man mano che aggiornano il codice, i team eseguono regolarmente la convalida dei livelli per intercettare i conflitti che si verificano e risolverli prontamente.

 I team collaborano per integrare e testare in modo incrementale i due sistemi. Prima di occuparsi di ElaborazionePagamenti, verificano il corretto funzionamento di RespApprovazionePagamenti con gli altri componenti di Dinner Now.

 La mappa codice seguente mostra le nuove chiamate tra Dinner Now e RespApprovazionePagamenti:

 ![Grafico delle dipendenze aggiornato con il sistema integrato](../modeling/media/depgraph_intsystem.png)

 **Mappa codice con le chiamate di metodo aggiornate**

 Dopo aver verificato che il sistema funziona come previsto, Dinner Now imposta come commento il codice di ElaborazionePagamenti. I report di convalida dei livelli non segnalano problemi e la mappa codice risultante mostra che non esistono altre dipendenze di ElaborazionePagamenti:

 ![Grafico delle dipendenze senza ElaborazionePagamenti](../modeling/media/depgraph_nomore.png)

 **Codice mappa senza ElaborazionePagamenti**

#### <a name="drawing-a-dependency-diagram"></a>Creazione di un diagramma di dipendenza

Un diagramma di dipendenza sono le seguenti funzionalità principali:

- *Livelli* : descrivono gruppi logici di elementi.

- *Collegamento* : un'associazione tra un livello e un elemento.

     Per creare livelli dagli elementi, trascinare gli elementi da Esplora soluzioni, da mappe codice, da Visualizzazione classi o da Visualizzatore oggetti. Per disegnare nuovi livelli e collegarli agli elementi, usare la casella degli strumenti o fare clic con il pulsante destro del mouse sulla superficie del diagramma per creare i livelli, quindi trascinare gli elementi su tali livelli.

     Il numero specificato su un livello indica il numero di elementi a esso collegati. Questi elementi possono essere spazi dei nomi, progetti, classi, metodi e così via. Quando si interpreta il numero di elementi in un livello, tenere presente quanto segue:

  - Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.

       Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.

  - Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.

    Per visualizzare gli elementi collegati a un livello, fare doppio clic la dipendenza e quindi fare clic su **Visualizza collegamenti** per aprire **Esplora livello**.

- *Dipendenza* : indica che un livello può usare le funzionalità di un altro livello, ma non viceversa. *Dipendenza bidirezionale* : indica che un livello può usare le funzionalità di un altro livello e viceversa.

     Per visualizzare le dipendenze esistenti nel diagramma delle dipendenze, pulsante destro del mouse sulla superficie del diagramma e quindi fare clic su **genera dipendenze**. Per descrivere le dipendenze previste, disegnarne altre.

Vedere:

- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)

- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)

- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Riepilogo: Vantaggi dei diagrammi delle dipendenze

I diagrammi delle dipendenze consentono di:

- Descrivere l'architettura logica di un sistema in base alle funzionalità degli elementi.

- Assicurarsi che il codice in corso di sviluppo sia conforme alla progettazione specificata.

#### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi

|**Diagramma**|**Descrizione**|
|-|-|
|Mappa codice|Visualizzazione dell'organizzazione e delle relazioni nel codice esistente.<br /><br /> Per creare livelli, generare una mappa codice e quindi raggruppare gli elementi della mappa come potenziali livelli. Trascinare i gruppi dalla mappa nel diagramma delle dipendenze.<br /><br /> Vedere:<br /><br /> - [Mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />- [Cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Risorse esterne

|**Categoria**|**Links**|
|-|-|
|**Forum**|- [Visual Studio Visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />- [Visual Studio Visualization and Modeling SDK (strumenti DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Vedere anche

- [Visualizzare il codice](../modeling/visualize-code.md)
- [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)
- [Usare i modelli in Agile development](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)
