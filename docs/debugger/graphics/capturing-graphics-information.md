---
title: Acquisizione di informazioni grafiche | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d435ff9970748e8debe5edfd15514cde4f531b86
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63389701"
---
# <a name="capturing-graphics-information"></a>Acquisizione di informazioni grafiche
Acquisire informazioni grafiche dall'app Direct3D così da poter usare Analizzatore grafica di Visual Studio per diagnosticare i problemi di rendering e di prestazioni.

## <a name="capturing-graphics-information"></a>Acquisizione di informazioni grafiche
 L'acquisizione di informazioni grafiche è un processo costituito da due fasi. Innanzitutto, eseguire l'applicazione nella diagnostica della grafica, quindi specificare uno o più frame da cui acquisire informazioni dettagliate.

### <a name="to-run-your-app-under-graphics-diagnostics"></a>Per eseguire l'applicazione nella diagnostica della grafica

- Nella barra dei menu, scegliere **Debug**, **grafica**, **Avvia debug grafica**. (Tastiera: Premere ALT+F5)

- Nel **grafica** sulla barra degli strumenti, scegliere il **Avvia debug grafica** pulsante.

  Se un'app è in esecuzione nella diagnostica grafica, verranno costantemente acquisiti determinati tipi di informazioni grafiche, tra cui la configurazione dei dispositivi, la creazione della catena di scambio e di oggetti grafici e risorse, nonché altri eventi importanti che influiscono su più di un frame. Contemporaneamente, è possibile acquisire informazioni dettagliate su frame specifici; tali informazioni includono chiamate di disegno e invii di compute shader, oltre a risorse e oggetti Direct3D che li supportano.

### <a name="to-capture-a-frame"></a>Per acquisire un frame

- In Visual Studio sul **grafica** sulla barra degli strumenti, fare clic sui **Acquisisci Frame** pulsante ![icona pulsante acquisizione grafica](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").

- Sulla tastiera, premere il tasto STAMP.

  > [!NOTE]
  > Mentre un'app è in esecuzione in **Diagnostica della grafica**, è possibile usare il tasto STAMP solo per acquisire un frame di informazioni grafiche e non per eseguire la funzione standard. Questa condizione rimarrà attiva finché non si deciderà di interrompere l'acquisizione delle informazioni grafiche, in genere arrestando il debug o chiudendo l'app, anche se un'altra app presenta lo stato attivo.

- Nell'interfaccia di acquisizione di Visual Studio scegliere il pulsante **Acquisisci frame** che si trova sotto la sequenza temporale **Diagnostica sessione** o scegliere il pulsante di grandi dimensioni **Acquisisci frame** che si trova sotto la corsia **Frame al secondo** e a destra dei frame acquisiti in precedenza. Entrambi i pulsanti sono evidenziati nell'immagine seguente.

   ![Acquisire frame con lo strumento di uso della GPU.](media/pix_gpu_usage_tool_capture_frame.png)

   Quando si è pronti per esaminare i frame acquisiti, avviare **Analizzatore grafica di Visual Studio** facendo clic sul collegamento **Frame ...** sopra le anteprime delle immagini oppure facendo doppio clic sull'anteprima.

  È possibile acquisire solo frame interi e quindi, all'avvio di un'acquisizione, verranno effettivamente registrate le informazioni grafiche dal frame successivo. La registrazione inizierà immediatamente dopo aver verificato il frame in cui è stata avviata l'acquisizione e terminerà dopo aver verificato il frame acquisito. È possibile acquisire un numero indefinito di frame mentre l'app è in esecuzione nella diagnostica grafica. In assenza di frame acquisiti, il log di grafica verrà rimosso.

  Durante l'acquisizione dei frame, Visual Studio visualizza la finestra della sessione di diagnostica (con estensione diagsession). Se si chiude questa finestra, si arresta il debug o si chiude l'app, non sarà possibile acquisire altri frame nel log. Per acquisire più informazioni grafiche, è necessario eseguire nuovamente l'app in Diagnostica della grafica per avviare un nuovo log di grafica.

### <a name="graphics-diagnostics-capture-options"></a>Opzioni di acquisizione di diagnostica grafica
 È possibile configurare l'acquisizione per raccogliere stack di chiamate per tutti gli eventi grafici o per un subset limitato, per disabilitare l'HUD per l'acquisizione e per abilitare o disabilitare l'acquisizione in modalità di compatibilità.

#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Per configurare le opzioni di acquisizione di diagnostica della grafica

1. Nella barra dei menu scegliere Strumenti, Opzioni. Verrà visualizzata la finestra di dialogo Opzioni.

2. Nell'elenco di categorie delle opzioni a sinistra scegliere Diagnostica grafica, quindi configurare le opzioni desiderate di Diagnostica grafica.

     **Raccogli stack di chiamate durante l'acquisizione (rallenta l'acquisizione)** selezionare questa casella per raccogliere gli stack di chiamate. Per impostazione predefinita, gli stack di chiamate non vengono raccolti. Per acquisire gli stack di chiamate, assicurarsi che la casella di controllo **Raccogli stack di chiamate durante l'acquisizione (rallenta l'acquisizione)** sia selezionata e quindi impostare l'opzione **per indicatori _draw, dispatch, present e perf** (predefinita) per raccogliere solo gli stack di chiamate più importanti oppure l'opzione **per tutto** per raccogliere tutti gli stack di chiamate. Per interrompere la raccolta degli stack di chiamate in un momento successivo, deselezionare la casella di controllo **Raccogli stack di chiamate durante l'acquisizione (rallenta l'acquisizione)**.

     **Disabilita HUD di gioco durante l'acquisizione** controlla questa casella per disabilitare l'HUD sovrapporre che un'app in esecuzione con grafica diagnostica generalmente vengono visualizzati. Deselezionarla per visualizzare l'hud in sovraimpressione.

     **Acquisisci in modalità di compatibilità** selezionare questa casella per acquisire informazioni grafiche in modalità di compatibilità. L'acquisizione in modalità di compatibilità è l'impostazione predefinita. In modalità di compatibilità Direct3D non segnalerà che la GPU supporta tutte le funzionalità aggiuntive oltre a quelle definite nel livello funzionalità di base. Ciò impedisce all'app da acquisire di usare le estensioni specifiche dell'hardware della GPU su cui viene acquisita e assicura che il log di grafica possa essere riprodotto con qualsiasi GPU che supporta lo stesso livello funzionalità o un livello superiore. Deselezionare questa casella per disabilitare la modalità di compatibilità. I log acquisiti con la modalità di compatibilità disabilitata non verranno riprodotti su una GPU che non supporta le stesse funzionalità aggiuntive usate dall'app durante l'acquisizione.

     **Arrestare l'acquisizione se vengono rilevati errori livelli SDK** selezionare questa casella per interrompere immediatamente l'acquisizione se vengono rilevati errori.

