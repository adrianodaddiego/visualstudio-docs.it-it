---
title: Creazione di un Windows Form di controllo della casella degli strumenti | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3887a2d54f2744504f587b848bc1395090c3904c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345407"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Creare un controllo della casella degli strumenti di Windows Form

Il modello di elemento di controllo della casella degli strumenti di Windows Form incluso in Visual Studio Extensibility Tools (Visual Studio SDK), consente di creare un **casella degli strumenti** controllo che viene aggiunta automaticamente quando è installata l'estensione. Questa procedura dettagliata illustra come usare il modello per creare un controllo di un contatore semplice che è possibile distribuire ad altri utenti.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Creare il controllo della casella degli strumenti

Il modello di controllo della casella degli strumenti di Windows Form crea un controllo utente non definito e fornisce tutte le funzionalità necessarie per aggiungere il controllo per il **casella degli strumenti**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Creare un'estensione con un controllo della casella degli strumenti di Windows Form

1. Creare un progetto VSIX denominato `MyWinFormsControl`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** finestra di dialogo, eseguendo una ricerca per "vsix".

2. Quando si apre il progetto, aggiungere un **controllo della casella degli strumenti di Windows Form** modello di elemento denominato `Counter`. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual c#**  > **Extensibility** e selezionare **controllo della casella degli strumenti di Windows Form**

3. Ciò consente di aggiungere un controllo utente, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> per posizionare il controllo nel **della casella degli strumenti**e un **Microsoft.VisualStudio.ToolboxControl** voce di risorsa nel manifesto VSIX per la distribuzione.

### <a name="build-a-user-interface-for-the-control"></a>Compilare un'interfaccia utente per il controllo

Il `Counter` controllo richiede due controlli figlio: una <xref:System.Windows.Forms.Label> per visualizzare il conteggio corrente e un <xref:System.Windows.Forms.Button> per reimpostare il conteggio su 0. Altri controlli figlio non sono necessari perché i chiamanti incrementeranno il contatore a livello di codice.

#### <a name="to-build-the-user-interface"></a>Per creare l'interfaccia utente

1. Nelle **Esplora soluzioni**, fare doppio clic su *Counter.cs* per aprirlo nella finestra di progettazione.

2. Rimuovere il **fare clic qui.** pulsante che è incluso per impostazione predefinita quando si aggiunge il modello di elemento di controllo della casella degli strumenti di Windows Form.

3. Dal **casella degli strumenti**, trascinare un `Label` controllo e quindi un `Button` controllo sotto di esso nell'area di progettazione.

4. Ridimensionare il controllo utente generale a 150, 50 pixel e ridimensionare il pulsante di controllo su 50, 20 pixel.

5. Nel **proprietà** finestra, impostare i valori seguenti per i controlli nell'area di progettazione.

    |Control|Proprietà|Value|
    |-------------|--------------|-----------|
    |`Label1`|**per**|""|
    |`Button1`|**Name**|btnReset|
    |`Button1`|**per**|Reimposta|

### <a name="code-the-user-control"></a>Codice del controllo utente

Il `Counter` controllo espone un metodo per incrementare il contatore, un evento da generare ogni volta che il contatore viene incrementato, un **reimpostare** pulsante e tre le proprietà per archiviare il conteggio corrente, il testo visualizzato e se visualizzare o nascondere il **reimpostare** pulsante. L'attributo `ProvideToolboxControl` determina la posizione nella **casella degli strumenti** in cui verrà visualizzato il controllo `Counter` .

#### <a name="to-code-the-user-control"></a>Per codificare il controllo utente

1. Fare doppio clic sul form per aprire il gestore di eventi di carico nella finestra del codice.

2. Sopra il metodo del gestore eventi, creare un numero intero per archiviare il valore del contatore e una stringa per archiviare il testo visualizzato come illustrato nell'esempio seguente nella classe del controllo.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Creare le seguenti dichiarazioni di proprietà pubblica.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    I chiamanti possono accedere a queste proprietà per ottenere e impostare il testo visualizzato del contatore e per mostrare o nascondere il **reimpostare** pulsante. I chiamanti possono ottenere il valore corrente di sola lettura `Value` proprietà, ma non è possibile impostare il valore direttamente.

4. Inserire il codice seguente nel `Load` evento per il controllo.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Impostando il **etichetta** testo nel <xref:System.Windows.Forms.UserControl.Load> evento consente di caricare prima i relativi valori vengono applicati le proprietà di destinazione. Impostando il **Label** testo nel costruttore genera un oggetto vuoto **etichetta**.

