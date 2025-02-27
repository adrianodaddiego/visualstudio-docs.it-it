---
title: Testare app di Windows Store 8.1 e UWP con test codificati dell'interfaccia utente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: 26
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d772a2c3f8654d458ea1ba1b9d0661b290361b54
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446007"
---
# <a name="test-windows-uwp-and-81-store-apps-with-coded-ui-tests"></a>Testare app di Windows Store 8.1 e UWP con test codificati dell'interfaccia utente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usare questa procedura guidata per creare test dell'interfaccia utente per app UWP e app di Windows Store 8.1 basate su XAML.
  
## <a name="create-a-simple-windows-store-app"></a>Creare una semplice app di Windows Store  
  
1. Per eseguire test codificati dell'interfaccia utente per un'app di Windows Store basata su XAML, è necessario [impostare una proprietà di automazione univoca che identifichi ogni controllo](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md).  
  
     Scegliere **Opzioni** dal menu **Strumenti** , quindi **Editor di testo**, **XAML**e infine **Varie**.  
  
     Selezionare la casella di controllo per denominare automaticamente gli elementi non attivi al momento della creazione.  
  
     ![Altre opzioni XAML](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")  
  
2. Creare un nuovo progetto per un'app di Windows Store vuota basata su XAML, usando un modello di Visual C# o Visual Basic.  
  
     ![Creare un'app di Windows Store vuota &#40;XAML&#41;](../test/media/cuit-windowsstoreapp-newproject-blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")  
  
3. In Esplora soluzioni aprire il file MainPage.xaml. Dalla casella degli strumenti trascinare un controllo Button e un controllo Textbox nell'area di progettazione.  
  
     ![Progettare l'app di Windows Store](../test/media/cuit-windowsstoreapp-design.png "CUIT_WindowsStoreApp_Design")  
  
4. Fare doppio clic sul controllo Button e aggiungere il codice seguente:  
  
    ```csharp  
    private void button_Click_1(object sender, RoutedEventArgs e)  
    {  
        this.textBox.Text = this.button.Name;  
    }  
  
    ```  
  
    ```vb  
    Public NotInheritable Class MainPage  
        Inherits Page  
  
        Private Sub button_Click(sender As Object, e As RoutedEventArgs) Handles Button.Click  
            Me.textBox.Text = Me.button.Name  
        End Sub  
    End Class  
    ```  
  
5. Premere F5 per eseguire l'app di Windows Store.  
  
## <a name="create-and-run-a-coded-ui-test-for-the-windows-store-app"></a>Creare ed eseguire un test codificato dell'interfaccia utente per l'app di Windows Store  

[Come si creano i test codificati dell'interfaccia utente per le app UWP (Universal Windows Platform)?](#uwpapps)
  
1. Creare un nuovo progetto di test codificato dell'interfaccia utente per l'app di Windows Store.  
  
    ![Nuovo progetto di test codificato dell'interfaccia utente &#40;app di Windows Store&#41;](../test/media/cuit-windowsstore-newproject.png "CUIT_WindowsStore_NewProject")  
  
2. Scegliere di modificare la mappa dell'interfaccia utente usando lo strumento selettore di precisione.  
  
    ![Scegliere l'opzione per modificare il mapping dell'interfaccia utente o aggiungere asserzioni](../test/media/cuit-windowsstoreapp-createproject-gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")  
  
3. Usare lo strumento selettore di precisione nel Generatore di test codificati dell'interfaccia utente per selezionare il riquadro dell'app, fare clic con il pulsante destro del mouse su **AutomationId** e scegliere **Copia valore negli Appunti**. Il valore presente negli Appunti verrà usato più avanti per scrivere l'azione per l'avvio dell'app per i test.  
  
    ![Copiare AutomationId negli Appunti](../test/media/cuit-windows-store-tileautomationid.png "CUIT_Windows_Store_TileAutomationID")  
  
4. Nell'app di Windows Store in esecuzione usare lo strumento selettore di precisione per selezionare il controllo Button e il controllo Textbox. Dopo avere aggiunto ogni controllo, scegliere il pulsante **Aggiungi controllo alla mappa del controllo dell'interfaccia utente** sulla barra degli strumenti Generatore di test codificati dell'interfaccia utente.  
  
    ![Aggiungere un controllo al mapping dell'interfaccia utente](../test/media/cuit-windowsstoreapp-uimap.png "CUIT_WindowsStoreApp_UIMap")  
  
5. Scegliere il pulsante **Genera codice** sulla barra degli strumenti Generatore di test codificati dell'interfaccia utente, quindi scegliere **Genera** per creare il codice per le modifiche alla mappa del controllo dell'interfaccia utente.  
  
    ![Generare il codice per il mapping dell'interfaccia utente](../test/media/cuit-windowsstoreapp-generate.png "CUIT_WindowsStoreApp_Generate")  
  
6. Scegliere il pulsante per impostare un valore nella casella di testo.  
  
    ![Fare clic sul controllo Button per impostare il valore della casella di testo](../test/media/cuit-windowsstoreapp-clickbutton.png "CUIT_WindowsStoreApp_ClickButton")  
  
7. Usare lo strumento selettore di precisione per selezionare il controllo TextBox e quindi selezionare la proprietà **Text** .  
  
    ![Selezionare la proprietà Text](../test/media/cuit-windowsstoreapp-selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")  
  
8. Aggiungere un'asserzione. Verrà usata nel test per verificare che il valore sia corretto.  
  
    ![Scegliere la casella di testo con il mirino e aggiungere un'asserzione](../test/media/cuit-windowsstoreapp-textbox-addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")  
  
9. Aggiungere e generare il codice per l'asserzione.  
  
     ![Generare il codice per l'asserzione della casella di testo](../test/media/cuit-windowsstoreapp-textbox-generate-assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")  
  
10. **Visual C#**  
  
     In Esplora soluzioni aprire il file UIMap.Designer.cs per visualizzare il codice aggiunto per il metodo Assert e i controlli.  
  
     **Visual Basic**  
  
     Aprire il file CodedUITest1.vb in Esplora soluzioni, quindi nel codice del metodo CodedUITestMethod1() fare clic con il pulsante destro del mouse sulla chiamata al metodo di asserzione `Me.UIMap.AssertMethod1()` aggiunto automaticamente e scegliere **Vai a definizione**. Verrà aperto il file UIMap.Designer.vb nell'editor del codice, in cui è visibile il codice aggiunto per il metodo di asserzione e i controlli.  
  
    > [!WARNING]
    > Non modificare direttamente il file UIMap.designer.cs o UIMap.Designer.vb perché, così facendo, le modifiche apportate al file verrebbero sovrascritte ogni volta che viene generato il test.  
  
     **Metodo Assert**  
  
    ```csharp  
    public void AssertMethod1()  
    {  
        #region Variable Declarations  
        XamlEdit uITextBoxEdit = this.UIApp1Window.UITextBoxEdit;  
        #endregion  
  
        // Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(this.AssertMethod3ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);  
    }  
    ```  
  
    ```vb  
    Public Sub AssertMethod1()  
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit  
  
        'Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)  
    End Sub  
    ```  
  
     **Controlli**  
  
    ```csharp  
    #region Properties  
    public XamlButton UIButtonButton  
    {  
        get  
        {  
            if ((this.mUIButtonButton == null))  
            {  
                this.mUIButtonButton = new XamlButton(this);  
                #region Search Criteria  
                this.mUIButtonButton.SearchProperties[XamlButton.PropertyNames.AutomationId] = "button";  
                this.mUIButtonButton.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUIButtonButton;  
        }  
    }  
  
    public XamlEdit UITextBoxEdit  
    {  
        get  
        {  
            if ((this.mUITextBoxEdit == null))  
            {  
                this.mUITextBoxEdit = new XamlEdit(this);  
                #region Search Criteria  
                this.mUITextBoxEdit.SearchProperties[XamlEdit.PropertyNames.AutomationId] = "textBox";  
                this.mUITextBoxEdit.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUITextBoxEdit;  
        }  
    }  
    #endregion  
  
    #region Fields  
    private XamlButton mUIButtonButton;  
  
    private XamlEdit mUITextBoxEdit;  
    #endregion  
    ```  
  
    ```vb  
    #Region "Properties"  
    Public ReadOnly Property UIButtonButton() As XamlButton  
        Get  
            If (Me.mUIButtonButton Is Nothing) Then  
                Me.mUIButtonButton = New XamlButton(Me)  
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"  
                Me.mUIButtonButton.WindowTitles.Add("App2")  
            End If  
            Return Me.mUIButtonButton  
        End Get  
    End Property  
  
    Public ReadOnly Property UITextBoxEdit() As XamlEdit  
        Get  
            If (Me.mUITextBoxEdit Is Nothing) Then  
                Me.mUITextBoxEdit = New XamlEdit(Me)  
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"  
                Me.mUITextBoxEdit.WindowTitles.Add("App2")  
            End If  
            Return Me.mUITextBoxEdit  
        End Get  
    End Property  
    #End Region  
  
    #Region "Fields"  
    Private mUIButtonButton As XamlButton  
  
    Private mUITextBoxEdit As XamlEdit  
    #End Region  
    ```  
  
11. In Esplora soluzioni aprire il file CodedUITest1.cs o CodedUITest1.vb. A questo punto è possibile aggiungere il codice al metodo CodedUTTestMethod1 per le azioni necessarie per l'esecuzione del test usando i controlli aggiunti a UIMap:  
  
    1. Avviare l'app di Windows Store usando la proprietà automationID copiata in precedenza negli Appunti:  
  
       ```csharp  
       XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
       ```  
  
       ```vb  
       XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
       ```  
  
    2. Aggiungere un gesto tocco per il controllo Button:  
  
       ```csharp  
       Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);  
       ```  
  
       ```vb  
       Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)  
       ```  
  
    3. Verificare che la chiamata al metodo Assert generato automaticamente avvenga dopo l'avvio dell'app e del gesto tocco sul pulsante:  
  
       ```csharp  
       this.UIMap.AssertMethod1();  
       ```  
  
       ```vb  
       Me.UIMap.AssertMethod1()  
       ```  
  
       Dopo avere aggiunto il codice, il metodo di test CodedUITestMethod1 dovrebbe avere un aspetto simile al seguente:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
  
        // Launch the app.  
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
  
        // Tap the button.  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
  
        this.UIMap.AssertMethod1();  
    }  
    ```  
  
    ```vb  
    <CodedUITest(CodedUITestType.WindowsStore)>  
    Public Class CodedUITest1  
  
        <TestMethod()>  
        Public Sub CodedUITestMethod1()  
            '              
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
            '  
  
            ' Launch the app.  
            XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
  
            '// Tap the button.  
            Gesture.Tap(Me.UIMap.UIApp2Window.UIButtonButton)  
  
            Me.UIMap.AssertMethod1()  
        End Sub  
    ```  
  
12. Compilare ed eseguire il test con Esplora test.  
  
     ![Eseguire il test codificato dell'interfaccia utente da Esplora test](../test/media/cuit-windowsstoreapp-runtest.png "CUIT_WindowsStoreApp_RunTest")  
  
     L'app di Windows Store viene avviata, l'azione per il tocco del pulsante è completata e la proprietà Text della casella di testo è popolata e convalidata tramite il metodo Assert.  
  
     ![Esecuzione del test codificato dell'interfaccia utente](../test/media/cuit-windowsstoreapp-running.png "CUIT_WindowsStoreApp_Running")  
  
     Al termine dell'operazione, Esplora test indica che il test è stato superato.  
  
     ![Il test superato viene visualizzato in Esplora test](../test/media/cuit-windowsstorapp-passedtest.png "CUIT_WindowsStorApp_PassedTest")  
  
## <a name="q--a"></a>Domande e risposte  
  
- **D: Il motivo per cui non è presente un'opzione per registrare il test codificato dell'interfaccia utente nella finestra di dialogo Genera codice per un Test codificato dell'interfaccia utente?**  
  
     **R**: L'opzione per la registrazione non è supportata per le app di Windows Store.  
  
- **D: È possibile creare un test codificato dell'interfaccia utente per le app di Windows Store basate su WinJS?**  
  
     **R**: No, non sono supportate solo le app XAML di base.  
  
- **D: È possibile creare test codificati dell'interfaccia utente per le app di Windows Store in un sistema che non è in esecuzione Windows 8.1 o Windows 10?**  
  
     **R**: No, i modelli di progetto di Test codificato dell'interfaccia utente sono disponibili solo in Windows 8.1 e Windows 10. Per creare l'automazione per le app UWP (Universal Windows Platform), sarà necessario Windows 10.  

<a name="uwpapps"></a>
- **D: Come si crea codificati dell'interfaccia utente per le app Universal Windows Platform (UWP)?**  
  
   **R**: A seconda della piattaforma dove si sta testando l'app UWP, creare progetto di test codificato dell'interfaccia utente in uno dei modi seguenti:  
  
  - Un'app della piattaforma UWP in esecuzione in un computer locale verrà eseguita come app di Windows Store. Per testarla, è necessario usare il modello **Progetto di test codificato dell'interfaccia utente (Windows)** . Per trovare questo modello quando si crea un nuovo progetto, andare al nodo **Universal**, **Windows** oppure in alternativa andare al nodo **Windows**, **Windows 8**, **Windows** .  
  
  - Un'app della piattaforma UWP in esecuzione su un dispositivo mobile ed emulatore verrà eseguita come app per Windows Phone. Per testarla, è necessario usare il modello **Progetto di test codificato dell'interfaccia utente (Windows Phone)** . Per trovare questo modello quando si crea un nuovo progetto, andare al nodo **Universal**, **Windows** oppure in alternativa andare al nodo **Windows**, **Windows 8**, **Windows Phone** .  
  
    Dopo aver creato il progetto, la creazione di un test è uguale a quella descritta in precedenza.  
  
- **D: Perché non riesco a modificare il codice nel file UIMap Designer?**  
  
   **R**: Qualsiasi modifica del codice apportata nel file UIMapDesigner.cs verrà sovrascritta ogni volta che si genera codice usando UIMap - Generatore di test codificati dell'interfaccia utente. Se è necessario modificare un metodo registrato, copiarlo nel file UIMap.cs e rinominarlo. Il file UIMap.cs può essere usato per eseguire l'override dei metodi e delle proprietà contenuti nel file UIMapDesigner.cs. È necessario rimuovere il riferimento al metodo originale nel file Coded UITest.cs e sostituirlo con il nome del metodo rinominato.  
  
## <a name="see-also"></a>Vedere anche  
 [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)   
 [Impostare una proprietà di automazione univoca dei controlli Windows Store per il test](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
