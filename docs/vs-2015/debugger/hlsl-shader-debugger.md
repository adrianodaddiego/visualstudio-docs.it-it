---
title: Debugger dello Shader HLSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bef6c5a742c4bf6acc15a6326190686e46fef79b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410191"
---
# <a name="hlsl-shader-debugger"></a>Debugger dello shader HLS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debugger HLSL in Analizzatore grafica di Visual Studio Visual Studio aiuta a comprendere come opera il codice dello shader HLSL in condizioni di funzionamento reali dell'app.  
  
 Questo è il debugger HLSL:  
  
 ![Debug di HLSL usando Guarda e finestre stack di chiamate. ](../debugger/media/gfx-diag-demo-hlsl-debugger-orientation.png "gfx_diag_demo_hlsl_debugger_orientation")  
  
## <a name="understanding-the-hlsl-debugger"></a>Informazioni sul debugger HLSL  
 Il debugger HLSL consente di individuare i problemi che sorgono nel codice dello shader. L'esecuzione del debug del codice HLSL in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è analogo al debug del codice scritto in altri linguaggi (ad esempio, C++, C# o Visual Basic). È possibile controllare il contenuto delle variabili, impostare punti di interruzione, eseguire il codice istruzione per istruzione e risalire nello stack di chiamate, proprio come quando si esegue il debug di altri linguaggi.  
  
 Tuttavia, poiché le GPU raggiungono prestazioni elevate eseguendo il codice dello shader in centinaia di thread contemporaneamente, il debugger HLSL è progettato per interagire con gli altri strumenti dello strumento Analizzatore grafica per presentare tutte queste informazioni con un certo criterio. Analizzatore grafica ricrea i frame acquisiti tramite le informazioni registrate in un log di grafica; il debugger HLSL non monitora l'esecuzione delle GPU in tempo reale mentre esegue il codice dello shader. Poiché un log di grafica contiene informazioni sufficienti per ricreare una parte dell'output e poiché la Analizzatore grafica fornisce strumenti che consentono di individuare il pixel e l'evento esatto in cui si è verificato un errore, il debugger HLSL deve solo simulare il thread dello shader interessato. Ciò significa che il lavoro dello shader può essere simulato nella CPU, dove i meccanismi interni sono in visualizzazione completa. Questa operazione consente al debugger HLSL di operare in modo simile alla CPU.  
  
 Tuttavia, il debugger HLSL attualmente è limitato nei modi seguenti:  
  
- Il debugger HLSL non supporta la funzionalità Modifica e continuazione, ma è possibile modificare lo shader e quindi rigenerare il frame per visualizzare i risultati.  
  
- Non è possibile eseguire il debug di un'app e del codice dello shader contemporaneamente. Tuttavia, è possibile alternarli.  
  
- È possibile aggiungere variabili e registri alla finestra Espressioni di controllo, ma le espressioni non sono supportate.  
  
  Tuttavia, il debugger HLSL fornisce un'esperienza di debug più simile a quella di tipo CPU rispetto a quanto sarebbe altrimenti possibile.  
  
## <a name="hlsl-shader-edit--apply"></a>Funzionalità Modifica e applicazione Shader HLSL  
 Il debugger dello shader HLSL non supporta la funzionalità Modifica e continuazione nello stesso modo del debugger CPU perché il modello di esecuzione delle GPU non consente l'annullamento dello stato dello shader. Il debugger HLSL supporta invece la funzionalità Modifica e applicazione, che consente di modificare i file di origine HLSL e quindi di scegliere **Applica** per rigenerare il frame per vedere l'effetto delle modifiche. Il codice modificato dello shader è archiviato in un file separato per mantenere l'integrità dei file di origine HLSL originale del progetto, ma quando si è soddisfatti con le modifiche è possibile scegliere **copiare in...** Per copiare le modifiche nel progetto. Con questa funzionalità è possibile scorrere rapidamente il codice dello shader contenente gli errori ed eliminare i passaggi di ricompilazione e acquisizione che comportano un grande consumo di risorse dal flusso di lavoro del debug HLSL.  
  
## <a name="hlsl-disassembly"></a>Disassembly HLSL  
 Il debugger dello shader HLSL fornisce un elenco di assembly dello shader HLSL a destra dell'elenco del codice sorgente HLSL.  
  
## <a name="debugging-hlsl-code"></a>Debug del codice HLSL  
 È possibile accedere al debugger HLSL dalle finestre Fasi pipeline grafica o Cronologia pixel grafica.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>Per avviare il debugger HLSL dalla finestra Fasi pipeline grafica  
  
1. Nella finestra **Fasi pipeline grafica** individuare la fase della pipeline associata allo shader di cui eseguire il debug.  
  
2. Sotto il titolo della fase della pipeline scegliere **Avvia debug**, visualizzato con una piccola freccia verde.  
  
    > [!NOTE]
    > Questo punto di ingresso nel debugger HLSL esegue il debug solo del primo thread dello shader per la fase corrispondente, ovvero il primo vertice o pixel elaborato. È possibile usare Cronologia pixel grafica per accedere ad altri thread di queste fasi dello shader.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>Per avviare il debugger HLSL dalla finestra Cronologia pixel grafica  
  
1. Nella finestra **Cronologia pixel grafica** espandere la chiamata di disegno associata allo shader di cui eseguire il debug. Ogni chiamata di disegno può corrispondere a più primitive.  
  
2. Nei dettagli della chiamata di disegno espandere una primitiva il cui contributo di colore risultante indichi un bug nel codice dello shader. Se più primitive indicano un bug, scegliere la prima, onde evitare un accumulo di errori che potrebbe complicare la diagnosi del problema.  
  
3. Nei dettagli della primitiva scegliere se eseguire il debug di **Vertex Shader** o **Pixel Shader**. Eseguire il debug del vertex shader se si sospetta che il pixel shader sia corretto, ma generi un contributo di colore errato poiché il vertex shader passa costanti errate. In caso contrario, eseguire il debug del pixel shader.  
  
    A destra dello shader desiderato scegliere **Avvia debug**, visualizzato con una piccola freccia verde.  
  
   > [!NOTE]
   > Questo punto di ingresso nel debugger HLSL esegue il debug del thread del pixel shader che corrisponde alla chiamata di disegno, alla primitiva e al pixel desiderati oppure dei thread del vertex shader i cui risultati sono interpolati dalla chiamata di disegno, dalla primitiva e dal pixel desiderato. Nel caso dei vertex shader, è possibile migliorare ulteriormente il punto di ingresso in un vertice specifico espandendo i dettagli del vertex shader.  
  
   Per esempi su come usare il Debugger HLSL per eseguire il debug degli errori dello shader, vedere [esempi](../debugger/graphics-diagnostics-examples.md) o le procedure dettagliate un collegamento nella sezione Vedere anche.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Oggetti mancanti a causa dello sfondo Vertex](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Procedura dettagliata: Debug degli errori di rendering dovuti allo sfondo](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)   
 [Procedura dettagliata: Uso della diagnostica della grafica per eseguire il debug di un compute shader](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)
