---
title: Guida introduttiva a diagnostica della grafica | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9056fdae9d0eff55c572d8e38503d88269dbde3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704712"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Guida introduttiva a Diagnostica grafica di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa sezione ci si prepara al primo utilizzo di Diagnostica della grafica, quindi si acquisisce un frame da un'app Direct3D e lo si esamina in Analizzatore grafica.

## <a name="requirements"></a>Requisiti
 Per usare Diagnostica della grafica in Visual Studio 2015 è necessario disporre di una di queste edizioni:

- Visual Studio 2015 Enterprise

- Visual Studio 2015 Professional

- Visual Studio 2015 Community

  [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]

### <a name="windows-10-prerequisites"></a>Prerequisiti di Windows 10
 La funzionalità opzionale di Windows *Strumenti di grafica* offre l'infrastruttura di acquisizione e riproduzione richiesta dalla Diagnostica della grafica in Windows 10.

 Per informazioni sull'installazione di Strumenti di grafica, vedere [Installare Strumenti di grafica per Windows 10](#InstallGraphicsTools).

### <a name="windows-81-prerequisites"></a>Prerequisiti di Windows 8.1
 Windows Software Development Kit (SDK) per Windows 8.1 fornisce l'infrastruttura di acquisizione e riproduzione richiesti dalla diagnostica della grafica in Windows 8.1 e supporta lo sviluppo per Windows 8.1 e Windows 8.

 [Scaricare Windows Software Development Kit (SDK) per Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)

 Per usare un computer di riproduzione remoto che esegue Windows 10 da un computer di sviluppo con Windows 8.1, è necessario installare Windows 10 SDK nel computer di sviluppo e la funzionalità opzionale Strumenti di grafica nel computer di riproduzione.

## <a name="InstallGraphicsTools"></a> Installare Strumenti di grafica per Windows 10
 In Windows 10, l'infrastruttura di diagnostica grafica viene offerta attraverso la funzionalità facoltativa di Windows denominata *Strumenti di grafica*. Questa funzionalità è necessaria per acquisire e riprodurre le informazioni di grafica in Windows 10 indipendentemente dal fatto che l'app acquisita abbia come destinazione una versione precedente di Windows e dalla versione di Direct3D in uso. Si può scegliere di installare la funzionalità di Strumenti di grafica in anticipo; in caso contrario, sarà installata su richiesta al primo avvio di una sessione di Diagnostica grafica da Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Per installare Strumenti di grafica per Windows 10

1. Nel **avviare** menu, scegliere **impostazioni**. Il **impostazioni** viene visualizzata la finestra.

2. Nel **le impostazioni** finestra di dialogo, scegliere **System**, quindi selezionare **le app installate** dall'elenco di impostazioni di sistema.

3. Sul lato destro del **le impostazioni** finestra di dialogo scegliere **Gestisci funzionalità facoltative** sotto **installata l'App e funzionalità**. Viene visualizzata la finestra di dialogo **Gestisci funzionalità facoltative**.

4. Nella finestra di dialogo **Gestisci funzionalità facoltative** scegliere **Aggiungi una funzionalità**. Viene visualizzato un elenco di funzionalità facoltative che è possibile installare.

5. Selezionare **Strumenti di grafica** nell'elenco di funzionalità e quindi scegliere **Installa**.

   La funzionalità Strumenti di grafica viene inoltre installata automaticamente quando si installa Windows SDK 10.

> [!TIP]
> La funzionalità facoltativa di Windows 10 Strumenti di grafica offre funzionalità leggere di acquisizione e riproduzione, ad esempio il programma di acquisizione da riga di comando **dxcap.exe**, che può essere usato in scenari di supporto, testing e diagnostica nei computer in cui non sono installati gli strumenti di sviluppo. Per altre informazioni, vedere l'argomento [Strumento di acquisizione da riga di comando](../debugger/command-line-capture-tool.md).

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Primo utilizzo di Diagnostica della grafica
 Ora che si dispone di tutto il necessario, è possibile iniziare a usare Diagnostica della grafica eseguendo le operazioni descritte nei passaggi seguenti.

