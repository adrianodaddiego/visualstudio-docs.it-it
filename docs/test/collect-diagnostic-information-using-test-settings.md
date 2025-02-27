---
title: Raccogliere dati di diagnostica usando impostazioni test
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c378cea12ba749ee9131d13130fdbb7def84ea66
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823015"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Raccogliere dati di diagnostica usando impostazioni test

È possibile usare *Impostazioni test* in Visual Studio per raccogliere dati aggiuntivi quando si eseguono i test. Ad esempio, è possibile creare una registrazione video durante l'esecuzione del test. Sono presenti adattatori dati di diagnostica per:

- Raccogliere ogni passaggio delle azioni dell'interfaccia utente in formato di testo

- Registrare ciascuna azione dell'interfaccia utente per la riproduzione

- Raccogliere le informazioni sul sistema

- Raccogliere i dati del log eventi

- Raccogliere i dati IntelliTrace per isolare i bug non riproducibili

Gli adattatori dati di diagnostica possono essere usati per modificare il comportamento di un computer di test. Ad esempio, con un'impostazione test in Visual Studio, è possibile emulare diversi colli di bottiglia delle topologie di rete per valutare le prestazioni dell'applicazione del team.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Usare le impostazioni test con Visual Studio

Per eseguire gli unit test, i test codificati dell'interfaccia utente, delle prestazioni Web o di carico con Visual Studio, è possibile aggiungere, configurare e selezionare le impostazioni test da usare durante l'esecuzione. Per eseguire i test, raccogliere dati o influire su un computer di test in modalità remota, è necessario specificare un test controller da usare nelle impostazioni test. Il controller di test include agenti che possono essere usati per ogni ruolo nelle impostazioni di test.

## <a name="diagnostic-data-adapter-details"></a>Dettagli degli adattatori dati di diagnostica

Nella tabella seguente è disponibile una panoramica dei diversi modi in cui è possibile configurare gli adattatori dati di diagnostica da usare con ruoli computer locali o remoti.

