---
title: Uso dei file Dump | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 56
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a316006ba8983e00906e041d243d8f7c82d6277
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684292"
---
# <a name="using-dump-files"></a>Uso di file dump
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

File dump con o senza heap; creare un file dump; aprire un file dump; individuare i file binari, i file pdb e il file di origine di un file dump. 
  
## <a name="BKMK_Contents"></a> Contenuto  
 [Che cos'è un file di dump?](#BKMK_What_is_a_dump_file_)  
  
 [File di dump, con o senza heap](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Requisiti e limitazioni](#BKMK_Requirements_and_limitations)  
  
 [Creare un file dump](#BKMK_Create_a_dump_file)  
  
 [Aprire un file dump](#BKMK_Open_a_dump_file)  
  
 [Trovare i file binari, i file di simboli (PDB) e i file di origine](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
## <a name="BKMK_What_is_a_dump_file_"></a> Che cos'è un file di dump?  
 Oggetto *file di dump* è uno snapshot di un'app in corrispondenza del punto nel tempo viene impiegato il dump. Indica il processo in esecuzione e i moduli caricati. Se il dump è stato salvato con informazioni heap, contiene uno snapshot delle attività svolte nella memoria dell'app in quel momento. L'apertura di un file dump con un heap in Visual Studio è simile all'arresto in corrispondenza di un punto di interruzione in una sessione di debug. Sebbene non sia possibile continuare l'esecuzione, è possibile esaminare gli stack, i thread e i valori delle variabili dell'app al momento in cui si è verificato il dump.  
  
 I dump vengono utilizzati principalmente per il debug di problemi che si verificano nei computer a cui lo sviluppatore non ha accesso. Ad esempio, è possibile utilizzare un file dump del computer di un cliente quando non è possibile riprodurre nel proprio computer il blocco o l'arresto anomalo avvenuto nel computer del cliente. I dump vengono inoltre creati dai tester per salvare i dati relativi a un arresto anomalo o un blocco per eseguire altre verifiche nel computer di test. Il debugger di Visual Studio può salvare i file dump per il codice gestito o nativo. Il debugger può caricare i file dump creati da Visual Studio o da altri programmi che salvano i file nei *minidump* formato.  
  
 ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
## <a name="BKMK_Dump_files__with_or_without_heaps"></a> File di dump, con o senza heap  
 È possibile creare file dump con o senza informazioni heap.  
  
- **File dump con heap** contengono uno snapshot della memoria dell'app. Sono inclusi i valori delle variabili al momento della creazione del dump. Se si carica un file dump salvato con un heap, Visual Studio potrà caricare i simboli anche se il file binario dell'applicazione non è disponibile. Visual Studio salva inoltre i file binari dei moduli nativi caricati nel file dump, che possono semplificare il debug.  
  
- **File dump senza heap** sono molto più piccoli dei dump contenenti informazioni sull'heap. Il debugger deve tuttavia caricare i file binari dell'app per trovare informazioni sui simboli. I file binari devono corrispondere esattamente ai file binari utilizzati alla creazione del dump. Solo i valori delle variabili dello stack vengono salvati nei file dump senza dati dell'heap.  
  
  ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
## <a name="BKMK_Requirements_and_limitations"></a> Requisiti e limitazioni  
  
- Il debug di file dump del codice ottimizzato può generare confusione. Ad esempio, l'incorporamento di funzioni del compilatore può comportare stack di chiamate imprevisti e altre ottimizzazioni potrebbero modificare la durata delle variabili.  
  
- Il debug dei file dump di computer a 64 bit deve essere eseguito in un'istanza di Visual Studio in esecuzione in un computer a 64 bit.  
  
- Nelle versioni di Visual Studio precedenti a VS 2013, i dump delle app a 32 bit eseguite in computer a 64 bit raccolti da alcuni strumenti (ad esempio Gestione attività e WinDbg a 64 bit) potrebbero non essere aperti in Visual Studio. In VS 2013 questa limitazione è stata eliminata.  
  
- Visual Studio può eseguire il debug dei file dump delle app native di dispositivi ARM. Visual Studio può inoltre eseguire il debug dei file dump di app gestite di dispositivi ARM, ma solo nel debugger nativo.  
  
- Per eseguire il debug [in modalità kernel](https://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) dump file in Visual Studio 2013, scaricare la [Windows 8.1 versione di debug di strumenti per Windows](https://msdn.microsoft.com/windows/hardware/gg463009). Visualizzare [debug del Kernel in Visual Studio](https://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- Visual Studio non è possibile eseguire il debug di file dump salvati nel formato dump precedente noto come un [dump completi della modalità utente](/windows-hardware/drivers/debugger/user-mode-dump-files#full). Si noti che un dump completo in modalità utente non corrisponde a un dump con heap.  
  
- Eseguire il debug con il [SOS. dll (estensione del debugger SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) in Visual Studio, è necessario installare il debug di strumenti per Windows che fa parte del Windows Driver Kit (WDK). Vedere [Windows 8.1 Preview: Download di Kit, bit e strumenti](https://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
## <a name="BKMK_Create_a_dump_file"></a> Creare un file dump  
 Per creare un file dump con Visual Studio:  
  
- Durante il debug di un processo in Visual Studio, è possibile salvare un file dump quando il debugger è stato arrestato in corrispondenza di un'eccezione o di un punto di interruzione. Scegli **Salva Dump con nome**, **Debug**. Nel **Salva Dump con nome** nella finestra di dialogo il **Salva come tipo** elenco, è possibile selezionare **Minidump** oppure **Minidump con Heap** (predefinito).  
  
- Con [debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md) abilitata, è possibile collegare il debugger a un processo arrestatosi in modo anomalo è in esecuzione all'esterno del debugger e salvare un file di dump. Vedere [collegare ai processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  È inoltre possibile creare file dump con qualsiasi programma che supporta il formato di minidump di Windows. Ad esempio, il **Procdump** utilità della riga di comando da [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) può creare file dump di arresto anomalo del processo basati su trigger o su richiesta. Visualizzare [requisiti e limitazioni](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) in questo argomento per ulteriori informazioni sull'uso di altri strumenti per creare file dump.  
  
  ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
## <a name="BKMK_Open_a_dump_file"></a> Aprire un file dump  
  
1. In Visual Studio, scegliere **File**, **Open**, **File**.  
  
2. Nella finestra di dialogo **Apri file** individuare e selezionare il file dump. Il file dump in genere ha l'estensione dmp. Scegliere quindi **OK**.  
  
3. Il **riepilogo File Dump** verrà visualizzata la finestra. In questa finestra è possibile visualizzare informazioni di riepilogo sul debug del file dump, impostare il percorso dei simboli, avviare il debug e copiare le informazioni di riepilogo negli Appunti.  
  
     ![Pagina di riepilogo minidump](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4. Per avviare il debug, vedere il **azioni** sezione e scegliere **eseguire il Debug con solo nativo** o **Esegui Debug con misto**.  
  
## <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Trovare i file binari, i file di simboli (PDB) e i file di origine  
 Per utilizzare le funzionalità complete di Visual Studio per eseguire il debug di un file dump, è necessario accedere a:  
  
- File exe per cui il dump è stato creato e altri file binari (DLL e così via) utilizzati nel processo del dump.  
  
   Se si esegue il debug di un dump con dati dell'heap, Visual Studio può ovviare alla mancanza dei file binari per alcuni moduli, ma deve disporre dei file binari per un numero sufficiente di moduli per generare stack di chiamate validi. Visual Studio include i moduli nativi in un file dump con heap.  
  
- File di simboli (con estensione pdb) per il file con estensione exe e altri binari.  
  
- File di origine dei moduli a cui si è interessati.  
  
   I file eseguibili e i file con estensione pdb devono corrispondere esattamente alla versione e alla compilazione dei file utilizzati alla creazione del dump.  
  
   È possibile eseguire il debug utilizzando il disassembly dei moduli se non è possibile trovare i file di origine.  
  
  **Percorsi di ricerca predefinito per i file eseguibili**  
  
  Visual Studio esegue automaticamente la ricerca di questi percorsi per i file eseguibili che non sono inclusi nel file dump:  
  
1. Directory che contiene il file dump.  
  
2. Il percorso del modulo specificato nel file dump. Si tratta del percorso del modulo nel computer in cui è stato recuperato il dump.  
  
3. I percorsi di simboli specificati nella **Debugging**, **opzioni**, **simboli** pagina di Visual Studio **strumenti**, **opzioni**  nella finestra di dialogo. È possibile aggiungere più posizioni per effettuare la ricerca in questa pagina.  
  
   **Utilizzando il No Binary / simbolo / pagine di origine**  
  
   Se Visual Studio non trova i file necessari per eseguire il debug di un modulo nel dump, visualizzata una pagina appropriata (**Nessun file binario trovato**, **Nessun simbolo trovato**, o **Nessuna origine trovata**). Queste pagine forniscono informazioni dettagliate sulla causa del problema e vengono forniti collegamenti ad azioni che consentono di identificare il percorso corretto dei file. Vedere [Specificare file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
## <a name="see-also"></a>Vedere anche  
 [Debug Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)
