---
title: Presentazione dell'IDE di Visual Studio
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da6c19341a1e1ab37b38ae4f5379ee5aaace5b87
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954368"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Guida introduttiva: Presentazione dell'IDE di Visual Studio

In questa introduzione della durata di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio verranno presentati alcuni menu, finestre e altre funzionalità dell'interfaccia utente.

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Pagina iniziale

Il primo elemento visualizzato dopo l'apertura di Visual Studio è molto probabilmente la **Pagina iniziale**. La **Pagina iniziale** è progettata come "centro di smistamento" per facilitare l'accesso ai comandi e ai file di progetto necessari più velocemente. Nella sezione **Recenti** sono visualizzati i progetti e le cartelle usati di recente. In **Nuovo progetto** è possibile fare clic su un collegamento per visualizzare la finestra di dialogo **Nuovo progetto** o in **Apri** è possibile aprire un progetto o una cartella di codice esistente. Sulla destra è visualizzato un feed di notizie aggiornate per sviluppatori.

![Pagina iniziale di Visual Studio](media/start-page.png)

Se si chiude la **Pagina iniziale** e si vuole visualizzarla di nuovo, è possibile riaprirla dal menu **File**.

![Menu File di Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Finestra iniziale

All'apertura di Visual Studio viene visualizzata la finestra iniziale. La finestra iniziale consente di iniziare a lavorare con il codice più velocemente. Contiene opzioni per clonare o estrarre il codice, aprire un progetto o una soluzione esistente, creare un nuovo progetto o semplicemente aprire una cartella contenente alcuni file di codice.

[![](media/vs-2019/start-window-labeled.png "Finestra iniziale in Visual Studio 2019")](media/vs-2019/start-window-labeled.png#lightbox)

Se è la prima volta che si usa Visual Studio, l'elenco dei progetti recenti sarà vuoto.

Se si lavora con codebase non basate su MSBuild, usare l'opzione **Apri una cartella locale** per aprire il codice in Visual Studio. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](develop-code-in-visual-studio-without-projects-or-solutions.md). Oppure è possibile creare un nuovo progetto o clonarne uno da un provider di origine, ad esempio GitHub o Azure DevOps.

L'opzione **Continua senza codice** apre semplicemente l'ambiente di sviluppo di Visual Studio senza caricare alcun progetto o codice specifico. Si può scegliere questa opzione per accedere a una sessione di [Live Share](/visualstudio/liveshare/) o connettersi a un processo per il debug. È anche possibile premere **ESC** per chiudere la finestra iniziale e aprire l'IDE.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per continuare a esplorare le funzionalità di Visual Studio si procederà a creare un nuovo progetto.

::: moniker range="vs-2017"

1. Nella casella di ricerca sotto **Nuovo progetto** della **Pagina iniziale** digitare **console** per filtrare l'elenco dei tipi di progetto includendo solo quelli che contengono "console" nel nome.

   ![Cercare nei modelli di progetto nella Pagina iniziale di Visual Studio](media/start-page-search-templates.png)

   Visual Studio mette a disposizione diversi tipi di modelli di progetto che consentono di iniziare a scrivere codice rapidamente. Selezionare un modello di progetto C# **App console (.NET Framework)**. In alternativa, gli sviluppatori che usano Visual Basic, C++, Javascript o altri linguaggi possono creare liberamente un progetto in uno di questi linguaggi. L'interfaccia utente è simile per tutti i linguaggi di programmazione.

1. Nella finestra di dialogo **Nuovo progetto** visualizzata accettare il nome di progetto predefinito e scegliere **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   Viene visualizzata la finestra di dialogo **Crea un nuovo progetto**. Nella finestra è possibile cercare, filtrare e selezionare un modello di progetto. La finestra include anche un elenco dei modelli di progetto usati di recente.

1. Nella casella di ricerca in alto digitare **console** per filtrare l'elenco dei tipi di progetto includendo solo quelli che contengono "console" nel nome. Perfezionare ulteriormente i risultati della ricerca scegliendo **C#** (o un altro linguaggio di propria scelta) nel menu di selezione del **Linguaggio**.

   ![Finestra di dialogo Nuovo progetto di Visual Studio 2019](media/vs-2019/create-a-new-project.png)

1. Se è stato selezionato il linguaggio C#, Visual Basic o F#, selezionare il modello **App console (.NET Framework)** e quindi scegliere **Avanti**. Se è stato selezionato un linguaggio diverso, selezionare qualsiasi modello. L'interfaccia utente è simile per tutti i linguaggi di programmazione.

1. Nella pagina **Configura il nuovo progetto** accettare il nome e il percorso predefiniti per il progetto e scegliere **Crea**.

::: moniker-end

   Il progetto viene creato e nella finestra **Editor** si apre un file denominato *Program.cs*. L'**Editor** mostra il contenuto dei file ed è la posizione in cui si esegue la maggior parte delle operazioni di scrittura del codice in Visual Studio.

   ![Editor di Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Esplora soluzioni

**Esplora soluzioni**, generalmente sul lato destro di Visual Studio, mostra una rappresentazione grafica della gerarchia di file e cartelle nella cartella del progetto, della soluzione o del codice. È possibile esplorare la gerarchia e passare a un file in **Esplora soluzioni**.

![Esplora soluzioni di Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

La barra dei menu nella parte superiore di Visual Studio raggruppa i comandi in categorie. Ad esempio, il menu **Progetto** contiene i comandi correlati al progetto in uso. Dal menu **Strumenti** è possibile personalizzare Visual Studio selezionando **Opzioni** oppure aggiungere funzionalità all'installazione selezionando **Ottieni strumenti e funzionalità**.

::: moniker range="vs-2017"

![Barra dei menu di Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Barra dei menu di Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Elenco errori

Aprire la finestra **Elenco errori** scegliendo **Elenco errori** dal menu **Visualizza**.

Nell'**Elenco errori** sono visualizzati gli errori, gli avvisi e i messaggi riguardanti lo stato corrente del codice. Se il file o il progetto in uso contiene errori, ad esempio una parentesi o un punto e virgola mancante, verranno elencati in questa posizione.

![Elenco errori in Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Output (finestra)

Nella finestra **Output** vengono visualizzati i messaggi di output generati dalla compilazione del progetto e dal provider di controllo del codice sorgente.

Ora si procederà alla compilazione del progetto per esaminare alcuni elementi di output della compilazione. Scegliere **Compila soluzione** dal menu **Compila**. La finestra di **Output** ottiene automaticamente lo stato attivo e visualizza un messaggio di completamento della compilazione.

![Finestra Output di Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Casella di ricerca

La casella di ricerca è un modo rapido e semplice per eseguire pressoché qualsiasi operazione in Visual Studio. È possibile immettere testo correlato all'operazione che si vuole eseguire e verrà visualizzato un elenco di opzioni pertinenti. Ad esempio, si supponga di voler aumentare il livello di dettaglio dell'output di compilazione per visualizzare più informazioni sulle operazioni eseguite esattamente dalla compilazione. Ecco come si può fare:

::: moniker range="vs-2017"

1. Individuare la casella di ricerca **Avvio veloce** in alto a destra nell'IDE. In alternativa premere **CTRL**+**Q** per accedere.

2. Digitare **livello di dettaglio** nella casella di ricerca. Nei risultati visualizzati scegliere **Progetti e soluzioni -> Compila ed Esegui** nella categoria **Opzioni**.

   ![Casella di ricerca di Avvio veloce in Visual Studio 2017](media/quickstart-IDE-quick-launch.png)

   Si apre la pagina delle opzioni **Compila ed esegui** della finestra di dialogo **Opzioni**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Premere **CTRL**+**Q** per attivare la casella di ricerca nella parte superiore dell'IDE.

2. Digitare **livello di dettaglio** nella casella di ricerca. Nei risultati visualizzati scegliere **Modifica livello di dettaglio di MSBuild**.

   ![Casella di ricerca in Visual Studio 2019](media/vs-2019/quick-launch-verbosity.png)

   Si apre la pagina delle opzioni **Compila ed esegui** della finestra di dialogo **Opzioni**.

::: moniker-end

3. In **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi fare clic su **OK**.

4. Compilare di nuovo il progetto facendo clic con il pulsante destro del mouse sul progetto **ConsoleApp1** in **Esplora soluzioni** e scegliendo **Ricompila** dal menu di scelta rapida.

   Questa volta la finestra di **Output** mostra una registrazione più dettagliata del processo di compilazione, inclusi i file copiati e la posizione in cui sono stati copiati.

   ![Output di compilazione dettagliato in Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menu Invia commenti e suggerimenti

Se si verificano problemi durante l'uso di Visual Studio o se si hanno suggerimenti su come migliorare il prodotto, è possibile usare il menu **Invia commenti e suggerimenti** nella parte superiore della finestra di Visual Studio.

::: moniker range="vs-2017"

![Menu commenti e suggerimenti in Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Menu commenti e suggerimenti in Visual Studio 2019](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

Sono state presentate solo alcune delle funzionalità di Visual Studio per iniziare ad acquisire familiarità con l'interfaccia utente. Per esplorare ulteriormente:

> [!div class="nextstepaction"]
> [Informazioni sull'editor del codice](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Guida introduttiva: progetti e soluzioni](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Vedere anche

- [Panoramica dell'IDE di Visual Studio](../get-started/visual-studio-ide.md)
- [Altre funzionalità di Visual Studio](../ide/advanced-feature-overview.md)
- [Modificare i colori del tema e del carattere](../ide/quickstart-personalize-the-ide.md)