## <a name="capturing-graphics-information-remotely"></a>Acquisizione remota di informazioni grafiche
 È possibile acquisire informazioni grafiche da un'app in esecuzione nel computer locale o in un computer o dispositivo remoto. L'acquisizione remota è supportata per i computer [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] e i dispositivi [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)]. Per acquisire informazioni grafiche da un'app in esecuzione in remoto, configurare il progetto per il debug remoto e quindi eseguire l'app nella diagnostica della grafica come descritto in precedenza. L'app viene eseguita nel computer remoto e le informazioni grafiche acquisite vengono registrate nel computer di sviluppo.

 La modalità di configurazione del progetto per il debug remoto varia a seconda del tipo di app sviluppata e dal linguaggio di programmazione in uso. Per informazioni su come configurare il debug remoto per un'app UWP, vedere [eseguire App UWP in un computer remoto](../run-windows-store-apps-on-a-remote-machine.md). Per informazioni su come configurare il debug remoto per un'app desktop di Windows, vedere [debug remoto](../remote-debugging.md).

 Successivamente sarà possibile usare un computer o un dispositivo remoto per riprodurre le informazioni grafiche, indipendentemente dall'origine dell'acquisizione. Per altre informazioni, vedere [Procedura: Modificare il computer di riproduzione della diagnostica della grafica](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="capturing-graphics-information-from-the-command-line"></a>Acquisizione di informazioni grafiche dalla riga di comando
 È possibile acquisire le informazioni grafiche da un'app con uno strumento da riga di comando. Questo strumento, DXCap.exe, può acquisire e riprodurre rapidamente le informazioni grafiche senza usare Visual Studio o l'acquisizione a livello di codice. In particolare, è possibile usare DXCap.exe per l'automazione o in un ambiente di test. Per altre informazioni su DXCap.exe, vedere [Strumento di acquisizione da riga di comando](command-line-capture-tool.md)

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Acquisizione di informazioni grafiche](walkthrough-capturing-graphics-information.md)