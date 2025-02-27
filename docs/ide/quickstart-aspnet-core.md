---
title: Creare un'app Web ASP.NET Core in C#
description: Informazioni dettagliate su come creare un'app Web Hello World in Visual Studio con C# e ASP.NET Core.
ms.custom: mvc,seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: ea01ff2671212c8dfeb023d145cfd224a5feb2f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954757"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app Web ASP.NET Core

In questa introduzione di 5-10 minuti che spiega come usare Visual Studio viene creata un'app Web "Hello World" semplice tramite un modello di progetto ASP.NET e il linguaggio di programmazione C#.

## <a name="before-you-begin"></a>Prima di iniziare

### <a name="install-visual-studio"></a>Installare Visual Studio

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) per installarlo gratuitamente.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Scegliere il tema (facoltativo)

Questa esercitazione introduttiva include screenshot in cui viene usato il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](quickstart-personalize-the-ide.md).

## <a name="create-a-project"></a>Creare un progetto

Per iniziare, creare un progetto di applicazione Web ASP.NET Core. Il tipo di progetto include fin dall'inizio tutti i file di modello necessari per creare un'app Web.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

1. Nel riquadro a sinistra della finestra di dialogo **Nuovo progetto** espandere **Visual C#** e scegliere **.NET Core**. Nel riquadro centrale scegliere **Applicazione Web ASP.NET Core**. <br/><br/>Denominare il file `HelloWorld` e scegliere **OK**.

   ![Creare un progetto dell'applicazione Web ASP.NET Core per C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Se non viene visualizzata la categoria dei modelli di progetto **.NET Core** scegliere il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro. A seconda delle impostazioni di visualizzazione, potrebbe essere necessario scorrere la pagina per visualizzarla.
   >
   > ![Aprire Programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](../ide/media/open-visual-studio-installer.png)
   >
   > Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.
   >
   > ![Carico di lavoro ASP.NET nel programma di installazione di Visual Studio](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Potrebbe essere necessario chiudere Visual Studio prima di continuare l'installazione del nuovo carico di lavoro.)

1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** selezionare **ASP.NET Core 2.1** nel menu a discesa in alto. Scegliere quindi **Applicazione Web** e **OK**.

   ![Finestra di dialogo Nuova applicazione Web ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Se **ASP.NET Core 2.1** o versione successiva non è visualizzato, verificare che si stia usando la versione più recente di Visual Studio. Per altre informazioni su come aggiornare l'installazione, vedere la pagina [Aggiornare Visual Studio alla versione più recente](../install/update-visual-studio.md).

Dopo pochi istanti, Visual Studio apre il file di progetto.

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *ASP.NET* nella casella di ricerca. Scegliere quindi **C#**  dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma.

   Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **Applicazione Web ASP.NET Core**, quindi scegliere **Avanti**.

   ![Scegliere il modello C# per l'applicazione Web ASP.NET Core](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Se il modello **Applicazione Web ASP.NET Core** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > A questo punto scegliere il carico di lavoro **Sviluppo ASP.NET e Web** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Applicazione Web ASP.NET Core nel programma di installazione di Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura "[Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere **Crea**.

   ![Nella finestra Configura il nuovo progetto assegnare al progetto il nome "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. Nella finestra **Crea una nuova applicazione Web ASP.NET Core** verificare che **ASP.NET Core 2.1** o versione successiva venga visualizzato nel menu a discesa in alto. Scegliere quindi **Applicazione Web** che include un esempio di Razor Pages. Infine scegliere **Crea**.

   ![Finestra Crea una nuova applicazione Web ASP.NET Core](../get-started/csharp/media/vs-2019/csharp-create-aspnet-core-razor-pages-app.png)

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-and-run-the-app"></a>Creare ed eseguire l'app

1. In **Esplora soluzioni** espandere la cartella **Pagine** e quindi scegliere **About.cshtml**.

   ![Scegliere il file About.cshtml in Esplora soluzioni](../ide/media/csharp-aspnet-about-page-html-file.png)

   Questo file corrisponde a una pagina denominata **Informazioni su** nell'app Web, eseguita in un Web browser.

   ![Pagina di informazioni nell'app Web](../ide/media/csharp-aspnet-about-page.png)

   Nell'editor viene visualizzato il codice HTML per l'area delle "informazioni aggiuntive" della pagina **Informazioni su**.

   ![Codice HTML per l'area delle informazioni aggiuntive nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Modificare il testo "informazioni aggiuntive" in "**Hello World!**".

   ![Modifica del codice HTML predefinito per l'area delle informazioni aggiuntive nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. In **Esplora soluzioni** espandere **About.cshtml** e quindi scegliere **About.cshtml**. Questo file corrisponde anche alla pagina **Informazioni su** di un Web browser.

   ![Scegliere il file About.cshtml in Esplora soluzioni](../ide/media/csharp-aspnet-about-page-code-file.png)

   Nell'editor si noterà il codice C# che include il testo per l'area della "descrizione dell'applicazione" della pagina **Informazioni su**.

   ![Codice C# per l'area della descrizione dell'applicazione nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Modificare il testo del messaggio "descrizione dell'applicazione" in "**Qual è il mio messaggio?**".

   ![Modifica del testo del messaggio predefinito per l'area della descrizione dell'applicazione nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Scegliere **IIS Express** o premere **CTRL**+**F5** per eseguire l'app e aprirla in un Web browser.

   ![Selezionare il pulsante IIS Express in Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Se viene visualizzato il messaggio di errore **Impossibile connettersi al server Web "IIS Express"** o un messaggio di errore in cui viene indicato un certificato SSL, chiudere Visual Studio. Aprire quindi Visual Studio usando l'opzione **Esegui come amministratore** dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.

1. Nel Web browser verificare che la pagina **Informazioni su** includa il testo aggiornato.

   ![Visualizzare la pagina About aggiornata che include le modifiche apportate](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Chiudere il Web browser.

### <a name="review-your-work"></a>Rivedere il lavoro

Visualizzare l'animazione seguente per verificare il lavoro completato nella sezione precedente.

  ![Visualizzare il file animato con estensione gif che illustra come creare ed eseguire una semplice app Web ASP.NET Core C# in Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C#, ASP.NET Core e dell'IDE (ambiente di sviluppo integrato) di Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, continuare con l'esercitazione seguente:

> [!div class="nextstepaction"]
> [Introduzione a C# e ad ASP.NET Core in Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Vedere anche

[Publish your web app to Azure App Service by using Visual Studio](../deployment/quickstart-deploy-to-azure.md) (Pubblicare l'app Web in Servizio app di Azure con Visual Studio)
