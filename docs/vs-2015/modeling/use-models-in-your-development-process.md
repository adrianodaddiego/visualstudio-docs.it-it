---
title: Usare i modelli nel processo di sviluppo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
ms.assetid: a33ac8fc-4ba0-4850-b71b-014dc8674e54
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 92e8e236be1c6aa07709d03274a4c964b17b1bad
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700719"
---
# <a name="use-models-in-your-development-process"></a>Usare modelli nel processo di sviluppo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile usare un modello che consenta di comprendere e modificare un sistema, un'applicazione o un componente. Un modello consente di visualizzare l'ambiente in cui opera il sistema, chiarire le esigenze degli utenti, definire l'architettura del sistema, analizzare il codice e assicurarsi che soddisfi i requisiti. Vedere [Video di Channel 9: Migliorare l'architettura tramite la modellazione](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 Per vedere quali versioni di Visual Studio supportano ogni tipo di modello, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="how-to-use-models"></a>Come usare i modelli  
 I modelli possono essere di supporto all'utente in vari modi:  
  
- La creazione dei diagrammi di modellazione consente di chiarire i concetti coinvolti nei requisiti, nell'architettura e nella progettazione di alto livello. Per altre informazioni, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).  
  
- L'utilizzo di modelli consente di mettere in evidenza le incoerenze dei requisiti.  
  
- La comunicazione con i modelli consente di comunicare concetti importanti in modo meno ambiguo rispetto al linguaggio naturale. Per altre informazioni, vedere [modellare l'architettura dell'applicazione](../modeling/model-your-app-s-architecture.md).  
  
