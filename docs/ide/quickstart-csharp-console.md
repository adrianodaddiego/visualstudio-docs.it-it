---
title: Usare Visual Studio per creare la prima app console C#
titleSuffix: ''
description: Informazioni dettagliate su come creare un'app console Hello World semplice in Visual Studio con C#.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 34e943984755ff1f36f8a28134e1e2abde4312d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954074"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app console C#

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice app C# eseguita nella console.

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) per installarlo gratuitamente.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione C#. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **C#** e quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al progetto il nome *HelloWorld*.

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Se non viene visualizzato il modello di progetto **Applicazione console (.NET Core)**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

   ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

     ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C#**  dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **App console (.NET Core)** e quindi scegliere **Avanti**.

   ![Scegliere il modello C# per l'app console (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Se il modello **App console (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Scegliere quindi il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura "[Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere **Crea**.

   ![Nella finestra Configura il nuovo progetto assegnare al progetto il nome "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio aprirà il nuovo progetto.
   
::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

::: moniker range="vs-2017"

Dopo la selezione del modello di progetto C# e l'assegnazione di un nome al progetto, in Visual Studio viene creata una semplice applicazione "Hello World".

::: moniker-end

::: moniker range="vs-2019"

Visual Studio inserisce il codice di "Hello World" predefinito nel progetto.

::: moniker-end

A tale scopo, chiama il metodo <xref:System.Console.WriteLine%2A> per visualizzare la stringa letterale "Hello World!" nella finestra della console.

   ![Visualizzare il codice Hello World predefinito dal modello](../ide/media/csharp-console-helloworld-template.png)

Se si preme **F5** è possibile eseguire il programma in modalità di debug. La finestra della console resta comunque visibile per un istante, quindi viene chiusa.

Ciò accade perché il metodo `Main` termina dopo l'esecuzione dell'unica istruzione, quindi l'applicazione viene chiusa.

### <a name="add-some-code"></a>Aggiungere codice

È possibile aggiungere codice per sospendere l'applicazione in modo che la finestra della console non venga chiusa fino a quando non si preme **INVIO**.

1. Aggiungere il codice seguente subito dopo la chiamata al metodo <xref:System.Console.WriteLine%2A>:

   ```csharp
   Console.ReadLine();
   ```

1. Verificare che il codice sia simile al seguente nell'editor del codice:

   ![Aggiungere codice per sospendere l'app Hello World](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Fare clic sul pulsante **HelloWorld** sulla barra degli strumenti per eseguire l'applicazione in modalità di debug. In alternativa, è possibile premere **F5**.

   ![Fare clic sul pulsante HelloWorld per eseguire l'app dalla barra degli strumenti](../ide/media/csharp-console-hello-world-button.png)

1. Visualizzare l'app nella finestra della console.

   ![Finestra della console che mostra Hello World!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Chiudere l'applicazione

1. Premere **INVIO** per chiudere la finestra della console.

1. Chiudere il riquadro **Output** in Visual Studio.

   ![Chiudere il riquadro Output in Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Chiudere Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C# e dell'IDE di Visual Studio. Per altre informazioni, continuare con le esercitazioni seguenti.

> [!div class="nextstepaction"]
> [Introduzione a un'app console C# in Visual Studio](../get-started/csharp/tutorial-console.md)
