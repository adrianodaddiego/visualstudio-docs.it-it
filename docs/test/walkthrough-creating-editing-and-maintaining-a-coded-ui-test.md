---
title: Creare un test codificato dell'interfaccia utente
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 54ebc36f9dd18010e07403c3b9692b62b2380d99
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976304"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Procedura dettagliata: Creare, modificare e gestire un test codificato dell'interfaccia utente

Questa procedura dettagliata insegna come creare, modificare e gestire un test codificato dell'interfaccia utente per testare un'app di Windows Presentation Framework (WPF). Nella procedura dettagliata vengono fornite le soluzioni per correggere i test interrotti da vari problemi di temporizzazione e dal refactoring dei controlli.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Creare un'app WPF

1. Creare un nuovo progetto **App WPF (.NET Framework)** e denominarlo **SimpleWPFApp**.

     Si apriranno **WPF Designer** e la finestra MainWindow del progetto.

2. Aprire la casella degli strumenti, se non è già aperta. Scegliere il menu **Visualizza** e quindi **Casella degli strumenti**.

3. Nella sezione **Tutti i controlli di WPF** trascinare i controlli **Button**, **CheckBox** e **ProgressBar** su MainWindow nell'area di progettazione.

4. Selezionare il controllo **Button**. Nella finestra **Proprietà** modificare il valore della proprietà **Name** da \<No Name> a button1. Modificare quindi il valore della proprietà **Content** da Button a Start.

5. Selezionare il controllo **ProgressBar**. Nella finestra **Proprietà** modificare il valore della proprietà **Name** da \<No Name> a progressBar1. Modificare quindi il valore della proprietà **Maximum** da **100** a **10000**.

6. Selezionare il controllo **Checkbox**. Nella finestra **Proprietà** modificare il valore della proprietà **Name** da \<No Name> a checkBox1 e quindi deselezionare la proprietà **IsEnabled**.

     ![Applicazione WPF semplice](../test/media/codedui_wpfapp.png)

7. Fare doppio clic sul pulsante per aggiungere un gestore eventi Click.

     *MainWindow.xmal.cs* viene visualizzato nell'editor del codice con il cursore nel nuovo metodo button1_Click.

8. Nella parte superiore della classe MainWindow aggiungere un delegato, che verrà usato per l'indicatore di stato. Per aggiungere il delegato, aggiungere il codice seguente:

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }
    ```

9. Nel metodo button1_Click aggiungere il codice seguente:

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        double progress = 0;

        ProgressBarDelegate updatePbDelegate =
            new ProgressBarDelegate(progressBar1.SetValue);

        do
        {
            progress ++;

            Dispatcher.Invoke(updatePbDelegate,
                System.Windows.Threading.DispatcherPriority.Background,
                new object[] { ProgressBar.ValueProperty, progress });
            progressBar1.Value = progress;
        }
        while (progressBar1.Value != progressBar1.Maximum);

        checkBox1.IsEnabled = true;
    }
    ```

10. Salvare il file.

### <a name="run-the-wpf-app"></a>Eseguire l'app WPF

1. Nel menu **Debug** scegliere **Avvia debug** o premere **F5**.

2. Si noti che il controllo CheckBox è disabilitato. Scegliere **Avvia**.

     L'indicatore di stato dovrebbe essere completato al 100% in pochi secondi.

3. È ora possibile selezionare il controllo CheckBox.

4. Chiudere SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Creare un collegamento all'app WPF

1. Individuare l'applicazione SimpleWPFApp creata precedentemente.

2. Creare un collegamento sul desktop all'applicazione SimpleWPFApp. Fare clic con il pulsante destro del mouse su *SimpleWPFApp.exe* e scegliere **Copia**. Sul desktop fare clic con il pulsante destro del mouse e scegliere **Incolla collegamento**.

    > [!TIP]
    > Un collegamento all'applicazione rende più facile aggiungere o modificare i test codificati dell'interfaccia utente per l'applicazione, perché consente di avviare rapidamente l'applicazione.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Creare un test codificato dell'interfaccia utente per SimpleWPFApp

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Aggiungi** > **Nuovo progetto**.

2. Cercare e selezionare il modello di progetto **Progetto di test codificato dell'interfaccia utente** e procedere con i passaggi necessari per creare il nuovo progetto.

   > [!NOTE]
   > Se non viene visualizzato il modello **Progetto di test codificato dell'interfaccia utente**, è necessario [installare il componente di test codificato dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

     Il nuovo progetto di test codificato dell'interfaccia utente denominato **CodedUITestProject1** viene aggiunto alla soluzione e viene visualizzata la finestra di dialogo **Genera codice per test codificato dell'interfaccia utente**.