5. Creare il metodo pubblico seguente per incrementare il contatore.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Aggiungere una dichiarazione per il `Incremented` eventi alla classe del controllo.

    ```csharp
    public event EventHandler Incremented;
    ```

    I chiamanti possono aggiungere gestori all'evento per rispondere alle modifiche del valore del contatore.

7. Tornare alla visualizzazione progettazione e fare doppio clic sui **reimpostare** pulsante per generare il `btnReset_Click` gestore eventi e quindi compilare in come illustrato nell'esempio seguente.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Immediatamente sopra la definizione di classe, nella dichiarazione dell'attributo `ProvideToolboxControl` , modificare il valore del primo parametro da `"MyWinFormsControl.Counter"` a `"General"`. In questo modo si imposta il nome del gruppo di elementi che ospiterà il controllo nella **casella degli strumenti**.

    L'esempio seguente mostra l'attributo `ProvideToolboxControl` e la definizione di classe modificata.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Testare il controllo

 Per testare una **casella degli strumenti** controllare, testarlo prima di tutto nell'ambiente di sviluppo e quindi eseguirne il test in un'applicazione compilata.

#### <a name="to-test-the-control"></a>Per testare il controllo

1. Premere **F5** al **Avvia debug**.

    Questo comando compila il progetto e apre una seconda istanza sperimentale di Visual Studio con il controllo installato.

2. Nell'istanza sperimentale di Visual Studio, creare un **Windows Forms Application** progetto.

3. Nelle **Esplora soluzioni**, fare doppio clic su *Form1.cs* per aprirlo nella finestra di progettazione se non è già aperto.

4. Nel **casella degli strumenti**, il `Counter` controllo deve essere visualizzato nei **generale** sezione.

5. Trascinare un `Counter` controllo al form e selezionarlo. Il `Value`, `Message`, e `ShowReset` proprietà verranno visualizzate nel **delle proprietà** finestra, insieme alle proprietà che vengono ereditate da <xref:System.Windows.Forms.UserControl>.

6. Impostare la proprietà `Message` su `Count:`.

7. Trascinare un <xref:System.Windows.Forms.Button> controllo al form e quindi impostare le proprietà di nome e il testo del pulsante su `Test`.

8. Fare doppio clic sul pulsante per aprire *Form1.cs* nella visualizzazione del codice e creare un gestore eventi click.

9. Nel gestore di clic, chiamare `counter1.Increment()`.

10. Nella funzione del costruttore, dopo la chiamata a `InitializeComponent`, digitare `counter1``.``Incremented +=` e quindi premere **scheda** due volte.

    Visual Studio genera un gestore a livello di form per il `counter1.Incremented` evento.

11. Evidenziare la `Throw` istruzione nel gestore eventi, digitare `mbox`, quindi premere **scheda** due volte per generare una finestra di messaggio dal frammento di codice mbox.

12. Nella riga successiva, aggiungere quanto segue `if` / `else` blocco per impostare la visibilità del **reimpostazione** pulsante.

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Premere **F5**.

    Verrà aperto il modulo. Il `Counter` controllo Visualizza il testo seguente.

    **Conteggio: 0**

14. Fare clic su **Test**.

    L'incremento del contatore e Visual Studio visualizza una finestra di messaggio.

15. Chiudere la finestra di messaggio.

    Il **reimpostare** che scompare.

16. Fare clic su **Test** fino a quando il contatore raggiunge **5** il messaggio di chiusura caselle ogni volta.

    Il **reimpostare** pulsante viene visualizzata di nuovo.

17. Fare clic su **Reimposta**.

    Reimposta il contatore **0**.

## <a name="next-steps"></a>Passaggi successivi

Quando si compila un **casella degli strumenti** (controllo), Visual Studio crea un file denominato *ProjectName.vsix* nella cartella \bin\debug\ del progetto. È possibile distribuire il controllo caricando il *VSIX* file in una rete o a un sito Web. Quando un utente apre la *VSIX* file, il controllo viene installato e aggiunto a Visual Studio **della casella degli strumenti** nel computer dell'utente. In alternativa, è possibile caricare il *VSIX* del file ai [Visual Studio Marketplace](https://marketplace.visualstudio.com/) in modo che gli utenti potranno trovarlo cercando il **strumenti**  >   **Estensioni e aggiornamenti** finestra di dialogo.

## <a name="see-also"></a>Vedere anche

- [Estendere altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Creare un controllo della casella degli strumenti WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Estendere altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Nozioni fondamentali sullo sviluppo di controlli Windows Form](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
