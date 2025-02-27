---
title: Aggiunta di controllo utente alla pagina iniziale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: c662374b8ed0abc7e1c178fb4ff07d5033de8a54
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352301"
---
# <a name="add-user-control-to-the-start-page"></a>Aggiungi controllo utente nella pagina iniziale

Questa procedura dettagliata viene illustrato come aggiungere un riferimento DLL a una pagina iniziale personalizzata. L'esempio aggiunge un controllo utente alla soluzione, si basa il controllo utente e quindi si fa riferimento all'assembly compilato dalla pagina iniziale *XAML* file. Una nuova scheda contiene il controllo utente, che funziona come un Web browser di base.

È possibile usare lo stesso processo per aggiungere tutti gli assembly che può essere chiamato da un *XAML* file.

## <a name="add-a-wpf-user-control-to-the-solution"></a>Aggiungere un controllo utente WPF alla soluzione

In primo luogo, aggiungere un controllo utente Windows Presentation Foundation (WPF) per la soluzione di pagina iniziale.

1. Crea una pagina iniziale con cui è stato creato [creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).

2. Nella **Esplora soluzioni**, fare doppio clic la soluzione, fare clic su **Add**, quindi fare clic su **nuovo progetto**.

3. Nel riquadro sinistro della finestra il **nuovo progetto** finestra di dialogo espandere uno il **Visual Basic** o **Visual c#** nodo e fare clic su **Windows**. Nel riquadro centrale, selezionare **libreria di controlli utente WPF**.

4. Denominare il controllo `WebUserControl` e quindi fare clic su **OK**.

## <a name="implement-the-user-control"></a>Implementare il controllo utente

Per implementare un controllo utente WPF, compilare l'interfaccia utente (UI) in XAML e quindi scrivono gli eventi di code-behind in c# o un altro linguaggio .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Per scrivere il XAML per il controllo utente

1. Aprire il file XAML per il controllo utente. Nel `<Grid>` elemento, aggiungere le seguenti definizioni di riga per il controllo.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Nel principale `<Grid>` elemento, aggiungere la seguente nuovo `<Grid>` elemento che contiene una casella di testo per digitare gli indirizzi Web e un pulsante per impostare il nuovo indirizzo.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Aggiungere il frame seguente al livello superiore `<Grid>` elemento subito dopo il `<Grid>` elemento che contiene il pulsante e casella di testo.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Nell'esempio seguente viene illustrato il XAML completato per il controllo utente.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Per scrivere gli eventi di code-behind per il controllo utente

1. Nella finestra di progettazione XAML fare doppio clic il **impostare indirizzo** pulsante è stato aggiunto al controllo.

    Il *UserControl1.cs* file viene aperto nell'editor del codice.

2. Compilare il gestore dell'evento SetButton_Click come indicato di seguito.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Questo codice imposta l'indirizzo Web che viene digitato nella casella di testo come destinazione per il Web browser. Se l'indirizzo non è valido, il codice genera un errore.

3. È anche necessario gestire l'evento WebFrame_Navigated:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Compilare la soluzione.

## <a name="add-the-user-control-to-the-start-page"></a>Aggiungere il controllo utente nella pagina iniziale

Per rendere disponibili per il progetto di pagina iniziale, questo controllo nel file di progetto di pagina di avvio, aggiungere un riferimento alla nuova libreria di controllo. È quindi possibile aggiungere il controllo al markup XAML pagina Start.

1. Nelle **Esplora soluzioni**, nel progetto di pagina iniziale, fare doppio clic su **riferimenti** e quindi fare clic su **Aggiungi riferimento**.

2. Nel **progetti** scheda, seleziona **WebUserControl** e quindi fare clic su **OK**.

3. Scegliere **Compila soluzione** dal menu **Compila**.

    La compilazione della soluzione rende il controllo utente disponibile per IntelliSense per gli altri file della soluzione.

    Per aggiungere il controllo al markup XAML pagina di avvio, aggiungere un riferimento all'assembly dello spazio dei nomi, quindi inserire il controllo nella pagina.

### <a name="to-add-the-control-to-the-markup"></a>Per aggiungere il controllo al markup

1. Nelle **Esplora soluzioni**, aprire la pagina di avvio *XAML* file.

2. Nel **XAML** riquadro, aggiungere la seguente dichiarazione dello spazio dei nomi di livello principale <xref:System.Windows.Controls.Grid> elemento.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. Nel **XAML** riquadro, scorrere verso il \<griglia > sezione.

    La sezione contiene un <xref:System.Windows.Controls.TabControl> elemento in un <xref:System.Windows.Controls.Grid> elemento.

4. Aggiungere un \<TabControl > elemento che contiene un \<TabItem > che contiene un riferimento a un controllo utente.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    È ora possibile testare il controllo.

## <a name="test-a-manually-created-custom-start-page"></a>Testare una pagina di avvio personalizzata creata manualmente

1. Copiare il file XAML e qualsiasi file di testo o markup supporto file, per il *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\*  cartella.

2. Se la pagina iniziale di fa riferimento a tutti i controlli o i tipi negli assembly che non sono installati da Visual Studio, copiare gli assembly e quindi incollarli nella _cartella di installazione di Visual Studio_ **\Common7\IDE\ PrivateAssemblies\\** .

3. Un prompt dei comandi di Visual Studio, digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.

4. Nell'istanza sperimentale, passare al **degli strumenti** > **opzioni** > **ambiente** > **avvio** pagina e selezionare il file XAML dal **Personalizza pagina iniziale** elenco a discesa.

5. Scegliere **Pagina iniziale** dal menu **Visualizza**.

    La pagina iniziale personalizzata deve essere visualizzata. Se si desidera modificare tutti i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi aprire nuovamente l'istanza sperimentale per visualizzare le modifiche.

## <a name="see-also"></a>Vedere anche

- [Controlli contenitore WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Procedura dettagliata: Aggiungere XAML personalizzato nella pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
