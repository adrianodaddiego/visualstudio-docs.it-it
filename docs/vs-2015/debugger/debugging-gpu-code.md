---
title: Debug del codice GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb5342dc2b5da3d1192aadbbea186b5b21f179f3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691559"
---
# <a name="debugging-gpu-code"></a>Debug del codice GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile eseguire il debug del codice C++ in esecuzione nell'unità di elaborazione grafica (GPU). Il supporto del debug di GPU in Visual Studio include il rilevamento di race condition, l'avvio di processi e la connessione a essi e l'integrazione nelle finestre di debug.  
  
## <a name="supported-platforms"></a>Piattaforme supportate  
 Il debug è supportato in [!INCLUDE[win7](../includes/win7-md.md)], [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)] e [!INCLUDE[winserver8](../includes/winserver8-md.md)]. Per eseguire il debug nell'emulatore software, è necessario disporre di [!INCLUDE[win8](../includes/win8-md.md)] o [!INCLUDE[winserver8](../includes/winserver8-md.md)]. Per eseguire il debug nell'hardware, è necessario installare i driver per la scheda grafica. Non tutti i fornitori di hardware implementano tutte le funzionalità del debugger. Vedere la documentazione del fornitore per eventuali limitazioni.  
  
> [!NOTE]
> I fornitori di hardware indipendenti che desiderano supportare il debug della GPU in Visual Studio devono creare una DLL che implementi l'interfaccia di VSD3DDebug e faccia riferimento ai propri driver.  
  
## <a name="configuring-gpu-debugging"></a>Configurazione del debug della GPU  
 Il debugger non può interrompere sia il codice della CPU sia quello della GPU nell'esecuzione della stessa app. Per impostazione predefinita, il debugger interrompe il codice della CPU. Per eseguire il debug del codice della GPU, utilizzare uno dei due passaggi seguenti:  
  
- Nell'elenco **Tipo di debug** sulla barra degli strumenti **Standard** scegliere **Solo GPU**.  
  
- In **Esplora soluzioni** scegliere **Proprietà** dal menu di scelta rapida del progetto. Nella finestra di dialogo **Pagine delle proprietà** selezionare **Debug** e **Solo GPU** nell'elenco **Tipo di debugger**.  
  
## <a name="launching-and-attaching-to-applications"></a>Avvio e associazione di applicazioni  
 È possibile utilizzare i comandi di debug di Visual Studio per avviare e interrompere il debug della GPU. Per altre informazioni, vedere [Navigating through Code with the Debugger](../debugger/navigating-through-code-with-the-debugger.md) (Spostarsi nel codice con il Debugger). È inoltre possibile associare il debugger della GPU a un processo in esecuzione, ma solo se tale processo esegue codice della GPU. Per altre informazioni, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Esegui Tile corrente fino al cursore ed Esegui fino al cursore  
 Quando si esegue il debug nella GPU, sono disponibili due opzioni per l'esecuzione fino alla posizione del cursore. I controlli per entrambe le opzioni sono disponibili nel menu di scelta rapida dell'editor di codice.  
  
1. Con il comando **Esegui fino al cursore** l'app viene eseguita finché non raggiunge la posizione del cursore, quindi si interrompe. Ciò non implica che il thread corrente venga eseguito fino al cursore, ma piuttosto che il primo thread che raggiunge il punto del cursore genera l'interruzione. Vedere [spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)  
  
2. Con il comando **Esegui Tile corrente fino al cursore** l'app viene eseguita finché tutti thread nel tile corrente non raggiungono il cursore, quindi si interrompe.  
  
## <a name="debugging-windows"></a>Debug di Windows  
 L'utilizzo di alcune finestre di debug consente di esaminare, contrassegnare e bloccare i thread della GPU. Per altre informazioni, vedere:  
  
- [Uso della finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)  
  
- [Uso della finestra Attività](../debugger/using-the-tasks-window.md)  
  
- [Procedura: Usare la finestra Espressione di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md)  
  
- [Eseguire il debug di thread e processi](../debugger/debug-threads-and-processes.md) (barra degli strumenti posizione di Debug)  
  
- [Procedura: Usare la finestra Thread GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## <a name="data-synchronization-exceptions"></a>Eccezioni di sincronizzazione dei dati  
 Il debugger può identificare diverse condizioni di sincronizzazione dei dati durante l'esecuzione. Quando viene rilevata una condizione, il debugger attivo lo stato di interruzione. Sono disponibili due opzioni: **Interrompi** o **Continua**. Tramite la finestra di dialogo **Eccezioni** è possibile configurare il debugger affinché rilevi o meno tali condizioni nonché quali condizioni causano l'interruzione. Per altre informazioni, vedere [la gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md). È anche possibile usare la **opzioni** finestra di dialogo per specificare che il debugger deve ignorare le eccezioni se i dati scritti non modificano il valore dei dati. Per altre informazioni, vedere [General, Debugging, Options Dialog Box](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
  
### <a name="specifying-an-accelerator"></a>Specifica di un acceleratore  
 I punti di interruzione nel codice della GPU vengono raggiunti solo se il codice è in esecuzione nell'acceleratore [accelerator::direct3d_ref](https://msdn.microsoft.com/library/a514b1a7-3b3f-4011-be6c-f7b0d9a42663) (REF). Se non si specifica un acceleratore nel codice, l'acceleratore REF viene automaticamente selezionato come **Tipo acceleratore debug** nelle proprietà del progetto. Se il codice seleziona in modo esplicito un acceleratore, l'acceleratore REF non viene utilizzato durante il debug e i punti di interruzione non vengono raggiunti a meno che l'hardware della GPU non supporti il debug. È possibile risolvere questo problema scrivendo il codice in modo da utilizzare l'acceleratore REF durante il debug. Per altre informazioni, vedere le proprietà del progetto e [utilizzo degli oggetti accelerator e accelerator_view](https://msdn.microsoft.com/library/18f0dc66-8236-4420-9f46-1a14f2c3fba1) e [impostazioni di progetto per un C++ Debug Configuration](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="conditional-breakpoints"></a>Punti di interruzione condizionali  
 I punti di interruzione condizionali nel codice della GPU sono supportati, ma non è possibile valutare tutte le espressioni nel dispositivo. Quando un'espressione non può essere valutata nel dispositivo, essa viene valutata nel debugger. È probabile che il debugger sia più lento del dispositivo.  
  
### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Errore: Si verifica un problema di configurazione con il tipo di acceleratore di debug selezionato.  
 Questo errore si verifica quando è presente un'incoerenza tra le impostazioni del progetto e la configurazione del PC in cui si esegue il debug. Per altre informazioni, vedere [impostazioni di progetto per una configurazione di Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Errore: Il driver di debug per il tipo di acceleratore di debug selezionato non è installato nel computer di destinazione.  
 Questo errore si verifica se si esegue il debug in un computer remoto. Il debugger non è in grado di determinare se i driver sono installati nel computer remoto fino al runtime. I driver sono disponibili tramite il produttore della scheda grafica.  
  
### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Errore: Timeout Detection and Recovery (TDR) deve essere disabilitati nel sito remoto.  
 È possibile che i calcoli di C++ AMP superino l'intervallo predefinito impostato tramite il processo Timeout Detection and Recovery (TDR) di Windows. In tal caso, il calcolo viene annullato e i dati vengono persi. Per ulteriori informazioni, vedere [Gestione di TDR in C++ AMP](http://go.microsoft.com/fwlink/p/?LinkId=249154).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Debug di un'applicazione C++ AMP](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Avviare il debug della GPU in Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=255381)