|Adattatore dati di diagnostica usato nell'impostazione di test|Test manuali nel computer locale|Test automatizzati|Test manuali: raccolta di dati mediante un set di ruoli e un ambiente|Note|
|-|-|-|-|-|
|**Proxy client ASP.NET per IntelliTrace e impatto test:** questo proxy consente di raccogliere informazioni sulle chiamate http da un client a un server Web per gli adattatori dati di diagnostica di IntelliTrace e impatto test.|Sì|Yes|Sì|- Usare questa soluzione solo se per un ruolo client sono selezionati gli adattatori dati di diagnostica di IntelliTrace o impatto test.|
|**Profiler ASP.NET:** è possibile creare un'impostazione test che includa la profilatura ASP.NET per la raccolta di dati sulle prestazioni nelle applicazioni Web ASP.NET.|No|Sì (vedere le note)|No|- Questo adattatore dati di diagnostica è supportato solo in caso di esecuzione di test di carico da Visual Studio.|
|**Code coverage:** è possibile creare un'impostazione test in cui siano incluse informazioni sul code coverage usate per determinare la quantità di codice analizzata dai test.|No|Sì (vedere le note)|No|- È possibile usare il code coverage solo quando si esegue un test automatizzato da Visual Studio o *mstest.exe* e soltanto dal computer che esegue il test. La raccolta di dati in remoto non è supportata.<br />- La raccolta di dati di code coverage non funziona se l'impostazione di test è configurata per raccogliere informazioni di IntelliTrace. **Nota:**  Questo adattatore dati di diagnostica è applicabile solo alle impostazioni di test di Visual Studio. Non viene usato per le impostazioni test in Microsoft Test Manager. Inoltre, questo adattatore è per la compatibilità con i progetti di test di Visual Studio 2010. **Nota:**  Per compatibilità, il code coverage verrà applicato quando i test automatizzati vengono eseguiti da Microsoft Test Manager o su un agente di test remoto da Visual Studio tramite Test runner MS legacy.|
|**Log eventi:** è possibile configurare un'impostazione test per includere la raccolta del log eventi, compresa nei risultati dei test.|Sì|Yes|Sì||
|**IntelliTrace:** è possibile configurare l'adattatore dati di diagnostica in modo che *IntelliTrace* raccolga informazioni delle tacce di diagnostica specifiche, per agevolare l'isolamento di bug difficili da riprodurre. In questo modo viene creato un file IntelliTrace contenente queste informazioni. Un file IntelliTrace ha estensione *iTrace*. Quando un test non viene superato, si crea un bug. Il file di IntelliTrace salvato con i risultati del test viene collegato automaticamente a questo bug. I dati raccolti nel file di IntelliTrace consentono di migliorare la produttività del debug riducendo il tempo necessario per riprodurre e diagnosticare un errore nel codice. Da questo file di IntelliTrace è possibile simulare la sessione locale in un altro computer. Questo riduce il rischio di non riproducibilità di un bug.|Sì|Yes|Sì|- Se si abilita la raccolta di dati di IntelliTrace, la raccolta di dati del code coverage non funziona.<br />- Se si usa IntelliTrace per un ruolo client Web, è necessario anche selezionare l'adattatore dati di diagnostica Proxy client ASP.NET per IntelliTrace e impatto test.<br />- Sono supportate solo le versioni seguenti di IIS: IIS 7.0, IIS 7.5 e IIS 8.0.|
|**Emulazione di rete:** è possibile specificare che si vuole aggiungere un carico di rete artificiale al test usando un'impostazione test. L'emulazione di rete influisce sulla comunicazione da e verso il computer emulando una determinata velocità della connessione di rete, ad esempio di una connessione remota. |No|Sì (vedere le note)|No|È possibile usare l'adattatore dati di diagnostica dell'emulazione di rete per un ruolo client o server. Non è necessario usare l'adattatore su entrambi i ruoli che comunicano l'uno con l'altro. **Nota:**  Questo adattatore dati di diagnostica è applicabile solo alle impostazioni di test di Visual Studio. Non viene usato per le impostazioni test in Microsoft Test Manager. **Nota:**  Non è possibile usare l'emulazione di rete per aumentare la velocità della connessione di rete. **Avviso:**  Se si include l'adattatore dati di diagnostica dell'emulazione di rete nelle impostazioni di test e si vuole usarlo sul computer locale, è necessario anche associare il driver di emulazione di rete a una delle schede di rete del computer. Il driver di emulazione di rete è richiesto affinché l'adattatore dati di diagnostica dell'emulazione di rete funzioni. Il driver di emulazione di rete viene installato e associato all'adattatore in due modi: <ul><li>**Driver di emulazione di rete installato con l'agente di test Microsoft Visual Studio:** l'agente di test Microsoft Visual Studio può essere usato sia nei computer remoti che nel computer locale. Quando si installa un agente di test di Visual Studio, il processo di installazione include un passaggio di configurazione che associa il driver di emulazione di rete alla scheda di rete. Per altre informazioni, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).</li><li>**Driver di emulazione di rete installato con Microsoft Visual Studio Test Professional:** Quando si usa l'emulazione di rete per la prima volta, viene chiesto di associare il driver di emulazione di rete a una scheda di rete.</li></ul> È anche possibile installare il driver di emulazione di rete dalla riga di comando nel computer locale senza installare l'agente di test di Visual Studio tramite il comando seguente: **VSTestConfig NETWORKEMULATION /install** **Avviso:**  L'adattatore di emulazione di rete viene ignorato dai test di carico. Al contrario, i test di carico usano le impostazioni specificate nella combinazione di reti dello scenario dei test di carico.|
|**Informazioni di sistema:** è possibile configurare un'impostazione test per includere le informazioni di sistema relative al computer in cui viene eseguito il test.|Sì|Yes|Sì||
|**Impatto test:** è possibile raccogliere informazioni sui metodi del codice dell'applicazione usati durante l'esecuzione di un test case. Queste informazioni possono essere usate, insieme a quelle relative alle modifiche apportate al codice dell'applicazione dagli sviluppatori, per individuare i test interessati da tali modifiche di sviluppo.|Sì|Yes|Sì|- Se si raccolgono dati sull'impatto sui test per un ruolo client Web, è anche necessario selezionare l'adattatore dati di diagnostica Proxy client ASP.NET per IntelliTrace e impatto test.<br />- Sono supportate solo le versioni seguenti di IIS: IIS 7.0, IIS 7.5 e IIS 8.0.|
|**Videoregistratore:** è possibile creare una registrazione video della sessione desktop durante l'esecuzione di un test. Il video può consentire ad altri membri del team di isolare i problemi dell'applicazione difficili da riprodurre.|Sì|Sì (vedere le note)|Sì|- Se si abilita il software dell'agente di test per l'esecuzione come processo anziché come servizio, è possibile creare una registrazione video quando si eseguono i test automatizzati.|