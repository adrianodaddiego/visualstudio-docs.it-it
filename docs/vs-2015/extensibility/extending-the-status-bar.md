---
title: Estendere la barra di stato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28fc1155279ec624cea576b5a70a25800d4ff837
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101067"
---
# <a name="extending-the-status-bar"></a>Estensione della barra di stato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare la barra di stato di Visual Studio nella parte inferiore dell'IDE per visualizzare le informazioni.  
  
 Quando si estende la barra di stato, è possibile visualizzare le informazioni e l'interfaccia utente in quattro aree: l'area commenti e suggerimenti, l'indicatore di stato, l'area animazione e l'area di progettazione. L'area commenti e suggerimenti consente di visualizzare il testo ed evidenziare il testo visualizzato. L'indicatore di stato Mostra lo stato incrementale per le operazioni a esecuzione breve, ad esempio salvataggio di un file. L'area animazione visualizza un'animazione chiuso in modo continuativo per le operazioni a esecuzione prolungata o operazione di lunghezza non determinata, quali la creazione di più progetti in una soluzione. E l'area di progettazione Mostra il numero di riga e alla colonna della posizione del cursore.  
  
 È possibile ottenere la barra di stato usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfaccia (dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> servizio). Inoltre, qualsiasi oggetto individuato in una cornice di finestra può registrare lo stato della barra di oggetto client mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfaccia. Ogni volta che una finestra viene attivata, Visual Studio esegue una query dell'oggetto individuato in tale finestra di `IVsStatusbarUser` interfaccia. Se viene trovato, verrà chiamata la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo sull'oggetto e l'interfaccia restituita è possibile aggiornare la barra di stato dall'interno di tale metodo. Documenti di windows, ad esempio, possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo per aggiornare le informazioni nell'area di progettazione quando diventano attivi.  
  
 Le procedure seguenti presuppongono che si sappiano creare un progetto VSIX e aggiungere un comando di menu personalizzato. Per informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Modificare la barra di stato  
 Questa procedura viene illustrato come impostare e ottenere il testo, visualizzare il testo statico ed evidenziare il testo visualizzato nell'area commenti e suggerimenti della barra di stato.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Lettura e scrittura per la barra di stato  
  
1. Creare un progetto VSIX denominato **TestStatusBarExtension** e aggiungere un comando di menu denominato **TestStatusBarCommand**.  
  
2. In TestStatusBarCommand.cs, sostituire il codice del metodo del gestore comando (MenuItemCallback) con gli elementi seguenti:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3. Compilare il codice e avviare il debug.  
  
4. Aprire il **strumenti** menu nell'istanza sperimentale di Visual Studio. Scegliere il **richiamare TestStatusBarCommand** pulsante.  
  
     Si noterà che il testo nella barra ora letture di stato **"Abbiamo appena scritto nella barra di stato."** la finestra di messaggio visualizzato è lo stesso testo.  
  
#### <a name="updating-the-progress-bar"></a>Aggiornare l'indicatore di stato  
  
1. In questa procedura si mostrerà come inizializzare e aggiornare l'indicatore di stato.  
  
2. Aprire il file TestStatusBarCommand.cs e sostituire il metodo MenuItemCallback con il codice seguente:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3. Compilare il codice e avviare il debug.  
  
4. Aprire il **strumenti** menu nell'istanza sperimentale di Visual Studio. Fare clic su **richiamare TestStatusBarCommand** pulsante.  
  
     Si noterà che il testo nella barra ora letture di stato **"scrittura per l'indicatore di stato."** Si dovrebbe vedere anche l'indicatore di stato vengono aggiornati ogni secondo per 20 secondi. Dopo che la barra di stato e l'indicatore di stato vengono cancellati.  
  
#### <a name="displaying-an-animation"></a>Visualizzazione di un'animazione  
  
1. La barra di stato Visualizza un'animazione di ciclo che indica un'operazione a esecuzione prolungata (ad esempio, la creazione di più progetti in una soluzione). Se non viene visualizzata questa animazione, assicurarsi di avere i valori corretti **Strumenti / opzioni** impostazioni:  
  
     Andare alla **Strumenti/opzioni / Generale** scheda e deselezionare **regola automaticamente esperienza visiva in base alle prestazioni del client**. Quindi selezionare l'opzione secondaria **Abilita esperienza visiva dettagliata del client**. A questo punto sarà possibile visualizzare l'animazione quando si compila il progetto nell'istanza sperimentale di Visual Studio.  
  
     In questa procedura viene visualizzato l'animazione di Visual Studio standard, che rappresenta la creazione di un progetto o soluzione.  
  
2. Aprire il file TestStatusBarCommand.cs e sostituire il metodo MenuItemCallback con il codice seguente:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3. Compilare il codice e avviare il debug.  
  
4. Aprire il **degli strumenti** menu nell'istanza sperimentale di Visual Studio e fare clic su **richiamare TestStatusBarCommand**.  
  
     Quando viene visualizzata la finestra di messaggio, si dovrebbe vedere anche l'animazione nella barra di stato all'estrema destra. Appena si chiude la finestra di messaggio, l'animazione viene rimosso.
