---
title: Creare un'app Windows Forms con Visual Basic
description: Informazioni dettagliate su come creare un'app Windows Forms in Visual Studio con Visual Basic.
ms.date: 03/23/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 4619a56bfe052a1fb191af8edfd1cef8b376617b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976912"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Creare un'app Windows Forms in Visual Studio con Visual Basic

In questa breve introduzione all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione di Visual Basic con un'interfaccia utente basata su Windows.

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) per installarlo gratuitamente.

> [!NOTE]
> Alcune delle schermate contenute in questa esercitazione usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](../ide/quickstart-personalize-the-ide.md).

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

In primo luogo si creerà un progetto di applicazione Visual Basic. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **Desktop di Windows**. Nel riquadro centrale scegliere il modello **App Windows Forms (.NET Framework)**. Assegnare al file il nome `HelloWorld`.

     Se non viene visualizzato il modello del progetto **App Windows Forms (.NET Framework)**, chiudere la finestra di dialogo **Nuovo progetto** e nella barra dei menu superiore scegliere **Strumenti** > **Ottieni strumenti e funzionalità**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET**, quindi scegliere **Modifica**.

     ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *Windows Forms* nella casella di ricerca. Quindi scegliere **Visual Basic** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **App Windows Forms (.NET Core)** e quindi scegliere **Avanti**.

   ![Scegliere il modello Visual Basic per l'app Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Se il modello **App Windows Forms (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Scegliere quindi il carico di lavoro **Sviluppo per desktop .NET** nel programma di installazione di Visual Studio.
   > 
   > ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Scegliere quindi il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura "[Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere **Crea**.

   ![Nella finestra Configura il nuovo progetto assegnare al progetto il nome "HelloWorld"](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

Dopo aver selezionato il modello di progetto Visual Basic e assegnato un nome al file, in Visual studio viene aperto un modulo. Un modulo è un'interfaccia utente di Windows. Ora si crea un'applicazione "Hello World" aggiungendo controlli al modulo, quindi si esegue l'applicazione.

### <a name="add-a-button-to-the-form"></a>Aggiungere un pulsante al modulo

1. Fare clic su **Casella degli strumenti** per aprire la finestra a comparsa della casella degli strumenti.

     ![Fare clic su Casella degli strumenti per aprire la finestra della casella degli strumenti](../ide/media/vb-toolbox-toolwindow.png)

     (Se la finestra a comparsa della **Casella degli strumenti** non viene visualizzata, è possibile aprirla premendo **CTRL**+**ALT**+**X**.)

2. Fare clic sull'icona **Blocca** per ancorare la **Casella degli strumenti**.

     ![Fare clic sull'icona Blocca per ancorare la Casella degli strumenti all'IDE](../ide/media/vb-pin-the-toolbox-window.png)

3. Fare clic sul controllo **Pulsante** e trascinarlo nel modulo.

     ![Aggiungere un pulsante al modulo](../ide/media/vb-add-a-button-to-form1.png)

4. Nella sezione **Aspetto** o nella sezione **Tipi di carattere** della finestra **Proprietà** digitare `Click this` e quindi premere **INVIO**.

     ![Aggiungere testo al pulsante nel modulo](../ide/media/vb-button-control-text.png)

     (Se la finestra **Proprietà** non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo fare clic su **Visualizza** > **Finestra Proprietà**. In alternativa premere **F4**.)

5. Nella sezione **Progettazione** della finestra **Proprietà** cambiare il nome da **Button1** a `btnClickThis`, quindi premere **INVIO**.

     ![Aggiungere una funzione al pulsante nel modulo](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Aggiungere un'etichetta al modulo

È stato aggiunto un controllo pulsante per creare un'azione. Ora si aggiungerà un controllo etichetta al quale inviare del testo.

1. Selezionare il controllo **Etichetta** nella **Casella degli strumenti**, quindi trascinarlo sul modulo e rilasciarlo sotto il pulsante **Click this**.

2. Nella sezione **Progettazione** della finestra **Proprietà** cambiare il nome da **Label1** a `lblHelloWorld`, quindi premere **INVIO**.

### <a name="add-code-to-the-form"></a>Aggiungere codice al modulo

1. Nella finestra**Form1.vb &#91;Design&#93;** fare doppio clic sul pulsante **Click this** per aprire la finestra **Form1.vb**.

      In alternativa è possibile espandere **Form1.vb** in **Esplora soluzioni** e quindi fare clic su **Form1**.

2. Nella finestra **Form1.vb**, tra la riga **Private Sub** e la riga **End Sub** (o tra la riga **Public Class Form1** e la riga **End Class**), digitare il codice seguente.

     ![Aggiungere codice al modulo](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Fare clic sul pulsante **Avvia** per eseguire l'applicazione.

     ![Fare clic su Avvia per eseguire il debug e avviare l'app](../ide/media/vb-click-start-hello-world.png)

   Vengono eseguite diverse operazioni. Nell'IDE di Visual Studio viene aperta la finestra **Strumenti di diagnostica** e anche una finestra **Output**. All'esterno dell'IDE viene visualizzata una finestra di dialogo **Form1**. La finestra include il pulsante **Click this** e il testo **Label1**.

2. Fare clic sul pulsante **Click this** nella finestra di dialogo **Form1**. Osservare che il testo **Label1** diventa **Hello World!**.

    ![Finestra di dialogo Form1 con il testo Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di Visual Basic e dell'IDE di Visual Studio. Per approfondire ancora le conoscenze, continuare con un'esercitazione nella sezione **Esercitazioni** del sommario.

## <a name="see-also"></a>Vedere anche

* [Guida introduttiva: Creare un'app console in Visual Studio con Visual Basic](quickstart-visual-basic-console.md)
* [Learn more about Visual Basic IntelliSense](visual-basic-specific-intellisense.md) (Altre informazioni su Visual Basic IntelliSense)
