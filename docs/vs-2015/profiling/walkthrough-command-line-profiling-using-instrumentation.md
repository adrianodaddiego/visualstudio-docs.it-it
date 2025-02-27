---
title: 'Procedura dettagliata: Profilatura dalla riga di comando tramite Strumentazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a37350cf274fbb551326ac96387330b0f3956e7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439690"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>Procedura dettagliata: Riga di comando di profilatura tramite Strumentazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene descritto come eseguire la profilatura di un'applicazione autonoma [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] per raccogliere informazioni dettagliate sugli intervalli e dati sul numero di chiamate tramite il metodo di strumentazione degli strumenti di profilatura. In questa procedura dettagliata, si completeranno le attività seguenti:  
  
- Usare lo strumento della riga di comando [VSInstr](../profiling/vsinstr.md) per generare file binari instrumentati.  
  
- Usare lo strumento [VSPerfCLREnv](../profiling/vsperfclrenv.md) per impostare le variabili di ambiente per la raccolta dei dati di profilatura .NET.  
  
- Usare lo strumento [VSPerfCmd](../profiling/vsperfcmd.md) per raccogliere i dati di profilatura.  
  
- Usare lo strumento [VSPerfReport](../profiling/vsperfreport.md) per generare report basati su file dei dati di profilatura.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
- [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
- Conoscenza a livello intermedio di C#  
  
- Conoscenza a livello intermedio dell'uso degli strumenti da riga di comando  
  
- Una copia dell'[esempio PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Per usare le informazioni fornite dalla profilatura, è consigliabile avere a disposizione informazioni sui simboli di debug. Per altre informazioni, vedere [Procedura: Informazioni sui simboli di riferimento Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Profilatura dalla riga di comando tramite il metodo di strumentazione  
 La strumentazione è un metodo di profilatura in cui vengono usate particolari versioni dei file binari profilati, contenenti funzioni probe che raccolgono informazioni sugli intervalli all'ingresso e all'uscita dalle funzioni in un modulo instrumentato. Poiché questo metodo di profilatura è più invasivo rispetto al campionamento, comporta un sovraccarico maggiore. I file binari instrumentati sono anche più grandi dei file binari di debug o di rilascio e non sono destinati alla distribuzione.  
  
> [!NOTE]
> Non inviare file binari instrumentati ai clienti. I file binari instrumentati possono presentare diversi rischi. I file binari contengono informazioni che possono agevolare la decompilazione dell'applicazione, oltre a comportare rischi per la sicurezza.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>Per eseguire la profilatura dell'applicazione PeopleTrax tramite il metodo di strumentazione  
  
1. Installare l'applicazione di esempio PeopleTrax e compilare la versione di rilascio.  
  
2. Aprire una finestra del prompt dei comandi e aggiungere la directory degli **strumenti di profilatura** alla variabile di ambiente Path locale.  
  
3. Cambiare la directory di lavoro, passando alla directory che contiene i file binari di PeopleTrax.  
  
4. Creare una directory in cui saranno contenuti i report basati su file. Digitare il comando seguente:  
  
    ```  
    md Reports  
    ```  
  
5. Usare lo strumento da riga di comando VSInstr per instrumentare i file binari nell'applicazione. Digitare i comandi seguenti in righe di comando distinte:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Nota** Per impostazione predefinita, VSInstr salva una copia di backup non instrumentata del file originale. Il nome del file di backup ha l'estensione orig. Ad esempio, la versione originale di "MyApp.exe" viene salvata con il nome "MyApp.exe.orig".  
  
6. Digitare il comando seguente per impostare le variabili di ambiente appropriate:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7. Per avviare il profiler, digitare il comando seguente:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8. Dopo avere avviato il profiler in modalità di traccia, eseguire la versione instrumentata del processo PeopleTrax.exe per raccogliere i dati.  
  
     Verrà visualizzata la finestra dell'applicazione **PeopleTrax**.  
  
9. Fare clic su **Get People**.  
  
     Verranno inseriti dati nella griglia dei dati di PeopleTrax.  
  
10. Fare clic su **Esporta dati**.  
  
     Verrà avviato il Blocco note e sarà visualizzato un nuovo file che contiene un elenco di persone dell'applicazione **PeopleTrax**.  
  
11. Chiudere il Blocco note e quindi chiudere l'applicazione **PeopleTrax**.  
  
12. Arrestare il profiler. Digitare il comando seguente:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Digitare il comando seguente per reimpostare le variabili di ambiente:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Usare lo strumento VSPerfReport per generare file di report con valori delimitati da virgole (CSV). Tipo:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     È possibile analizzare i report generati in un programma di foglio di calcolo oppure usare l'IDE di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per analizzare i dati di profilatura nel file Report.vsp. Per altre informazioni, vedere [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)   
 [Performance Report Views](../profiling/performance-report-views.md)(Visualizzazioni dei rapporti di prestazioni)
