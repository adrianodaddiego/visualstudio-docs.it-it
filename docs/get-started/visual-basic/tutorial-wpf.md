---
title: App Hello World con WPF in Visual Basic
description: Creare una semplice app Windows Desktop .NET in Visual Basic con Visual Studio usando il framework di interfaccia utente Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 04/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: conceptual
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f56482dbbe76722e8b8d55fad01d283de2dc113e
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263620"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Esercitazione: Creare un'applicazione semplice con Visual Basic

Completando questa esercitazione, si acquisirà familiarità con molti strumenti, finestre di dialogo e finestre di progettazione che è possibile usare quando si sviluppano applicazioni con Visual Studio. Si creerà un' applicazione "Hello, World", si progetterà l'interfaccia utente, si aggiungerà il codice e si eseguirà il debug degli errori, apprendendo l'uso dell'ambiente di sviluppo integrato ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) per installarlo gratuitamente.

::: moniker-end

## <a name="configure-the-ide"></a>Configurare IDE

::: moniker range="vs-2017"

Quando si apre per la prima volta, Visual Studio richiede di eseguire l'accesso. Questo passaggio è facoltativo per questa esercitazione. È possibile che venga visualizzata una finestra di dialogo in cui viene chiesto di scegliere le impostazioni di sviluppo e il tema colori. Mantenere i valori predefiniti e scegliere **Avvia Visual Studio**.

![Finestra di dialogo Selezionare le impostazioni](../media/exploreide-settings.png)

Dopo aver avviato Visual Studio, saranno visualizzati le finestre degli strumenti, i menu, le barre degli strumenti e l'area della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione, con **Avvio veloce**, la barra dei menu e la barra degli strumenti standard nella parte superiore. Al centro della finestra dell'applicazione si trova **Pagina iniziale**. Quando si carica una soluzione o un progetto, gli editor e le finestre di progettazione vengono visualizzati nello spazio in cui si trova la **pagina iniziale** . Quando si sviluppa un'applicazione, per la maggior parte del tempo si usa quest'area centrale.