- In alcuni casi, è possibile usare modelli per generare codice o altri elementi quali documenti o schemi di database. Ad esempio, i componenti di modellazione di [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] generati da un modello.  Per altre informazioni, vedere [generare e configurare l'app da modelli](../modeling/generate-and-configure-your-app-from-models.md).  
  
  È possibile usare modelli in un'ampia gamma di processi da procedure estremamente agili a quelle più complesse.  
  
### <a name="use-models-to-reduce-ambiguity"></a>Usare modelli per ridurre l'ambiguità  
 Il linguaggio di modellazione è meno ambiguo del linguaggio naturale ed è progettato per esprimere idee in genere necessarie durante lo sviluppo di software.  
  
 Se per il progetto è disponibile un piccolo team che segue procedure agili, è possibile usare i modelli per chiarire le storie utente. Nelle discussioni con il cliente riguardo alle sue esigenze, la creazione di un modello può generare domande utili molto più rapidamente e in un'area più ampia del prodotto rispetto alla scrittura di codice di picco o di prototipi.  
  
 Se il progetto è grandi dimensioni e coinvolge team in diverse parti del mondo, è possibile usare i modelli per comunicare i requisiti e l'architettura in modo molto più efficace rispetto all'uso di testo normale.  
  
 In entrambi i casi la creazione di un modello quasi sempre comporta una riduzione significativa di incoerenze e ambiguità. Le diverse parti interessate frequentemente hanno percezioni diverse del mondo aziendale in cui funziona il sistema e sviluppatori diversi spesso hanno percezioni diverse della modalità di funzionamento del sistema. L'utilizzo di un modello come elemento attivo di una discussione generalmente rivela queste differenze. Per altre informazioni su come usare un modello per ridurre le incoerenze, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).  
  
### <a name="use-models-with-other-artifacts"></a>Usare i modelli con altri elementi  
 Un modello non è da solo una specifica dei requisiti o un'architettura. È uno strumento per esprimere alcuni aspetti di questi elementi in modo più chiaro, ma non è possibile esprimere tutti i concetti necessari durante la progettazione del software. I modelli devono perciò essere usati con altri mezzi di comunicazione, ad esempio paragrafi o pagine di OneNote, documenti di Microsoft Office, elementi di lavoro in [!INCLUDE[esprfound](../includes/esprfound-md.md)] o Sticky Notes sulla bacheca della stanza del progetto. Tranne l'ultimo elemento, tutti i tipi di oggetto possono essere collegati alle parti di elementi del modello.  
  
 Di seguito sono riportati altri aspetti della specifica che in genere vengono usati con i modelli. A seconda della scala e dello stile del progetto, è possibile usare diversi di questi aspetti o non usarli affatto:  
  
- Storie utente. Una storia utente è una breve descrizione, discussa con utenti e altre parti interessate, di un aspetto del comportamento del sistema che verrà recapitata in una delle iterazioni del progetto. Una storia utente tipica inizia nel modo seguente: "Il cliente sarà in grado di..." Una storia utente potrebbe presentare un gruppo di casi di utilizzo o definire estensioni di casi di utilizzo che sono stati sviluppati in precedenza. La definizione o l'estensione di casi di utilizzo consente di rendere la storia utente più chiara.  
  
- Richieste di modifica. Una richiesta di modifica in un progetto più formale è molto simile a una storia utente in un progetto agile. Nell'approccio agile tutti i requisiti vengono considerati modifiche a ciò che è stato sviluppato in iterazioni precedenti.  
  
- Descrizione del caso di utilizzo. Un caso di utilizzo rappresenta uno dei modi in cui un utente interagisce con il sistema per raggiungere un obiettivo specifico. Una descrizione completa include l'obiettivo, sequenze principali e alternative di eventi e risultati eccezionali. Un diagramma caso di utilizzo consente di riepilogare e fornire una panoramica dei casi di utilizzo.  
  
- Scenari. Uno scenario è una descrizione piuttosto dettagliata di una sequenza di eventi che mostrano come il sistema, gli utenti e altri sistemi funzionano insieme per fornire valore alle parti interessate. Potrebbe avere l'aspetto di una presentazione dell'interfaccia utente o di un prototipo dell'interfaccia utente. Può descrivere un caso di utilizzo o una sequenza di casi di utilizzo.  
  
- Glossario. Il glossario dei requisiti del progetto descrivono le parole con cui i clienti discutono in merito al proprio mondo. I modelli di requisiti e interfaccia utente devono usare anche questi termini. Un diagramma classi può chiarire le relazioni tra la maggior parte di questi termini. La creazione dei diagrammi e del glossario non solo riduce malintesi tra utenti e sviluppatori, ma quasi sempre evidenzia anche malintesi tra le diverse parti aziendali interessate.  
  
- Regole di business. Molte regole di business possono essere espresse come vincoli invariabili sulle associazioni e sugli attributi nel modello di classi di requisiti e come vincoli sui diagrammi di sequenza.  
  
- Progettazione ad alto livello. Vengono descritte le parti principali e come interagiscono. I diagrammi dei componenti, di sequenza e interfaccia costituiscono una parte importante di un progetto di alto livello.  
  
- Schemi progettuali. Vengono descritte le regole di progettazione che vengono condivise tra diverse parti del sistema.  
  
- Specifiche di test. Gli script di test e le progettazioni per il codice di test possono avvalersi dei diagrammi di sequenza e di attività per descrivere le sequenze dei passi di test. I test di sistema devono essere espressi in termini di modello requisiti in modo che sia possibile modificarli facilmente quando cambiano i requisiti.  
  
- Piano del progetto. Il piano del progetto o il backlog definisce quando verrà recapitata ogni funzionalità. È possibile definire ogni funzionalità dichiarando quali casi di utilizzo e regole di business vengono implementate o estese. È possibile fare riferimento ai casi di utilizzo e alle regole di business direttamente nel piano oppure è possibile definire un set di funzionalità in un documento separato e usare i titoli delle funzionalità nel piano.  
  
### <a name="use-models-in-iteration-planning"></a>Usare i modelli nel piano di iterazione  
 Anche se tutti i progetti sono diversi nella scala e nell'organizzazione, un progetto tipico è pianificato come una serie di iterazioni compresa tra due e sei settimane. È importante pianificare sufficienti iterazioni per consentire il feedback delle iterazioni precedenti da usare per regolare l'ambito e i piani per iterazioni successive.  
  
 I suggerimenti seguenti possono risultare utili per realizzare i vantaggi della modellazione in un progetto iterativo.  
  
#### <a name="sharpen-focus-as-each-iteration-approaches"></a>Migliorare lo stato all'approccio di ogni iterazione  
 All'approcciarsi di ogni iterazione, è possibile usare modelli per definire cosa deve essere consegnato alla fine dell'iterazione.  
  
- Non modellare tutto in dettaglio nelle prime iterazioni. Nella prima iterazione creare un diagramma classi per gli elementi principali nel glossario dell'utente, creare un diagramma dei casi di utilizzo principali e creare un diagramma dei componenti principali. Non descrivere nessuno di questi elementi dettagliatamente perché i dettagli verranno modificati in un secondo momento nel progetto. Usare i termini definiti in questo modello per creare un elenco di funzionalità o storie utente principali. Assegnare le funzionalità alle iterazioni in modo da bilanciare approssimativamente il carico di lavoro stimato nel corso del progetto. Queste assegnazioni verranno modificate in un secondo momento nel progetto.  
  
- Provare a implementare versioni semplificate di tutti i casi di utilizzo più importanti in una prima iterazione. Estendere i casi di utilizzo in iterazioni successive. Questo approccio consente di ridurre il rischio di individuare un difetto nei requisiti o nell'architettura del progetto troppo tardi per poter fare qualcosa a riguardo.  
  
- Verso la fine di ogni iterazione indire un workshop dei requisiti per definire in dettaglio i requisiti o le storie utente che verranno sviluppate nell'iterazione successiva. Invitare gli utenti e le parti interessate dell'azienda che sono in grado di decidere le priorità, nonché gli sviluppatori e i tester di sistema. Vengono consentite tre ore per definire i requisiti per un'iterazione di 2 settimane.  
  
- Per ogni partecipante l'obiettivo del workshop è accettare ciò che verrà effettuato entro la fine dell'iterazione successiva. Usare i modelli come uno degli strumenti che consentono di chiarire i requisiti. L'output del workshop è il backlog di un'iterazione: vale a dire un elenco di sviluppo di attività in [!INCLUDE[esprfound](../includes/esprfound-md.md)] e i gruppi di test in [!INCLUDE[TCMext](../includes/tcmext-md.md)].  
  
- Nel workshop dei requisiti discutere la progettazione solo nella misura in cui è necessario determinare le stime per le attività di sviluppo. In caso contrario, discutere sul comportamento del sistema che gli utenti possono sperimentare direttamente. Mantenere il modello requisiti separato dal modello dell'architettura.  
  
- Le parti interessate non tecniche in genere non hanno problemi a comprendere i diagrammi UML con alcune indicazioni da parte dell'utente.  
  
#### <a name="link-model-to-work-items"></a>Collegare il modello agli elementi di lavoro  
 Dopo il workshop di requisiti, elaborare i dettagli del modello requisiti e collegare il modello alle attività di sviluppo. A tale scopo è possibile collegare gli elementi di lavoro in [!INCLUDE[esprfound](../includes/esprfound-md.md)] agli elementi del modello. Per informazioni su come eseguire questa operazione, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).  
  
 È possibile collegare qualsiasi elemento agli elementi di lavoro, ma quelli più utili sono i seguenti:  
  
