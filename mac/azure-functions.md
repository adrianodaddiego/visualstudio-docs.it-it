---
title: Introduzione alle funzioni di Azure
description: Uso delle funzioni di Azure in Visual Studio per Mac.
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: db25a9cbc647e399da86781d155a7b55d8e3802e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62984875"
---
# <a name="introduction-to-azure-functions"></a>Introduzione alle funzioni di Azure

Le funzioni di Azure sono un metodo per la creazione e l'esecuzione di frammenti di codice gestiti dagli eventi (funzioni) nel cloud, senza richiedere l'aggiunta o la gestione esplicita di elementi di infrastruttura. Per altre informazioni sulle funzioni di Azure, vedere la [documentazione di Funzioni di Azure](/azure/azure-functions/).

## <a name="requirements"></a>Requisiti

Gli strumenti per le funzioni di Azure sono inclusi in **Visual Studio per Mac 7.5** e versioni successive.

Per creare e distribuire le funzioni è necessaria anche una sottoscrizione di Azure, disponibile gratuitamente in [https://azure.com/free](https://azure.com/free).

## <a name="creating-your-first-azure-functions-project"></a>Creazione del primo progetto di Funzioni di Azure

1. In Visual Studio per Mac selezionare **File > Nuova soluzione**.
2. Nella finestra di dialogo Nuovo progetto, selezionare il modello Funzioni di Azure in **Cloud > Generale** e fare clic su **Avanti**:

    ![Finestra Nuovo progetto con l'opzione Funzioni di Azure](media/azure-functions-image1.png)

3. Selezionare il modello iniziale di Funzioni di Azure che si desidera usare, immettere il nome della funzione e fare clic su **Avanti**.

    ![Finestra Nuovo progetto che mostra i modelli di funzioni di Azure](media/azure-functions-image2.png)

    > [!TIP]
    > Anche se si cerca di mantenere il più possibile aggiornati il runtime e i modelli di Funzioni di Azure (interfaccia della riga di comando) in bundle, è inevitabile che diventino obsoleti. Quando si crea un nuovo progetto Funzioni, Visual Studio per Mac controlla la disponibilità di aggiornamenti per l'interfaccia della riga di comando e invia una notifica come illustrato nell'immagine seguente. È sufficiente fare clic sul pulsante per scaricare i modelli aggiornati.
    > ![Finestra Nuovo progetto che mostra che sono disponibili aggiornamenti per le funzioni di Azure](media/azure-functions-update.png)

    A seconda del tipo di funzione selezionato, nella pagina successiva verrà richiesto di immettere i dettagli, ad esempio i diritti di accesso, come illustrato nell'immagine seguente:

    ![Finestra Nuovo progetto con l'opzione aggiuntiva](media/azure-functions-image3.png)

    Per altre informazioni sui diversi tipi di modelli di Funzioni di Azure e le proprietà di associazione richieste per configurare ogni modello, vedere la sezione [Modelli di funzione disponibili](#available-function-templates). Per questo esempio, si usa un trigger HTTP con diritti di accesso anonimi.

4. Dopo aver impostato i parametri, scegliere la posizione per il progetto e fare clic su **Crea**.

Visual Studio per Mac crea un progetto .NET Standard che include una funzione predefinita. Il progetto include anche riferimenti NuGet a vari pacchetti **AzureWebJobs**, nonché al pacchetto **Newtonsoft.Json**.

![Editor di Visual Studio per Mac con una nuova funzione di Azure creata da un modello](media/azure-functions-newproj.png)

Il nuovo progetto contiene i file seguenti:

* **nome-funzione.cs** - Questa classe contiene il codice boilerplate per la funzione selezionata. Contiene un attributo **FunctionName** con il nome della funzione e un attributo trigger che specifica cosa attiva la funzione, ad esempio una richiesta HTTP. Per altre informazioni sul metodo della funzione, vedere l'articolo [Azure Functions C# developer reference](/azure/azure-functions/functions-dotnet-class-library) (Riferimento di Funzioni di Azure per gli sviluppatori C#).
* **host.json**: questo file descrive le opzioni di configurazione globali per l'host delle funzioni. Per visualizzare un file di esempio e informazioni sulle impostazioni disponibili per tale file, vedere [Riferimento host.json per Funzioni di Azure](/azure/azure-functions/functions-host-json).
* **local.settings.json**: questo file contiene tutte le impostazioni per l'esecuzione locale delle funzioni. Le impostazioni vengono usate dagli strumenti di base di Funzioni di Azure. Per altre informazioni, vedere [File di impostazioni locali](/azure/azure-functions/functions-run-local#local-settings-file) nell'articolo relativo agli strumenti di base di Funzioni di Azure.

Ora che è stato creato un nuovo progetto di Funzioni di Azure in Visual Studio per Mac, è possibile sottoporre a test la funzione attivata da HTTP predefinita nel computer locale.

## <a name="testing-the-function-locally"></a>Test della funzione in locale

Grazie al supporto di Funzioni di Azure in Visual Studio per Mac è possibile sottoporre a test e debug la funzione nel computer di sviluppo locale.

1. Per eseguire il test della funzione in locale, fare clic sul pulsante **Esegui** in Visual Studio per Mac:

    ![Pulsante per l'avvio del debug in Visual Studio per Mac](media/azure-functions-run.png)

1. L'esecuzione del progetto inizia con il debug locale della funzione di Azure e apre una nuova finestra Terminale, come illustrato nell'immagine seguente:

    ![Finestra Terminale con l'output della funzione](media/azure-functions-terminal.png)

    Copiare l'URL dall'output.

3. Incollare l'URL della richiesta HTTP nella barra degli indirizzi del browser. Aggiungere la stringa di query `?name=<yourname>` alla fine dell'URL ed eseguire la richiesta. L'immagine seguente visualizza la risposta restituita dalla funzione nel browser alla richiesta GET locale:

    ![Richiesta HTTP nel browser](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Aggiunta di un'altra funzione al progetto

I modelli di funzione consentono di creare rapidamente nuove funzioni usando i trigger e i modelli più comuni. Per creare un altro tipo di funzione, seguire questa procedura:

1. Per aggiungere una nuova funzione, fare clic con il pulsante destro del mouse sul nome del progetto e selezionare **Aggiungi > Aggiungi funzione**:

    ![Azione di contesto per l'aggiunta della nuova funzione](media/azure-functions-addnew.png)

2. Nella finestra di dialogo **Nuova funzione di Azure** selezionare la funzione necessaria:

    ![Finestra di dialogo Nuova funzione di Azure](media/azure-functions-image4.png)

    Nella sezione [Modelli di funzione disponibili](#available-function-templates) è disponibile un elenco dei modelli di Funzioni di Azure.

È possibile usare la procedura sopra descritta per aggiungere altre funzioni al progetto dell'app per le funzioni. Ogni funzione nel progetto può avere un trigger diverso, ma una funzione deve avere esattamente un trigger. Per altre informazioni, vedere [Concetti di trigger e associazioni di Funzioni di Azure](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Pubblicare in Azure

1. Fare clic con il pulsante destro del mouse sul nome del progetto e scegliere **Pubblica > Pubblica in Azure**:  ![Opzione di menu Pubblica in Azure](media/azure-functions-image5.png)
2. Se l'account di Azure è già stato connesso a Visual Studio per Mac, viene visualizzato un elenco dei servizi app disponibili. Se non è stato ancora effettuato l'accesso, verrà richiesto di farlo.
3. Nella finestra di dialogo **Pubblica in Servizi app di Azure** è possibile selezionare un servizio app esistente o crearne uno nuovo facendo clic **Nuovo**.
4. Nella finestra di dialogo **Crea nuovo servizio app** immettere le impostazioni:  ![Opzione di menu Pubblica in Azure](media/azure-functions-image7.png)

    |Impostazione  |Description  |
    |---------|---------|
    |**Nome del servizio app**|Nome globalmente univoco che identifica la nuova app per le funzioni.|
    |**Sottoscrizione**|La sottoscrizione di Azure da usare.|
    |**[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)**|Nome del gruppo di risorse in cui creare l'app per le funzioni. Scegliere **+** per creare un nuovo gruppo di risorse.|
    |**[Piano di servizio](/azure/azure-functions/functions-scale)**|Scegliere un piano esistente o creare un piano personalizzato. Scegliere una località in un'area nelle vicinanze o vicino ad altri servizi a cui accedono le funzioni.|

5. Fare clic su **Avanti** per creare un account di archiviazione. Il runtime di Funzioni richiede un account di archiviazione di Azure. Fare clic su **Personalizzato** per creare un account di archiviazione per utilizzo generico oppure usarne uno esistente:

    ![Opzione di menu Pubblica in Azure](media/azure-functions-image8.png)

6. Fare clic su **Crea** per creare un'app per le funzioni e le relative risorse in Azure con queste impostazioni e distribuire il codice del progetto per funzioni.

7. Potrebbe essere visualizzata una finestra di dialogo durante la pubblicazione con la richiesta "Aggiorna versione di Funzioni in Azure". Fare clic su **Sì**:

    ![Opzione di menu Pubblica in Azure](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Impostazioni dell'app per le funzioni

Le impostazioni aggiunte nel file local.settings.json devono essere aggiunte anche all'app per le funzioni in Azure. Queste impostazioni non vengono caricate automaticamente quando si pubblica il progetto.

Per accedere alle impostazioni dell'app, passare al portale di Azure all'indirizzo [https://ms.portal.azure.com/](https://ms.portal.azure.com/). In **App per le funzioni** selezionare **App per le funzioni** ed evidenziare il nome della funzione:

![Menu di Funzioni di Azure](media/azure-functions-image9.png)

Nella scheda **Panoramica** selezionare **Impostazioni applicazione** in **Funzionalità configurate**:

![Scheda Panoramica per la funzione di Azure](media/azure-functions-image10.png)

Da qui è possibile impostare le impostazioni dell'applicazione per l'app per le funzioni ed è possibile aggiungere nuove impostazioni o modificare quelle esistenti:

![Area delle impostazioni dell'applicazione del portale di Azure](media/azure-functions-image11.png)

Un'altra impostazione importante che potrebbe essere necessario impostare è `FUNCTIONS_EXTENSION_VERSION`. Durante la pubblicazione da Visual Studio per Mac, questo valore deve essere impostato su **beta**.

## <a name="available-function-templates"></a>Modelli di funzioni disponibili

- **Trigger GitHub**: risponde a eventi che si verificano nei repository GitHub. Per altre informazioni, vedere l'[articolo di Funzioni di Azure su GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - Commenter GitHub: funzione che viene eseguita e aggiunge un commento ogni volta che viene ricevuto un webhook GitHub per un problema o una richiesta pull.
    - WebHook GitHub: funzione che viene eseguita ogni volta che viene ricevuto un webhook GitHub.

- **HTTP**: attivare l'esecuzione del codice usando una richiesta HTTP. Sono disponibili modelli espliciti per i seguenti trigger HTTP:
    - Trigger HTTP
    - Http GET CRUD
    - Http POST CRUD
    - Trigger HTTP con parametri

- **Timer**: consente di eseguire attività di pulizia o altre attività batch in una pianificazione predefinita. Questo modello supporta due campi: un nome e una pianificazione, ovvero un'espressione CRON a sei campi. Per altre informazioni, vedere [l'articolo di Funzioni di Azure con timer](/azure/azure-functions/functions-create-scheduled-function)

- **Trigger Queue**: funzione che risponde ai messaggi quando raggiungono la coda di Archiviazione di Azure. Oltre al nome della funzione, questo modello accetta una proprietà **Path** (nome della coda dalla quale verrà letto il messaggio) e una proprietà **Connection** dell'account di archiviazione (nome dell'impostazione dell'app che contiene la stringa di connessione dell'account di archiviazione). Per altre informazioni, vedere l'[articolo di Funzioni di Azure sull'archiviazione code](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Trigger BLOB**: elabora i BLOB di Archiviazione di Azure quando vengono aggiunti a un contenitore. Oltre al nome della funzione, questo modello accetta proprietà Path e Connection. La proprietà Path è il percorso dell'account di archiviazione che verrà monitorato dal trigger. L'account di connessione è il nome dell'impostazione dell'app contenente la stringa di connessione dell'account di archiviazione. Per altre informazioni, vedere l'[articolo di Funzioni di Azure sull'archiviazione BLOB](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **WebHook generico**: funzione semplice che viene eseguita ogni volta che riceve una richiesta da un servizio che supporta i webhook. Per altre informazioni, vedere l'[articolo di Funzioni di Azure sui webhook generici](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Gestione di Funzioni durevoli**: Funzioni durevoli consente di creare funzioni con stato in un ambiente senza server. L'estensione gestisce lo stato, i checkpoint e i riavvii per conto dell'utente. Per altre informazioni, vedere le sezioni relative alle funzioni di Azure in [Funzioni durevoli](/azure/azure-functions/durable-functions-overview).

- **Image Resizer**: questa funzione crea immagini ridimensionate ogni volta che un BLOB viene aggiunto a un contenitore. Il modello accetta un percorso e una stringa di connessione per il trigger, un output immagine di piccole dimensioni e un output immagine di medie dimensioni.

- **Token SAS**: funzione che genera un token di firma di accesso condiviso per un nome BLOB e un contenitore di archiviazione di Azure specificato. Oltre al nome della funzione, questo modello accetta proprietà Path e Connection. La proprietà Path è il percorso dell'account di archiviazione che verrà monitorato dal trigger. L'account di connessione è il nome dell'impostazione dell'app contenente la stringa di connessione dell'account di archiviazione. È necessario impostare anche i **diritti di accesso**. Il livello di autorizzazione controlla se la funzione richiede una chiave API e quale chiave usare: Function usa una chiave di funzione, mentre Admin usa la chiave master. Per altre informazioni, vedere l'esempio [C# Azure Function for generating SAS tokens](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) (Funzione di Azure C# per generare token SAS).
