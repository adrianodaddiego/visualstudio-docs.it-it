---
title: 'Passaggio 5: Aggiungere controlli al modulo'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f1662f484d8738c381f704732389537b0ac3ad5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431483"
---
# <a name="step-5-add-controls-to-your-form"></a>Passaggio 5: Aggiungere controlli al modulo
In questo passaggio si aggiungono controlli, ad esempio un controllo <xref:System.Windows.Forms.PictureBox> e un controllo <xref:System.Windows.Forms.CheckBox>, al form. Si aggiungono quindi controlli <xref:System.Windows.Forms.Button> al modulo.

 ![Collegamento a video](../data-tools/media/playvideo.gif)Per una versione video di questo argomento, vedere [Esercitazione 1: Creare un visualizzatore di immagini in Visual Basic - Video 2](http://go.microsoft.com/fwlink/?LinkId=205211) o [Esercitazione 1: Creare un visualizzatore immagini in C# - Video 2](http://go.microsoft.com/fwlink/?LinkId=205200). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.

## <a name="to-add-controls-to-your-form"></a>Per aggiungere controlli al form

1. Passare alla scheda **Casella degli strumenti**, a sinistra dell'IDE di Visual Studio, ed espandere il gruppo **Controlli comuni**. Verranno visualizzati i controlli più comuni dei form.

2. Scegliere il controllo **TableLayoutPanel** nel modulo. Per verificare che TableLayoutPanel sia selezionato, assicurarsi che il nome sia visualizzato nella casella di riepilogo a discesa nella parte superiore della finestra **Proprietà**. È inoltre possibile scegliere i controlli del form nella casella di riepilogo a discesa nella parte superiore della finestra **Proprietà**. Spesso, questa modalità di scelta del controllo può essere più semplice della scelta di un controllo minuscolo con il mouse.

3. Fare doppio clic sull'elemento **PictureBox** per aggiungere un controllo PictureBox al form. Poiché TableLayoutPanel è ancorato in modo da riempire il form, l'IDE aggiunge il controllo PictureBox alla prima cella vuota (angolo in alto a sinistra).

4. Scegliere il nuovo controllo **PictureBox** per selezionarlo e quindi scegliere il triangolo nero sul nuovo controllo PictureBox per visualizzare il relativo elenco attività, come illustrato nell'immagine seguente.

     ![Attività di PictureBox](../ide/media/express_pictureboxtasks.png)
Attività di **PictureBox**

    > [!NOTE]
    > Se accidentalmente si aggiunge il tipo non corretto di controllo a TableLayoutPanel, è possibile eliminarlo. Fare clic con il pulsante destro del mouse sul controllo, quindi scegliere **Elimina** dal relativo menu di scelta rapida. È inoltre possibile rimuovere controlli dal form utilizzando la barra dei menu. Sulla barra dei menu scegliere **Modifica** > **Annulla** o **Modifica** > **Elimina**.

5. Scegliere il collegamento **Ancora nel contenitore padre**. La proprietà **Dock** di PictureBox verrà automaticamente impostata su **Fill**. Per verificarlo, scegliere il controllo **PictureBox** per selezionarlo, passare alla finestra **Proprietà** e verificare che la proprietà **Dock** sia impostata su **Riempi**.

6. Estendere il controllo PictureBox su entrambe le colonne modificandone la proprietà **ColumnSpan**. Scegliere il controllo **PictureBox** e impostare la relativa proprietà **ColumnSpan** su **2**. Inoltre, quando PictureBox è vuoto, si desidera visualizzare un frame vuoto. Impostare la proprietà **BorderStyle** su **Fixed3D**.

    > [!NOTE]
    > Se non viene visualizzata una proprietà **ColumnSpan** per PictureBox, è probabile che tale controllo sia stato aggiunto al form anziché a TableLayoutPanel. Per risolvere questo problema, scegliere il controllo **PictureBox**, eliminarlo, scegliere **TableLayoutPanel** e quindi aggiungere un nuovo controllo PictureBox.

7. Scegliere **TableLayoutPanel** nel modulo e quindi aggiungere un controllo CheckBox al modulo. Fare doppio clic sull'elemento **CheckBox** nella **casella degli strumenti** per aggiungere un nuovo controllo CheckBox alla cella libera successiva della tabella. Poiché un controllo PictureBox occupa le prime due celle, in TableLayoutPanel viene aggiunto un controllo CheckBox alla cella inferiore sinistra. Scegliere la proprietà **Text** e digitare la parola **Stretch**, come illustrato nell'immagine.

     ![Controllo TextBox con la proprietà Stretch](../ide/media/express_pictureviewercheckbox.png)
Controllo **TextBox** con la proprietà **Stretch**

8. Scegliere **TableLayoutPanel** nel modulo e quindi passare al gruppo **Contenitori** nella **casella degli strumenti** (dove si è ottenuto il controllo TableLayoutPanel) e fare doppio clic sull'elemento **FlowLayoutPanel** per aggiungere un nuovo controllo all'ultima cella di PictureBox (in basso a destra). Ancorare quindi FlowLayoutPanel in TableLayoutPanel, scegliendo **Ancora nel contenitore padre** nell'elenco attività a forma di triangolo nero di FlowLayoutPanel o impostando la proprietà **Dock** di FlowLayoutPanel su **Fill**.

    > [!NOTE]
    > Un controllo <xref:System.Windows.Forms.FlowLayoutPanel> è un contenitore che dispone gli altri controlli nelle righe in modo corretto e ordinato. Quando si ridimensiona un controllo FlowLayoutPanel, tutti i controlli vengono disposti in una singola riga, se esiste spazio. In caso contrario, vengono disposti su più righe, uno sopra l'altro. Si utilizzerà un controllo FlowLayoutPanel per contenere quattro pulsanti. Se i pulsanti aggiunti vengono disposti uno sopra l'altro, assicurarsi che FlowLayoutPanel sia selezionato prima di aggiungerli. Anche se in precedenza è stato dichiarato che ogni cella può contenere un solo controllo, la cella inferiore destra di TableLayoutPanel dispone di quattro controlli pulsante. Questo si verifica perché è possibile inserire un controllo in una cella che contiene altri controlli. Questo tipo di controllo è denominato contenitore e FlowLayoutPanel è un contenitore.

## <a name="to-add-buttons"></a>Per aggiungere pulsanti

1. Scegliere il nuovo controllo FlowLayoutPanel aggiunto. Passare a **Controlli comuni** nella **casella degli strumenti** e fare doppio clic sull'elemento **Button** per aggiungere un pulsante denominato **button1** a FlowLayoutPanel. Ripetere l'operazione per aggiungere un altro pulsante. L'IDE determina che un pulsante chiamato **button1** esiste già e denomina il successivo **button2**.

2. In genere, si aggiungono gli altri pulsanti usando la **casella degli strumenti**. Questa volta, scegliere **button2** e quindi sulla barra dei menu scegliere **Modifica** > **Copia** oppure premere **CTRL**+**C**. Sulla barra dei menu scegliere **Modifica** > **Incolla** oppure premere **CTRL**+**V** per incollare una copia del pulsante. Ora incollarlo nuovamente. Nell''IDE sono stati aggiunti **button3** e **button4** a FlowLayoutPanel.

    > [!NOTE]
    > È possibile copiare e incollare qualsiasi controllo. L'IDE denomina e posiziona i nuovi controlli in modo logico. Se si incolla un controllo in un contenitore, l'IDE sceglie lo spazio logico successivo per la posizione.

3. Scegliere il primo pulsante e impostarne la proprietà **Text** su **Visualizza immagine**. Impostare quindi le proprietà **Text** dei tre pulsanti successivi su **Cancella immagine**, **Imposta colore di sfondo** e **Chiudi**.

4. Il passaggio successivo consiste nel ridimensionamento e nella disposizione dei pulsanti in modo da allinearli sul lato destro del pannello. Scegliere il controllo **FlowLayoutPanel** e osservarne la proprietà **FlowDirection**. Modificarla in modo che venga impostata su **RightToLeft**. I pulsanti vengono immediatamente allineati sul lato destro della cella e l'ordine viene invertito in modo che il pulsante **Visualizza immagine** si trovi sulla destra.

    > [!NOTE]
    > Se i pulsanti sono ancora nell'ordine errato, è possibile trascinarli nel controllo FlowLayoutPanel per ridisporli in qualsiasi ordine. È possibile scegliere un pulsante e trascinarlo a sinistra o a destra.

5. Scegliere il pulsante **Chiudi** per selezionarlo. Tenere premuto **CTRL** e scegliere gli altri tre pulsanti, in modo che siano tutti selezionati. Mentre tutti i pulsanti sono selezionati, andare alla finestra **Proprietà** e scorrere verso l'alto fino alla proprietà **AutoSize**. Questa proprietà consente di ridimensionare automaticamente il pulsante in modo che si adatti a tutto il testo. Impostarla su **true**. I pulsanti sono ora ridimensionati correttamente e si trovano nell'ordine corretto. Finché i quattro pulsanti sono selezionati, è possibile modificare contemporaneamente le quattro proprietà **AutoSize**. Nell'immagine riportata di seguito vengono illustrati i quattro pulsanti.

     ![Visualizzatore immagini con quattro pulsanti](../ide/media/express_autosize.png)
**Visualizzatore immagini** con quattro pulsanti

6. Ora eseguire nuovamente il programma per visualizzare il form con il nuovo layout. La scelta dei pulsanti e della casella di controllo non produce ancora nessun risultato, ma i controlli funzioneranno a breve.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 6: Assegnare un nome ai pulsanti](../ide/step-6-name-your-button-controls.md).

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).
