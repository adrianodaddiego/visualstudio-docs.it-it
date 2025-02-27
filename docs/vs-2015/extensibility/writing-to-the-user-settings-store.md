---
title: La scrittura in Store le impostazioni utente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408492"
---
# <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le impostazioni utente sono le impostazioni modificabili come quelli nel **Strumenti / opzioni** finestra di dialogo, finestre delle proprietà e alcune altre finestre di dialogo. Estensioni di Visual Studio possono usarle per archiviare piccole quantità di dati. Questa procedura dettagliata illustra come aggiungere il blocco note a Visual Studio come uno strumento esterno per leggere e scrivere nell'archivio delle impostazioni utente.  
  
### <a name="backing-up-your-user-settings"></a>Backup di impostazioni utente  
  
1. È necessario essere in grado di reimpostare le impostazioni di strumenti esterni, in modo che sia possibile eseguire il debug e ripetere la procedura. A tale scopo, è necessario salvare le impostazioni originali in modo che sia possibile ripristinarli in base alle esigenze.  
  
2. Aprire Regedit.exe.  
  
3. Passare a strumenti HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.  
  
    > [!NOTE]
    > Assicurarsi che si sta esaminando la chiave che contiene \14.0Exp\ e non \14.0\\. Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni utente sono nell'hive del Registro di sistema "14.0Exp".  
  
4. Pulsante destro del mouse sulla sottochiave \External Tools\ e quindi fare clic su **esportare**. Verificare che l'opzione **rami selezionati** sia selezionata.  
  
5. Salvare il file esterno Tools.reg risulta.  
  
6. In un secondo momento, quando si desidera reimpostare le impostazioni di strumenti esterni, selezionare la chiave del Registro di sistema Tools \ HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External e fare clic su **eliminare** nel menu di scelta rapida.  
  
7. Quando la **Conferma chiave di eliminazione** verrà visualizzata la finestra di dialogo, fare clic su **Yes**.  
  
8. Fare doppio clic il file esterno Tools.reg salvato in precedenza, fare clic su **Apri con**, quindi fare clic su **dell'Editor del Registro di sistema**.  
  
## <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente  
  
1. Creare un progetto VSIX denominato UserSettingsStoreExtension e quindi aggiungere un comando personalizzato denominato UserSettingsStoreCommand. Per altre informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. In UserSettingsStoreCommand.cs, aggiungere quanto segue usando istruzioni:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3. In MenuItemCallback, eliminare il corpo del metodo e ottenere l'utente archiviano le impostazioni, come indicato di seguito:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4. A questo punto è scoprire se il blocco note è già impostato come uno strumento esterno. È necessario scorrere tutti gli strumenti esterni per determinare se l'impostazione ToolCmd è "Notepad", come indicato di seguito:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5. Se il blocco note non è stato impostato come uno strumento esterno, impostarlo come indicato di seguito:  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6. Testare il codice. Tenere presente che aggiunge il blocco note come uno strumento esterno, pertanto è necessario il rollback del Registro di sistema prima di eseguirlo una seconda volta.  
  
7. Compilare il codice e avviare il debug.  
  
8. Nel **degli strumenti** menu, fare clic su **UserSettingsStoreCommand richiamare**. Verrà aggiunto il blocco note per la **strumenti** menu.  
  
9. Verrà ora visualizzato il blocco note sugli strumenti / opzioni di menu e scegliendo **Notepad** dovrebbe visualizzare un'istanza del blocco note.