### <a name="1---create-a-direct3d-app"></a>1 - Creare un'app Direct3D
 Se si dispone già di un'app Direct3D con cui esplorare Diagnostica della grafica, passare al punto successivo. In caso contrario, si può usare uno degli esempi di Direct3D disponibili in Code Gallery.

- Per provare diagnostica della grafica con Direct3D 12 su Windows 10 usando Visual Studio 2015, provare il [esempio Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) per Windows 10.

- Per provare diagnostica della grafica con Direct3D 11 su Windows 10 o Windows 8.1, è possibile usare la **App DirectX (Windows universale)** oppure **App DirectX (Windows 8.1)** modelli di progetto. O, per operazioni più complesse, provare il [esempio di gioco marble maze DirectX](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) per Windows 8.1.

  Verificare che sia possibile compilare l'applicazione prima di andare avanti.

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - Avviare una sessione di Diagnostica grafica
 A questo punto si è pronti per avviare la prima sessione di diagnostica della grafica. In Visual Studio, nel menu principale, scegliere **eseguire il Debug, grafica, avvia diagnostica**, oppure premere **ALT+F5**. L'app viene avviata in Diagnostica grafica e in Visual Studio vengono visualizzate le finestre della sessione di diagnostica.

> [!IMPORTANT]
> Se si esegue l'app in Windows 10 e non si è ancora installata la funzionalità facoltativa Strumenti di grafica, verrà richiesto di farlo ora. La funzionalità deve essere installata per poter usare Diagnostica della grafica in Windows 10.

### <a name="3---capture-frames"></a>3 - Acquisire frame
 Non appena l'app si avvia, è possibile iniziare ad acquisire frame.

##### <a name="to-capture-single-frames"></a>Per acquisire singoli frame

- In Visual Studio scegliere il pulsante nella barra degli strumenti **Acquisisci frame** nella barra degli strumenti di grafica o nella finestra della sessione di diagnostica. Oppure, se l'app ha lo stato attivo, premere **Stamp**.

##### <a name="to-capture-a-sequence-of-frames"></a>Per acquisire una sequenza di frame

- In Visual Studio, nella finestra della sessione di diagnostica impostare **Frame da acquisire** sul numero di frame da acquisire in sequenza, quindi acquisire la sequenza usando uno dei metodi descritti in precedenza per acquisire singoli frame.

   Per acquisire nuovamente singoli frame, impostare **frame da acquisire** a `1`.

  Al termine dell'operazione di acquisizione dei frame, uscire dall'app o scegliere il pulsante **Arresta** nella barra degli strumenti di grafica o nella finestra della sessione di diagnostica.

### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4 - Esaminare i frame acquisiti in Analizzatore grafica
 A questo punto si è pronti per esaminare i frame acquisiti. Per iniziare ad analizzare un frame, scegliere il numero del frame da esaminare nella finestra della sessione di diagnostica. Il frame verrà aperto in **Analizzatore grafica** dove è possibile servirsi degli strumenti di Diagnostica della grafica per esaminare il modo in cui l'app usa Direct3D per individuare i problemi di rendering oppure usare lo strumento **Analisi dei frame** per comprenderne le prestazioni.

 Se è stato selezionato frame errato nella finestra della sessione di diagnostica oppure si vuole esaminare un frame diverso, è possibile selezionare un altro da Analizzatore grafica. Nella scheda **Destinazione rendering** della finestra del log di grafica, sotto l'immagine della destinazione di rendering, espandere l'**Elenco frame** e quindi scegliere un altro frame da esaminare.

 Per altre informazioni su come usare gli strumenti di Analizzatore grafica tra loro, vedere la [esempi](../debugger/graphics-diagnostics-examples.md).

## <a name="see-also"></a>Vedere anche
 [Grafica Direct3D 12](https://msdn.microsoft.com/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)
