---
title: Dati di diagnostica e i log generati dal sistema
ms.date: 05/24/2018
ms.topic: conceptual
author: gewarren
ms.author: michma
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f92e899ff8e56c68fcf1a4ab639d027c139afcf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557398"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Log generati dal sistema raccolti da Visual Studio

Visual Studio raccoglie i log generati dal sistema per la risoluzione dei problemi e il miglioramento della qualità del prodotto tramite l'[Analisi utilizzo software](visual-studio-experience-improvement-program.md). Questo articolo offre informazioni sui tipi di dati raccolti e sul loro utilizzo. Vengono inoltre forniti suggerimenti sul modo in cui gli autori delle estensioni possono evitare la divulgazione accidentale di informazioni sensibili o personali.

## <a name="types-of-collected-data"></a>Tipi di dati raccolti

Visual Studio raccoglie i log generati dal sistema per gli arresti anomali, i blocchi, la mancanza di risposta dall'interfaccia utente e un utilizzo elevato della CPU o della memoria. Vengono anche raccolte informazioni sugli errori rilevati durante l'installazione o l'utilizzo del prodotto. I dati raccolti variano a seconda dell'errore e possono includere le analisi degli stack, i dump di memoria e le informazioni sulle eccezioni:

- Per l'utilizzo elevato della CPU e la mancanza di risposta, vengono raccolte le analisi degli stack dei thread di Visual Studio interessati.

- Per i casi in cui le analisi degli stack di alcuni thread non sono sufficienti per determinare la causa radice del problema, ad esempio per gli arresti anomali del sistema, i blocchi o l'utilizzo elevato della memoria, viene raccolto un *dump* della memoria. Il dump rappresenta lo stato del processo nel momento in cui si è verificato l'errore.

- Per le condizioni di errore imprevisto, ad esempio un'eccezione durante il tentativo di scrivere in un file su disco, vengono raccolte informazioni sull'eccezione. Le informazioni includono il nome dell'eccezione, l'analisi dello stack del thread in cui si è verificata l'eccezione, il messaggio associato all'eccezione e altre informazioni sull'eccezione specifica.

   L'esempio seguente di dati raccolti mostra un nome di eccezione, l'analisi dello stack e il messaggio di eccezione:

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>Come vengono usati i log generati dal sistema

Il flusso di lavoro per determinare la causa radice di un errore varia a seconda del tipo di errore e della sua gravità.

### <a name="error-classification"></a>Classificazione degli errori

In base ai log, gli errori sono classificati e conteggiati per stabilire la priorità della loro analisi. Ad esempio, è possibile che venga rilevato che l'errore "System.IO.\__Error.WinIOError" in "System.IO.FileStream.Init" si sia verificato 500 volte nella versione \<x> del prodotto e che abbia la frequenza più elevata in quella versione.

### <a name="work-items-for-tracking"></a>Elementi di lavoro per il rilevamento

Gli elementi di lavoro dei singoli errori in ordine di priorità vengono creati e assegnati ai tecnici per un'analisi più approfondita. Questi elementi di lavoro contengono in genere la classificazione, la priorità e le informazioni di diagnostica specifiche del tipo di errore. Queste informazioni sono derivate dai log generati dal sistema raccolti per l'errore. Ad esempio, un elemento di lavoro di un arresto anomalo del sistema può contenere la traccia dello stack in cui è in corso l'arresto anomalo.

### <a name="error-investigation"></a>Analisi degli errori

I tecnici usano le informazioni disponibili in un elemento di lavoro per determinare la causa radice di un errore. In alcuni casi i tecnici necessitano di altre informazioni non presenti nell'elemento di lavoro. In tal caso, fanno riferimento al log originale generato dal sistema. Ad esempio, è possibile che un tecnico controlli un dump di memoria per individuare la causa di un arresto anomalo del prodotto.

## <a name="tips-for-extension-authors"></a>Suggerimenti per gli autori delle estensioni

Gli autori delle estensioni devono limitare l'esposizione delle informazioni personali evitando di usare informazioni personali o riservate nei nomi dei moduli, dei tipi e dei metodi. Se si verifica un arresto anomalo del sistema o una condizione di errore simile, le informazioni vengono raccolte nell'ambito dei log generati dal sistema.

## <a name="opt-out-of-data-collection"></a>Rifiutare esplicitamente la raccolta dei dati

Considerate le finalità della raccolta dei dati e i vincoli di accesso e memorizzazione, si consiglia di usare le impostazioni di privacy predefinite di Visual Studio e Windows. È possibile tuttavia [rifiutare esplicitamente](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) il programma Analisi utilizzo software di Visual Studio. Per rifiutare esplicitamente la raccolta di log generati dal sistema per tutti i programmi, vedere [Diagnostica, feedback e privacy in Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Le opzioni possono variare a seconda della versione di Windows in uso.

## <a name="see-also"></a>Vedere anche

- [Analisi utilizzo software di Visual Studio](visual-studio-experience-improvement-program.md)
- [Diagnostica, feedback e privacy in Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)