- Casi di utilizzo. È possibile collegare un caso di utilizzo alle attività di sviluppo che lo implementeranno.  
  
- Estensioni del caso di utilizzo. Se solo un aspetto di un caso di utilizzo verrà implementato in un'iterazione, è possibile separarlo in un caso di utilizzo di base con una o più estensioni. Le estensioni sono casi di utilizzo collegati al caso di base con la relazione «Estendi». Per altre informazioni sull'estensione dei casi di utilizzo, vedere [diagrammi caso di utilizzo UML: informazioni di riferimento](../modeling/uml-use-case-diagrams-reference.md).  
  
- Commenti che descrivono i requisiti delle regole di business o della qualità del servizio. Per altre informazioni, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).  
  
#### <a name="link-model-to-tests"></a>Collegare un modello ai test  
 Usare il modello requisiti per guidare la progettazione dei test di accettazione. Creare questi test contemporaneamente al lavoro di sviluppo.  
  
 Per altre informazioni su questa tecnica, vedere [sviluppare test da un modello](../modeling/develop-tests-from-a-model.md).  
  
#### <a name="estimate-remaining-work"></a>Stimare il lavoro rimanente  
 Un modello requisiti può agevolare la stima delle dimensioni totali del progetto rispetto alle dimensioni di ogni iterazione. La valutazione del numero e della complessità delle classi e dei casi di utilizzo agevolano la stima del lavoro di sviluppo che sarà necessario. Quando sono state completate le prime iterazioni, un confronto dei requisiti analizzati e di quelli ancora da analizzare può fornire un'indicazione approssimativa del costo e dell'ambito della parte restante del progetto.  
  
 Verso la fine di ogni iterazione, rivedere l'assegnazione dei requisiti per le iterazioni future. Può essere utile rappresentare lo stato del software alla fine di ogni iterazione come un sottosistema in un diagramma caso di utilizzo. Nelle discussioni è possibile spostare i casi di utilizzo e usare le estensioni da uno di questi sottosistemi a un altro.  
  
