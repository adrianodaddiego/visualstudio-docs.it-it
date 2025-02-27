---
title: Distribuire le app UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 02bfb1b4797973b3946405c38598409bf3247c70
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851744"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Distribuire app UWP da Visual Studio

La funzionalità di distribuzione di Visual Studio compila e registra le app UWP create con Visual Studio in un dispositivo di destinazione. Il modo in cui viene registrata l'app è determinato dal tipo di dispositivo, ovvero se è locale o remoto:

- Quando la destinazione è il computer Visual Studio locale, Visual Studio registra l'app dalla cartella della build dell'app stessa.

- Quando la destinazione è un dispositivo remoto, Visual Studio copia i file necessari nel computer remoto e registra l'app su questo dispositivo.

Distribuzione avviene automaticamente quando si esegue il debug dell'app da Visual Studio usando il **Avvia debug** opzione (tastiera: F5) o la **Avvia senza eseguire debug** opzione (tastiera: CTRL + F5). Puoi distribuire l'app anche manualmente. Ecco gli scenari in cui la distribuzione manuale può essere utile:

- Test ad hoc su un computer locale o remoto.

- Distribuzione di un'app che avvia un'altra app di cui vuoi eseguire il debug.

- Distribuzione di un'app di cui viene eseguito il debug quando viene avviata da un'altra app o da un altro metodo.

## <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Come distribuire un'app UWP
 La distribuzione manuale di un'app è un processo facile:

1. Se esegui la distribuzione in un dispositivo remoto, specifica il nome o l'indirizzo IP del dispositivo nella pagina delle proprietà del progetto di avvio dell'app. I passaggi necessari sono elencati più avanti in questo argomento.

2. Sulla barra degli strumenti Visual Studio del debugger seleziona la destinazione di distribuzione nell'elenco a discesa accanto al pulsante **Avvia debug** .

     ![Eseguire sul computer locale](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. Scegli **Distribuzione** dal menu **Compilazione**.

## <a name="BKMK_How_to_specify_a_remote_device"></a> Come specificare un dispositivo remoto

**Prerequisiti**

In un dispositivo remoto Windows 10, è necessario abilitare [modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development). Nei dispositivi Windows 10 che esegue Update Creators o versione successiva, remote tools vengono installati automaticamente quando si distribuisce l'app. Per altre informazioni, vedere [eseguire il Debug di un pacchetto dell'app installato](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Nelle versioni di pre-Creators Update di Windows 10, Remote Tools per Visual Studio deve essere installato nel dispositivo remoto e deve essere in esecuzione il debugger remoto.

La distribuzione usa il canale di rete del debugger remoto per inviare i file dell'app al dispositivo remoto.

#### <a name="to-specify-a-remote-device"></a>Per specificare un dispositivo remoto

1. Nella pagina delle proprietà Debug del progetto di avvio specifica il nome o l'indirizzo IP di una destinazione di distribuzione remota.

2. Per aprire la pagina delle proprietà Debug, seleziona il progetto in Esplora soluzioni e scegli **Proprietà** dal menu di scelta rapida.

3. Seleziona il nodo **Debug** nella finestra della pagina delle proprietà.

4. Per la **dispositivo di destinazione**, selezionare **computer remoto**.

5. Sotto **computer remoto**, fare clic su **trovare**.

6. È possibile digitare il nome o indirizzo IP del dispositivo remoto, oppure è possibile scegliere il dispositivo dal **connessione remota** nella finestra di dialogo.

    ![Finestra di dialogo Seleziona connessione Debugger remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    Il **connessione remota** nella finestra di dialogo Visualizza i dispositivi sulla subnet di rete locale e qualsiasi dispositivo che è direttamente connesso al computer Visual Studio tramite un cavo Ethernet.

   **Indicazione del dispositivo remoto in un oggetto visivo C++ pagina del progetto**

   ![C&#43; &#43; le proprietà per il debug remoto di progetto](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Scegliere **Debugger remoto** dall'elenco **Debugger da avviare** .

8. Immetti il nome di rete del dispositivo remoto nella casella **Nome computer** . In alternativa, puoi fare clic sulla freccia in giù della casella per selezionare il dispositivo nella finestra di dialogo Seleziona connessione debugger remoto.

   **Indicazione del dispositivo remoto nella pagina di un progetto Visual C# o Visual Basic**

   ![Proprietà del progetto per il debug remoto gestito](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Scegliere **Computer remoto** dall'elenco **Dispositivo di destinazione** .

10. Immetti il nome di rete del dispositivo remoto nella casella **Computer remoto** o fai clic su **Trova** per scegliere il dispositivo nella finestra di dialogo **Seleziona connessione debugger remoto** .

## <a name="BKMK_Deployment_options"></a> Opzioni di distribuzione

Di seguito sono indicate le opzioni di distribuzione che puoi impostare nella pagina delle proprietà Debug del progetto di avvio.

**Consenti loopback della rete locale**

Per motivi di sicurezza, una piattaforma UWP o [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app viene installata in modalità standard non è consentito effettuare chiamate di rete per il dispositivo in cui è installata. Per impostazione predefinita, la distribuzione di Visual Studio crea una esenzione da questa regola per l'app distribuita. Questa esenzione ti consente di verificare le procedure di comunicazione in un singolo computer. Prima di inviare l'app a [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], dovrai testarla senza l'esenzione.

Per rimuovere l'esenzione relativa al loopback della rete:

- Nel C# e il Debug di Visual Basic pagina delle proprietà, deseleziona il **Consenti loopback della rete locale** casella di controllo.

- Nel C++ pagina delle proprietà di Debug, impostare la **Consenti loopback della rete locale** valore per **No**.

**Non devono essere avviate, ma eseguine il debug del codice all'avvio (C# e Visual Basic) / /Avvia applicazione (C++)**

Per configurare la distribuzione in modo da avviare automaticamente una sessione di debug all'avvio dell'app:

- Nel C# e Visual Basic pagina delle proprietà Debug, controllare le **non, ma eseguine il debug del codice quando viene avviato** casella di controllo.

- Nel C++ pagina delle proprietà di Debug, impostare il **Avvia applicazione** valore **Yes**.

## <a name="see-also"></a>Vedere anche

- [Opzioni di distribuzione remota avanzata](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Eseguire il debug di un pacchetto dell'app installato](../debugger/debug-installed-app-package.md)
- [Eseguire app da Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
