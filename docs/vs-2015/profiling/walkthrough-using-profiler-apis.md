---
title: 'Procedura dettagliata: Uso delle API del profiler | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bcb7be3e2db3d8a48f03d971e104f1e64e1153c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435667"
---
# <a name="walkthrough-using-profiler-apis"></a>Procedura dettagliata: Usando le API di Profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella procedura dettagliata viene usata un'applicazione C# per illustrare l'uso delle API di Strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le API del profiler consentono di limitare la quantità di dati raccolti durante la profilatura della strumentazione.  
  
 In genere i passaggi descritti in questa procedura dettagliata si applicano a un'applicazione C/C++. Per ogni linguaggio, è necessario configurare l'ambiente di compilazione in modo appropriato.  
  
 Si inizia generalmente usando la profilatura campione per analizzare le prestazioni dell'applicazione. Se la profilatura campione non restituisce informazioni che indicano un collo di bottiglia, è possibile che la profilatura della strumentazione offra un livello di dettaglio maggiore. La profilatura della strumentazione è molto utile per esaminare l'interazione tra thread.  
  
 Per un livello di dettaglio maggiore è tuttavia necessario raccogliere più dati. È possibile quindi che la profilatura della strumentazione crei file di dati di grandi dimensioni. È anche possibile che la strumentazione comprometta le prestazioni dell'applicazione. Per altre informazioni, vedere [Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md) e [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)  
  
 Il profiler di Visual Studio consente di limitare la raccolta dei dati. Questa procedura dettagliata offre un esempio su come limitare la raccolta dei dati usando le API del profiler. Il profiler di Visual Studio offre un'API per il controllo della raccolta dei dati all'interno di un'applicazione.  
  
 Per il codice nativo, le API del profiler di Visual Studio API si trovano in VSPerf.dll. Il file di intestazione VSPerf.h e la libreria di importazione VSPerf.lib si trovano nella directory Microsoft Visual Studio 9\Team Tools\Strumenti per le prestazioni.  
  
 Per il codice gestito, le API del profiler si trovano in Microsoft.VisualStudio.Profiler.dll. Questa DLL è disponibile nella directory Microsoft Visual Studio 9\Team Tools\Strumenti per le prestazioni. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Profiler>.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questa procedura dettagliata presuppone che l'ambiente di sviluppo scelto sia configurato per supportare il debug e il campionamento. Gli argomenti seguenti offrono una panoramica di questi prerequisiti:  
  
 [Procedura: Scegliere i metodi di raccolta](../profiling/how-to-choose-collection-methods.md)  
  
 [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Per impostazione predefinita, quando viene avviato, il profiler raccoglie i dati a livello globale. Il codice seguente all'inizio del programma disabilita la profilatura globale.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 È possibile disabilitare la raccolta dei dati nella riga di comando senza usare una chiamata API. Questa procedura presuppone che l'ambiente di compilazione avviata tramite riga di comando sia configurato per eseguire gli strumenti di profilatura e come strumenti di sviluppo. Include le impostazioni necessarie per VSInstr e VSPerfCmd. Vedere gli strumenti di profilatura della riga di comando.  
  
## <a name="limiting-data-collection-using-profiler-apis"></a>Limitazione della raccolta dei dati usando le API del profiler  
  
#### <a name="to-create-the-code-to-profile"></a>Per creare il codice per il profilo  
  
1. Creare un nuovo progetto C# in Visual Studio o usare una compilazione avviata tramite riga di comando, a seconda delle preferenze.  
  
    > [!NOTE]
    > La compilazione deve fare riferimento alla libreria Microsoft.VisualStudio.Profiler.dll che si trova nella directory Microsoft Visual Studio 9\Team Tools\Strumenti per le prestazioni.  
  
2. Copiare il codice riportato di seguito e incollarlo nel progetto:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Per raccogliere e visualizzare i dati nell'IDE di Visual Studio  
  
1. Aprire l'IDE di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Nel menu **Analizza** scegliere **Profiler** e selezionare **Nuova sessione di prestazioni**.  
  
2. Aggiungere il file binario compilato per l'elenco **Destinazioni** nella finestra **Esplora prestazioni**. Fare clic con il pulsante destro del mouse su **Destinazioni** e selezionare **Aggiungi binario di destinazione**. Nella finestra di dialogo **Aggiungi binario di destinazione** selezionare il file binario e fare clic su **Apri**.  
  
3. Nell'elenco **Metodo** della barra degli strumenti **Esplora prestazioni** fare clic su **Strumentazione**.  
  
4. Fare clic su **Avvio con analisi**.  
  
    Il profiler instrumenterà ed eseguirà il file binario e creerà un file del report di prestazioni. Il file del report di prestazioni verrà visualizzato nel nodo **Report** di **Esplora prestazioni**.  
  
5. Aprire il file del report di prestazioni ottenuto.  
  
   Per impostazione predefinita, quando viene avviato, il profiler raccoglie i dati a livello globale. Il codice seguente all'inizio del programma disabilita la profilatura globale.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>Per raccogliere e visualizzare i dati nella riga di comando  
  
1. Compilare una versione di debug del codice di esempio creato nella procedura dettagliata illustrata in precedenza per la creazione di codice per il profilo.  
  
2. Per profilare un'applicazione gestita, digitare il comando seguente e impostare le variabili di ambiente appropriate:  
  
     **VsPefCLREnv /traceon**  
  
3. Digitare il comando seguente:**VSInstr \<filename>.exe**  
  
4. Digitare il comando seguente: **VSPerfCmd /start:trace /output:\<filename>.vsp**  
  
5. Digitare il comando seguente:**VSPerfCmd /globaloff**  
  
6. Uscire dal programma.  
  
7. Digitare il comando seguente:**VSPerfCmd /shutdown**  
  
8. Digitare il comando seguente: **VSPerfReport /calltrace:\<filename>.vsp**  
  
     Viene creato un file con estensione csv nella directory corrente con i dati sulle prestazioni risultanti.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Riferimenti per le API del profiler di Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Introduzione](../profiling/getting-started-with-performance-tools.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
