---
title: Creazione e gestione delle finestre di dialogo modali | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2784135b1f3588047e03166a7302f3b8941c564
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338321"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Creare e gestire le finestre di dialogo modale
Quando si crea una finestra di dialogo modale in Visual Studio, è necessario assicurarsi che la finestra padre della finestra di dialogo è disabilitata mentre viene visualizzata la finestra di dialogo, quindi abilitare nuovamente la finestra padre si chiude la finestra di dialogo. Se non si esegue in modo che venga visualizzato l'errore: *Microsoft Visual Studio non è chiusa perché è attiva una finestra di dialogo modale. Chiudere la finestra di dialogo attiva e riprovare.*

Esistono due modi di questa operazione. Il metodo consigliato, se si dispone di una finestra di dialogo WPF, è necessario derivare da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, quindi chiamare <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> per visualizzare la finestra di dialogo. In questo caso, non devi gestire lo stato modale della finestra padre.

Se la finestra di dialogo non WPF o per un'altra classe motivo non è possibile derivare la finestra di dialogo <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, quindi è necessario ottenere l'elemento padre della finestra di dialogo chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> e di gestire lo stato modale, chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> metodo con un parametro pari a 0 (false) prima di visualizzare la finestra di dialogo e chiamando il metodo con un parametro 1 (true) dopo avere chiuso la finestra di dialogo.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Creare una finestra di dialogo derivata da DialogWindow

1. Creare un progetto VSIX denominato **OpenDialogTest** e aggiungere un comando di menu denominato **OpenDialog**. Per altre informazioni su come eseguire questa operazione, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Usare la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> (classe), è necessario aggiungere riferimenti agli assembly seguenti (nella scheda Framework del **Aggiungi riferimento** nella finestra di dialogo):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. Nelle *OpenDialog.cs*, aggiungere il codice seguente `using` istruzione:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Dichiarare una classe denominata `TestDialogWindow` che deriva da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Per essere in grado di ridurre al minimo e massimo la finestra di dialogo, impostare <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> e <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> su true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. Nel `OpenDialog.ShowMessageBox` (metodo), sostituire il codice esistente con il codice seguente:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Compilare ed eseguire l'applicazione. L'istanza sperimentale di Visual Studio dovrebbe essere visualizzato. Nel **degli strumenti** dal menu dell'istanza sperimentale dovrebbe essere un comando denominato **OpenDialog richiamare**. Quando si fa clic su questo comando, si verrà visualizzata la finestra di dialogo. Dovrebbe essere possibile per ridurre e ingrandire la finestra.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Creare e gestire una finestra di dialogo non derivata da DialogWindow

1. Per questa procedura, è possibile usare la **OpenDialogTest** soluzione creata nella procedura precedente, con i riferimenti all'assembly stesso.

2. Aggiungere il codice seguente `using` dichiarazioni:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Creare una classe denominata `TestDialogWindow2` che deriva da <xref:System.Windows.Window>:

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Aggiungere un riferimento a private <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```
    private IVsUIShell shell;
    ```

5. Aggiungere un costruttore che imposta il riferimento a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. Nel `OpenDialog.ShowMessageBox` (metodo), sostituire il codice esistente con il codice seguente:

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. Compilare ed eseguire l'applicazione. Nel **Tools** menu dovrebbe essere un comando denominato **richiamare OpenDialog**. Quando si fa clic su questo comando, si verrà visualizzata la finestra di dialogo.