## <a name="levels-of-abstraction"></a>Livelli di astrazione  
 I modelli dispongono di un intervallo di astrazione in relazione al software. I modelli più concreti rappresentano direttamente il codice di programma e quelli più astratti rappresentano i concetti di business che possono o non possono essere rappresentati nel codice.  
  
 È possibile visualizzare un modello tramite diversi tipi di diagrammi. Per informazioni sui modelli e diagrammi, vedere [creare modelli per l'app](../modeling/create-models-for-your-app.md).  
  
 Diversi tipi di diagramma sono utili per descrivere la progettazione a diversi livelli di astrazione. Molti tipi di diagramma sono utili più livelli. Questa tabella mostra come usare ogni tipo di diagramma.  
  
|Livello di progettazione|Tipi di diagramma|  
|------------------|-------------------|  
|Processo aziendale<br /><br /> Le informazioni sul contesto in cui verrà usato il sistema consentono di comprendere quali sono le esigenze degli utenti.|-Diagrammi di attività descrivono il flusso di lavoro tra persone e sistemi per raggiungere gli obiettivi aziendali.<br />-I diagrammi classi concettuali descrivono i concetti aziendali usati all'interno del processo di business.|  
|Requisiti utente<br /><br /> La definizione di ciò che gli utenti richiedono al sistema.|-Diagrammi casi d'uso riepilogano le interazioni che gli utenti e altri sistemi esterni hanno con il sistema che si sta sviluppando. È possibile associare altri documenti per ogni caso di utilizzo per descriverlo in dettaglio.<br />-Diagrammi classi UML descrivono i tipi di informazioni che gli utenti e il sistema di segnalare.<br />-Le regole di business e qualità dei requisiti del servizio possono essere descritti nei documenti separati.|  
|Progettazione ad alto livello<br /><br /> La struttura generale del sistema: i componenti principali e la modalità con cui vengono accoppiati.|: I diagrammi livello viene descritto come il sistema viene strutturato in parti interdipendenti. È possibile convalidare il codice di programma con i diagrammi livello per assicurarsi che sia conforme all'architettura.<br />-Diagrammi dei componenti mostrano le interfacce delle parti, specificando i messaggi e i servizi forniti e richiesti da ogni componente.<br />-Diagrammi di sequenza mostrano come i componenti comunicano per implementare ogni caso d'uso.<br />-Diagrammi classi UML descrivono le interfacce dei componenti e i tipi di dati passati tra i componenti.|  
|Schemi progettuali<br /><br /> Convenzioni e metodi di risoluzione dei problemi di progettazione che vengono usati in tutte le parti della progettazione|-Diagrammi classi UML descrivono le strutture di un modello<br />-Sequenza o diagrammi di attività mostrano le interazioni e gli algoritmi|  
|Analisi codice<br /><br /> Diversi tipi di diagramma possono essere generati dal codice.|-Diagrammi di sequenza mostrano l'interazione tra oggetti nel codice.<br />: I diagrammi livello mostrano le dipendenze tra classi. Il codice aggiornato può essere convalidato in base a un diagramma livello.<br />-Diagrammi classi mostrano le classi nel codice.|  
  
## <a name="external-resources"></a>Risorse esterne  
  
|**Categoria**|**Collegamenti**|  
|------------------|---------------|  
|**Video**|![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I video: Come creare e usare i modelli UML e diagrammi (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkId=214460)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML con Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=201106)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: Gli strumenti UML e l'estendibilità (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkID=214467)|  
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blog**|[Blog di Visual Studi ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Articoli e pubblicazioni tecniche**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)<br /><br /> [Documentazione Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Usare i modelli nello sviluppo Agile](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)   
 [Modellare i requisiti utente](../modeling/model-user-requirements.md)   
 [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)   
 [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)   
 [Strutturare la soluzione di modellazione](../modeling/structure-your-modeling-solution.md)