1. Selezionare l'opzione **Registra azioni, modifica mappa dell'interfaccia utente o aggiungi asserzioni** e fare clic su **OK**.

     Viene visualizzata la finestra di dialogo **UIMap – Generatore di test codificati dell'interfaccia utente** e Visual Studio è ridotto a icona.

     Per altre informazioni sulle opzioni disponibili nella finestra di dialogo, vedere [Creare test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md).

1. Scegliere **Avvia registrazione** nella finestra di dialogo **UIMap - Generatore di test codificati dell'interfaccia utente**.

     ![Avviare la registrazione](../test/media/cuit_builder_record.png)

     Se necessario, è possibile sospendere la registrazione, ad esempio per controllare la posta elettronica in arrivo.

     ![Sospendere la registrazione](../test/media/cuit_.png)

    > [!WARNING]
    > Tutte le azioni eseguite sul desktop verranno registrate. Sospendere la registrazione se si eseguono azioni che possono comportare l'inserimento di dati sensibili nella registrazione.

1. Avviare SimpleWPFApp usando il collegamento sul desktop.

     Anche in questo caso, si noti che il controllo CheckBox è disabilitato.

1. In SimpleWPFApp scegliere **Avvia**.

     L'indicatore di stato dovrebbe essere completato al 100% in pochi secondi.

1. Selezionare il controllo CheckBox, ora abilitato.

1. Chiudere l'applicazione SimpleWPFApp.

1. Nella finestra di dialogo **UIMap - Generatore di test codificati dell'interfaccia utente** scegliere **Genera codice**.

1. Nella casella **Nome metodo** digitare **SimpleAppTest** e scegliere **Aggiungi e genera**. Entro pochi secondi il test codificato dell'interfaccia utente verrà visualizzato e aggiunto alla soluzione.

1. Chiudere **UIMap - Generatore di test codificati dell'interfaccia utente**.

     Il file *CodedUITest1.cs* verrà visualizzato nell'editor del codice.

1. Salvare il progetto.

### <a name="run-the-test"></a>Eseguire il test

1. Nel menu **Test** scegliere **Finestre** e quindi **Esplora test**.

2. Scegliere **Compila soluzione** dal menu **Compila**.