![Visual Studio 2017 IDE con impostazioni generali applicate](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Quando si avvia Visual Studio, si apre la finestra iniziale. Selezionare **Continua senza codice** per aprire l'ambiente di sviluppo. Saranno visualizzate le finestre degli strumenti, i menu, barre degli strumenti e lo spazio della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione, con una casella di ricerca, la barra dei menu e la barra degli strumenti standard nella parte superiore. Quando si carica una soluzione o un progetto, gli editor e le finestre di progettazione vengono visualizzati nell'area al centro della finestra dell'applicazione. Quando si sviluppa un'applicazione, per la maggior parte del tempo si usa quest'area centrale.

::: moniker-end

## <a name="create-the-project"></a>Creare il progetto

Quando si crea un'applicazione in Visual Studio, è innanzitutto necessario creare un progetto e una soluzione. In questo esempio verrà creato un progetto Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Creare un nuovo progetto. Nella barra dei menu selezionare **File** > **Nuovo** > **Progetto**.

     ![Nella barra dei menu scegliere File, Nuovo, Progetto](../media/exploreide-filenewproject.png)

2. Nella finestra di dialogo **Nuovo progetto** selezionare la categoria **Installati** > **Visual Basic** > **Windows Desktop** e quindi selezionare il modello **App WPF (.NET Framework)** . Assegnare al progetto il nome **HelloWPFApp** e scegliere **OK**.

     ![Modello App WPF nella finestra di dialogo Nuovo progetto di Visual Studio](media/exploreide-newproject-vb.png)

Visual Studio crea il progetto e la soluzione HelloWPFApp e in **Esplora soluzioni** vengono visualizzati i vari file. **WPF Designer** include una doppia visualizzazione con una visualizzazione Progettazione e una visualizzazione XAML di *MainWindow.xaml*. È possibile far scorrere la barra di divisione in modo da mostrare più o meno elementi in ciascuna visualizzazione. È possibile scegliere di visualizzare solo la visualizzazione degli elementi visivi o solo la visualizzazione XAML. In **Esplora soluzioni**vengono visualizzati gli elementi indicati di seguito.

![Esplora soluzioni con i file HelloWPFApp caricati](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

2. Nella schermata **Crea un nuovo progetto** cercare "WPF", scegliere **App WPF (.NET Framework)** e quindi scegliere **Avanti**.

   ![Modello App WPF nella finestra di dialogo Nuovo progetto di Visual Studio](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Nella schermata successiva assegnare al progetto il nome **HelloWPFApp** e scegliere **Crea**.

Visual Studio crea il progetto e la soluzione HelloWPFApp e in **Esplora soluzioni** vengono visualizzati i vari file. **WPF Designer** include una doppia visualizzazione con una visualizzazione Progettazione e una visualizzazione XAML di *MainWindow.xaml*. È possibile far scorrere la barra di divisione in modo da mostrare più o meno elementi in ciascuna visualizzazione. È possibile scegliere di visualizzare solo la visualizzazione degli elementi visivi o solo la visualizzazione XAML. In **Esplora soluzioni**vengono visualizzati gli elementi indicati di seguito.

![Esplora soluzioni con i file HelloWPFApp caricati](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> Per altre informazioni su XAML (eXtensible Application Markup Language), vedere la [panoramica di XAML per WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Dopo aver creato il progetto, sarà possibile personalizzarlo. Nella finestra **Proprietà** (disponibile nel menu **Visualizzazione** ) è possibile visualizzare e modificare le opzioni per elementi di progetto, controlli e altri elementi in un'applicazione.

### <a name="change-the-name-of-mainwindowxaml"></a>Cambiare il nome di MainWindow.xaml

Assegnare a MainWindow un nome più specifico.

1. In **Esplora soluzioni**selezionare *MainWindow.xaml*. Verrà visualizzata la finestra **Proprietà**, altrimenti scegliere il menu **Visualizzazione** e l'elemento **Finestra Proprietà**.

1. Cambiare la proprietà **Nome file** in `Greetings.xaml`.

     ![Finestra Proprietà con il nome file evidenziato](../media/exploreide-filenameinpropertieswindow.png)

     **Esplora soluzioni** indica che il nome del file è ora *Greetings.xaml* e che il nome del file di codice annidato è ora *Greetings.xaml.vb*. Questo file di codice è annidato sotto il nodo del file con estensione *xaml*, a indicare che sono strettamente correlati tra loro.

## <a name="design-the-user-interface-ui"></a>Progettare l'interfaccia utente

Verranno aggiunti tre tipi di controlli all'applicazione: un controllo <xref:System.Windows.Controls.TextBlock>, due controlli <xref:System.Windows.Controls.RadioButton> e un controllo <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Aggiungere un controllo TextBlock

1. Premere **CTRL**+**Q** per attivare la casella di ricerca e digitare **Casella degli strumenti**. Scegliere **Visualizza > Casella degli strumenti** dall'elenco dei risultati.

2. Nella **casella degli strumenti** espandere il nodo **Controlli WPF comuni** per visualizzare il controllo TextBlock.

     ![Casella degli strumenti con il controllo TextBlock evidenziato](../media/exploreide-textblocktoolbox.png)

3. Aggiungere un controllo TextBlock all'area di progettazione scegliendo l'elemento **TextBlock** e trascinandolo nell'area di progettazione nella finestra. Centrare il controllo nella parte superiore della finestra.

La finestra dovrebbe essere simile a quella illustrata nella figura di seguito.

![Controllo TextBlock nel modulo di messaggi di apertura](../media/exploreide-greetingswithtextblockonly.png)

Il markup XAML sarà simile all'esempio seguente:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Personalizzare il testo nel blocco di testo

1. Nella visualizzazione XAML individuare il markup di TextBlock e modificare l'attributo Text:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. Se necessario, riallineare al centro il controllo TextBlock e salvare le modifiche premendo CTRL+S o usando la voce di menu **File**.

Verranno successivamente aggiunti due controlli [RadioButton](/dotnet/framework/wpf/controls/radiobutton) al form.

### <a name="add-radio-buttons"></a>Aggiungere pulsanti di opzione

1. Nella **casella degli strumenti** cercare il controllo **RadioButton**.

     ![Finestra Casella degli strumenti con il controllo RadioButton selezionato](../media/exploreide-radiobuttontoolbox.png)

2. Aggiungere due controlli RadioButton all'area di progettazione scegliendo l'elemento **RadioButton** e trascinandolo nell'area di progettazione nella finestra. Selezionare i pulsanti e usare i tasti di direzione per spostare i pulsanti in modo che vengano visualizzati affiancati sotto il controllo TextBlock.

     La finestra dovrebbe risultare simile alla seguente:

     ![Modulo di messaggi di apertura con controllo TextBlock e due pulsanti di opzione](../media/exploreide-greetingswithradiobuttons.png)

3. Nella finestra **Proprietà** per il controllo RadioButton sinistro modificare la proprietà **Nome** (la proprietà nella parte superiore della finestra **Proprietà** ) in `HelloButton`.

     ![Finestra delle proprietà di RadioButton](../media/exploreide-buttonproperties.png)

4. Nella finestra **Proprietà** per il controllo RadioButton destro modificare la proprietà **Nome** in `GoodbyeButton`, quindi salvare le modifiche.

È ora possibile aggiungere il testo visualizzato per ogni controllo RadioButton. Nella procedura seguente verrà aggiornata la proprietà **Contenuto** per un controllo RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Aggiungere testo visualizzato per ogni pulsante di opzione

1. Nell'area di progettazione aprire il menu di scelta rapida di HelloButton facendo clic con il pulsante destro del mouse su HelloButton, quindi scegliere **Modifica testo** e immettere `Hello`.

2. Aprire il menu di scelta rapida per GoodbyeButton facendo clic con il pulsante destro del mouse su GoodbyeButton, quindi scegliere **Modifica testo** e immettere `Goodbye`.

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Impostare un pulsante di opzione che deve essere selezionato per impostazione predefinita

In questo passaggio il pulsante di opzione HelloButton viene impostato in modo che sia selezionato per impostazione predefinita, così che uno dei due pulsanti di opzione sia sempre selezionato.

Nella visualizzazione XAML individuare il markup per HelloButton e aggiungere un attributo **IsChecked**:

```xaml
IsChecked="True"
```

L'elemento finale dell'interfaccia utente da aggiungere è un controllo [Button](/dotnet/framework/wpf/controls/button).

### <a name="add-the-button-control"></a>Aggiungere il controllo del pulsante

1. Nella **casella degli strumenti** cercare il controllo **Button** e aggiungerlo all'area di progettazione sotto i controlli RadioButton trascinandolo nel modulo nella visualizzazione Progettazione.

2. Nella visualizzazione XAML modificare il valore di **Contenuto** per il controllo Button da `Content="Button"` a `Content="Display"`, e salvare le modifiche.

     Il markup deve essere simile all'esempio seguente: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     La finestra dovrebbe essere simile a quella illustrata nella figura di seguito.

     ![Form di messaggi di apertura con etichette del controllo](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Aggiungere codice al pulsante Visualizza

Quando l'applicazione è in esecuzione, si apre una finestra di messaggio se si sceglie un pulsante di opzione e si seleziona il pulsante **Visualizza**. Verranno visualizzate una finestra di messaggio per Hello e una per Goodbye. Per creare questo comportamento, è necessario aggiungere codice all'evento `Button_Click` in *Greetings.xaml.vb* o *Greetings.xaml.cs*.

1. Nell'area di progettazione fare doppio clic sul pulsante **Visualizza** .

     Viene visualizzato il file *Greetings.xaml.vb* con il cursore nell'evento `Button_Click`.

    ```vb
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

2. Immettere il codice seguente:

    ```vb
    If HelloButton.IsChecked = True Then
        MessageBox.Show("Hello.")
    ElseIf GoodbyeButton.IsChecked = True Then
        MessageBox.Show("Goodbye.")
    End If
    ```

3. Salvare l'applicazione.

## <a name="debug-and-test-the-application"></a>Eseguire il debug e il test dell'applicazione

Verrà quindi eseguito il debug dell'applicazione per rilevare eventuali errori e verificare che entrambe le finestre di messaggio vengano visualizzate correttamente. Le istruzioni seguenti indicano come compilare e avviare il debugger, ma in un secondo momento può essere utile leggere [Compilare un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) e [Debug WPF](../../debugger/debugging-wpf.md) per altre informazioni.

### <a name="find-and-fix-errors"></a>Trovare e correggere errori

In questo passaggio verrà identificato l'errore generato in precedenza modificando il nome del file *MainWindow.xaml*.

#### <a name="start-debugging-and-find-the-error"></a>Avviare il debug e trovare l'errore

1. Avviare il debugger premendo **F5** o selezionando **Debug**, quindi **Avvia debug**.

   Si apre la finestra **Modalità interruzione**. La finestra **Output** indica che si è verificata un'eccezione IOException: Impossibile individuare la risorsa 'mainwindow.xaml'.

   ![Screenshot del messaggio IOException](../media/exploreide-ioexception.png)

2. Arrestare il debugger scegliendo **Debug** > **Termina debug**.

Il file *MainWindow.xaml* è stato rinominato come *Greetings.xaml* all'inizio di questa esercitazione, ma il codice fa ancora riferimento a *MainWindow.xaml* come URI di avvio per l'applicazione. Di conseguenza il progetto non può essere avviato.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Specificare Greetings.xaml come URI di avvio

1. In **Esplora soluzioni** aprire il file *Application.xaml*.

2. Modificare `StartupUri="MainWindow.xaml"` in `StartupUri="Greetings.xaml"`, quindi salvare le modifiche.

Avviare nuovamente il debugger premendo **F5**. Viene visualizzata la finestra **Greetings** dell'applicazione. Chiudere la finestra dell'applicazione per arrestare il debug.

### <a name="debug-with-breakpoints"></a>Eseguire il debug con punti di interruzione

Aggiungendo alcuni punti di interruzione, è possibile testare il codice durante il debug. È possibile aggiungere punti di interruzione selezionando **Debug** > **Imposta/Rimuovi punto di interruzione**, facendo clic sul margine sinistro dell'editor accanto alla riga di codice in cui si vuole inserire l'interruzione oppure premendo **F9**.

#### <a name="add-breakpoints"></a>Aggiungere punti di interruzione

1. Aprire *Greetings.xaml.vb* e selezionare la riga seguente: `MessageBox.Show("Hello.")`

2. Aggiungere un punto di interruzione dal menu premendo **F9** o selezionando **Debug**, quindi **Attiva/disattiva punto di interruzione**.

   Accanto alla riga di codice nel margine di estrema sinistra della finestra dell'editor verrà visualizzato un cerchio rosso.

3. Selezionare la riga seguente: `MessageBox.Show("Goodbye.")`.

4. Premere **F9** per aggiungere un punto di interruzione e poi premere **F5** per avviare il debug.

5. Nella finestra **Greetings** scegliere il pulsante di opzione **Hello** , quindi il pulsante **Visualizza** .

   La riga `MessageBox.Show("Hello.")` viene evidenziata in giallo. Nella parte inferiore dell'IDE, le finestre Auto, Variabili locali ed Espressioni di controllo sono ancorate insieme sul lato sinistro e le finestre Stack di chiamate, Punti di interruzione, Impostazioni eccezione, Comando, Controllo immediato e Output sono ancorate insieme sul lato destro.

   ![Screenshot del punto di interruzione nel debugger](media/exploreide-debugbreakpoint.png)

6. Nella barra dei menu scegliere **Debug** > **Esci da istruzione/routine**.

     L'applicazione riprende l'esecuzione e verrà visualizzata una finestra di messaggio con la parola "Hello".

7. Scegliere il pulsante **OK** per chiudere la finestra di messaggio.

8. Nella finestra **Greetings** scegliere il pulsante di opzione **Goodbye** , quindi il pulsante **Visualizza** .

     La riga `MessageBox.Show("Goodbye.")` viene evidenziata in giallo.

9. Scegliere **F5** per proseguire con il debug. Quando verrà visualizzata la finestra del messaggio, scegliere il pulsante **OK** per chiuderla.

10. Chiudere la finestra dell'applicazione per arrestare il debug.

11. Nella barra dei menu scegliere **Debug** > **Disabilita tutti i punti di interruzione**.

### <a name="build-a-release-version-of-the-application"></a>Compilare una versione di rilascio dell'applicazione

Dopo aver verificato che tutto funzioni, è possibile preparare una build di rilascio dell'applicazione.

1. Nel menu principale selezionare **Compila** > **Pulisci soluzione** per eliminare i file intermedi e di output creati durante le compilazioni precedenti. Questa operazione non è necessaria, ma elimina l'output di compilazione di debug.

2. Modificare la configurazione della build per HelloWPFApp da **Debug** a **Rilascio** usando il controllo a discesa sulla barra degli strumenti (al momento è selezionato "Debug").

3. Compilare la soluzione scegliendo **Compila** > **Compila soluzione**.

L'esercitazione è stata completata. È possibile trovare il file con estensione *exe* compilato nella directory del progetto e della soluzione ( *…\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Vedere anche

::: moniker range="vs-2017"

- [Novità di Visual Studio 2017](../../ide/whats-new-visual-studio-2017.md)
- [Suggerimenti per la produttività](../../ide/productivity-tips-for-visual-studio.md)

::: moniker-end

::: moniker range="vs-2019"

- [Novità di Visual Studio 2019](../../ide/whats-new-visual-studio-2019.md)
- [Suggerimenti per la produttività](../../ide/productivity-tips-for-visual-studio.md)

::: moniker-end