3. Nel file *CodedUITest1.cs* individuare il metodo **CodedUITestMethod**, fare clic con il pulsante destro del mouse e scegliere **Esegui test** oppure eseguire i test da **Esplora test**.

   Durante l'esecuzione del test codificato dell'interfaccia utente, SimpleWPFApp rimane visibile. Vengono eseguiti i passaggi effettuati nella procedura precedente. Tuttavia, quando nel test è effettuato il tentativo di selezionare la casella di controllo relativa al controllo CheckBox, nella finestra **Risultati test** viene indicato che il test non è stato completato. Ciò è dovuto al fatto che durante l'esecuzione del test è effettuato il tentativo di selezionare la casella di controllo, senza considerare che il controllo CheckBox rimane disabilitato finché l'indicatore di stato non sarà completato al 100%. È possibile correggere questo e problemi analoghi usando i diversi metodi `UITestControl.WaitForControlXXX()` disponibili per il test codificato dell'interfaccia utente. Nella procedura seguente verrà descritto l'uso del metodo `WaitForControlEnabled()` per correggere il problema che ha impedito il corretto funzionamento di questo test. Per altre informazioni, vedere [Impostazione dei test codificati dell'interfaccia utente per l'attesa di eventi specifici durante la riproduzione](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Modificare ed eseguire di nuovo il test codificato dell'interfaccia utente

1. Nella finestra **Esplora test** selezionare il test non riuscito e quindi nella sezione **StackTrace** scegliere il primo collegamento a **UIMap.SimpleAppTest()**.

2. Il file *UIMap.Designer.cs* verrà aperto con il punto di errore evidenziato nel codice:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Per correggere questo problema, è possibile fare in modo che il test codificato dell'interfaccia utente attenda che il controllo CheckBox sia abilitato prima di continuare fino a questa riga usando il metodo `WaitForControlEnabled()`.

    > [!WARNING]
    > Il file *UIMap.Designer.cs* non deve essere modificato. Qualsiasi modifica del codice apportata verrà sovrascritta ogni volta che si genera codice usando **UIMap - Generatore di test codificati dell'interfaccia utente**. Se è necessario modificare un metodo registrato, copiarlo nel file *UIMap.cs* e rinominarlo. Il file *UIMap.cs* può essere usato per eseguire l'override dei metodi e delle proprietà contenuti nel file *UIMapDesigner.cs*. È necessario rimuovere il riferimento al metodo originale nel file *Coded UITest.cs* e sostituirlo con il nome del metodo rinominato.

4. In **Esplora soluzioni** individuare *UIMap.uitest* nel progetto di test codificato dell'interfaccia utente.

5. Aprire il menu di scelta rapida per *UIMap.uitest* e scegliere **Apri**.

     Il test codificato dell'interfaccia utente viene visualizzato nell'Editor test codificati dell'interfaccia utente. È quindi possibile visualizzare e modificare il test codificato dell'interfaccia utente.

6. Nel riquadro **Azioni dell'interfaccia utente** selezionare il metodo di test (SimpleAppTest) che si desidera spostare nel file *UIMap.cs* o *UIMap.vb*. Lo spostamento del metodo in un altro file consente di aggiungere codice personalizzato che non verrà sovrascritto in fase di ricompilazione del codice di test.

7. Scegliere il pulsante **Sposta codice** sulla barra degli strumenti dell'**Editor di test codificati dell'interfaccia utente**.

8. Verrà visualizzata una finestra di dialogo di Microsoft Visual Studio Si tratta di un avviso indicante che il metodo verrà spostato dal file *UIMap.uitest* al file *UIMap.cs* e che non sarà più possibile modificare il metodo usando l'Editor test codificati dell'interfaccia utente. Scegliere **Sì**.

     Il metodo di test verrà rimosso dal file *UIMap.uitest* e non verrà più visualizzato nel riquadro delle azioni dell'interfaccia utente. Per modificare il file di test spostato, aprire il file *UIMap.cs* da **Esplora soluzioni**.

9. Nella barra degli strumenti di Visual Studio scegliere **Salva**.

     Gli aggiornamenti al metodo di test vengono salvati nel file *UIMap.Designer*.

    > [!WARNING]
    > Una volta che è stato spostato il metodo, non è più possibile modificarlo tramite l'Editor test codificati dell'interfaccia utente. È necessario aggiungere il codice personalizzato e gestirlo usando l'editor del codice.

10. Rinominare il metodo `SimpleAppTest()` in `ModifiedSimpleAppTest()`.

11. Aggiungere al file l'istruzione using seguente:

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. Aggiungere il metodo `WaitForControlEnabled()` seguente prima della riga di codice che causa il problema identificato precedentemente:

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. Nel file *CodedUITest1.cs* individuare il metodo **CodedUITestMethod** e impostare come commento o rinominare il riferimento al metodo SimpleAppTest() originale e quindi sostituirlo con il nuovo metodo ModifiedSimpleAppTest():

    ```csharp
    [TestMethod]
            public void CodedUITestMethod1()
            {
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463
                //this.UIMap.SimpleAppTest();
                this.UIMap.ModifiedSimpleAppTest();
            }
    ```

14. Scegliere **Compila soluzione** dal menu **Compila**.

15. Fare clic con il pulsante destro del mouse sul metodo **CodedUITestMethod** e selezionare **Esegui test**.

16. Questa volta tutti i passaggi del test codificato dell'interfaccia utente vengono completati e nella finestra **Esplora test** è visualizzato **Superato**.

## <a name="refactor-a-control-in-simplewpfapp"></a>Effettuare il refactoring di un controllo in SimpleWPFApp

1. Nel file *MainWindow.xaml* selezionare il pulsante nella finestra di progettazione.

2. Nella parte superiore della finestra **Proprietà** modificare il valore della proprietà **Name** da **button1** a **buttonA**.

3. Scegliere **Compila soluzione** dal menu **Compila**.

4. In **Esplora test** eseguire **CodedUITestMethod1**.

     Il test non funziona perché il test codificato dell'interfaccia utente non è in grado di individuare il pulsante mappato in origine come button1 in UIMap. Il refactoring può influire in questo modo sui test codificati dell'interfaccia utente.

5. Nella sezione **StackTrace** di **Esplora test** scegliere il primo collegamento accanto a **UIMpa.ModifiedSimpleAppTest()**.

     Verrà aperto il file *UIMap.cs*. Il punto di errore è evidenziato nel codice:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Si noti che nella riga di codice precedente di questa procedura viene usato `UiStartButton`, che corrisponde al nome di UIMap prima del refactoring.

     Per correggere il problema, è possibile aggiungere il controllo di cui è stato effettuato il refactoring a UIMap tramite il **Generatore di test codificati dell'interfaccia utente**. È possibile aggiornare il codice del test in modo che venga usato il codice, come illustrato nella procedura seguente.

## <a name="map-refactored-control-rerun-the-test"></a>Mapping del controllo di cui è stato effettuato il refactoring, eseguire di nuovo il test

1. Nel file *CodedUITest1.cs* fare clic con il pulsante destro del mouse sul metodo **CodedUITestMethod1()**, scegliere **Genera codice per test codificato dell'interfaccia utente** e quindi fare clic su **Usa il generatore di test codificati dell'interfaccia utente**.

     Verrà visualizzato **UIMap - Generatore di test codificati dell'interfaccia utente**.

2. Usando il collegamento del desktop creato in precedenza, eseguire l'applicazione SimpleWPFApp creata precedentemente.

3. In **UIMap - Generatore di test codificati dell'interfaccia utente** trascinare il selettore di precisione sul pulsante **Start** in SimpleWPFApp.

     Il pulsante **Start** è racchiuso in una casella blu. **Generatore di test codificati dell'interfaccia utente** richiede alcuni secondi per elaborare i dati relativi al controllo selezionato e visualizza le proprietà dei controlli. Si noti che il valore di **AutomationUId** è **buttonA**.

4. Nelle proprietà del controllo scegliere la freccia nell'angolo superiore sinistro per espandere la mappa del controllo dell'interfaccia utente. Si noti che **UIStartButton1** è selezionato.

5. Sulla barra degli strumenti scegliere **Aggiungi controllo alla mappa del controllo dell'interfaccia utente**.

     Lo stato nella parte inferiore della finestra consente di verificare l'azione visualizzando il messaggio **Il controllo selezionato è stato aggiunto alla mappa del controllo dell'interfaccia utente**.

6. Nella finestra di dialogo **UIMap - Generatore di test codificati dell'interfaccia utente** scegliere **Genera codice**.

     Viene visualizzata la finestra di dialogo **Generatore di test codificati dell'interfaccia utente - Genera codice** con una nota in cui è indicato che non è richiesto alcun nuovo metodo e che il codice sarà generato solo per le modifiche alla mappa del controllo dell'interfaccia utente.

7. Scegliere **Genera**.

8. Chiudere SimpleWPFApp.

9. Chiudere **UIMap - Generatore di test codificati dell'interfaccia utente**.

10. In **Esplora soluzioni** aprire il file *UIMap.Designer.cs*.

11. Nel file *UIMap.Designer.cs* individuare la proprietà **UIStartButton1**. Si noti che `SearchProperties` è impostato su `"buttonA"`:

    ```csharp
    public WpfButton UIStartButton1
            {
                get
                {
                    if ((this.mUIStartButton1 == null))
                    {
                        this.mUIStartButton1 = new WpfButton(this);
                        #region Search Criteria
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");
                        #endregion
                    }
                    return this.mUIStartButton1;
                }
            }
    ```

     A questo punto è possibile modificare il test codificato dell'interfaccia utente in modo che venga usato il controllo appena mappato. Come evidenziato nella procedura precedente, se si intende eseguire l'override di metodi o proprietà nel test codificato dell'interfaccia utente, è necessario eseguire questa operazione nel file *UIMap.cs*.

12. Nel file *UIMap.cs* aggiungere un costruttore e specificare la proprietà `SearchProperties` della proprietà `UIStartButton` per usare la proprietà `AutomationID` con un valore `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. Scegliere **Compila soluzione** dal menu **Compila**.

14. In **Esplora test** eseguire **CodedUITestMethod1**.

     Questa volta tutti i passaggi del test codificato dell'interfaccia utente vengono completati. Nella finestra **Risultati test** viene visualizzato **Superato**.

## <a name="videos"></a>Video

![collegamento a video](../data-tools/media/playvideo.gif) [Get started with coded UI tests](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)(Introduzione ai test codificati dell'interfaccia utente)

## <a name="faq"></a>Domande frequenti

[Domande frequenti sui test codificati dell'interfaccia utente](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Vedere anche

- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Modificare test codificati dell'interfaccia utente usando l'editor di test codificati dell'interfaccia utente](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
