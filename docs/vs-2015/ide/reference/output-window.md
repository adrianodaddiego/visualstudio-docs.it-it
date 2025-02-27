---
title: Finestra Output | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7173abd87a9e7345e7d7caee02d2bb333f507514
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696065"
---
# <a name="output-window"></a>Finestra di output
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nella finestra **Output** è possibile che vengano visualizzati messaggi di stato per diverse funzionalità dell'ambiente di sviluppo integrato (IDE, Integrated Development Environment). Per aprire la finestra **Output**, nella barra dei menu scegliere **Visualizza/Output** oppure premere CTRL+ALT+O.  
  
> [!WARNING]
> La finestra di output non viene visualizzata nel menu nelle edizioni di Visual Studio Express. Per visualizzarla, utilizzare il tasto di scelta CTRL + ALT + O.  
  
## <a name="toolbar"></a>ToolBar  
 **Mostra output di**  
 Visualizza uno o più riquadri di output da visualizzare. Potrebbero essere disponibili diversi riquadri di informazioni, a seconda dello strumento dell'IDE da cui è stata usata la finestra **Output** per recapitare messaggi all'utente.  
  
 **Trova messaggio nel codice**  
 Sposta il punto di inserimento nell'editor di codice nella riga che contiene l'errore di compilazione selezionato.  
  
 **Vai al messaggio precedente**  
 Consente di spostare l'attivazione nella finestra **Output** all'errore di compilazione precedente e di spostare il punto di inserimento nell'editor di codice alla riga che contiene l'errore di compilazione.  
  
 **Vai al messaggio successivo**  
 Consente di spostare l'attivazione nella finestra **Output** all'errore di compilazione successivo e di spostare il punto di inserimento nell'editor di codice alla riga che contiene l'errore di compilazione.  
  
 **Cancella tutto**  
 Cancella tutto il testo dal riquadro **Output**.  
  
 **Attiva/Disattiva a capo automatico**  
 Attiva e disattiva la funzione A capo automatico nel riquadro **Output**. Quando la funzione A capo automatico è attiva, il testo contenuto in voci particolarmente lunghe che si estende oltre l'area di visualizzazione verrà visualizzato nella riga successiva.  
  
## <a name="output-pane"></a>Riquadro Output  
 Nel riquadro **Output** selezionato nell'elenco **Mostra output di** viene visualizzato l'output dell'origine indicata.  
  
## <a name="routing-messages-to-the-output-window"></a>Routing dei messaggi alla finestra di output  
 Per visualizzare la finestra **Output** ogni volta che si compila un progetto, nella finestra di dialogo **Generale, Progetti e soluzioni, Opzioni** selezionare **Mostra finestra di output a inizio compilazione**. Quindi, con un file di codice aperto per la modifica, scegliere i pulsanti **Vai al messaggio successivo** e **Vai al messaggio precedente** nella barra degli strumenti della finestra **Output** per selezionare le voci nel riquadro **Output**. Durante l'operazione, il punto di inserimento nell'editor di codice passa alla riga di codice in cui si è verificato il problema selezionato.  
  
 Alcuni comandi e funzionalità dell'IDE richiamati nella [finestra di comando](../../ide/reference/command-window.md) recapitano l'output nella finestra **Output**. L'output di strumenti esterni, quali file con estensione bat e com, in genere visualizzato nella finestra del prompt dei comandi, viene indirizzato a un riquadro **Output** quando si seleziona l'opzione **Usa finestra di output** (vedere [Gestione di strumenti esterni](../../ide/managing-external-tools.md)). Nei riquadri **Output** possono essere visualizzati anche molti altri tipi di messaggi. Ad esempio, quando la sintassi Transact-SQL in una stored procedure viene controllata in base a un database di destinazione, i risultati vengono visualizzati nella finestra **Output**.  
  
 È anche possibile programmare applicazioni personalizzate per scrivere messaggi di diagnostica in fase di esecuzione in un riquadro **Output**. A tale scopo, usare i membri della classe <xref:System.Diagnostics.Debug> o <xref:System.Diagnostics.Trace> nello spazio dei nomi <xref:System.Diagnostics> nella libreria di classi .NET Framework. I membri della classe <xref:System.Diagnostics.Debug> visualizzano l'output quando si compilano configurazioni di debug della soluzione o del progetto, mentre i membri della classe <xref:System.Diagnostics.Trace> visualizzano l'output quando si compilano configurazioni di debug o di rilascio. Per altre informazioni, vedere [Messaggi diagnostici nella finestra di output](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 In [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]  è possibile creare istruzioni ed eventi di compilazione personalizzati i cui avvisi ed errori vengono visualizzati e conteggiati nel riquadro **Output**. Premendo F1 su una riga di output, è possibile visualizzare un argomento della Guida appropriato. Per altre informazioni, vedere [Formattazione dell'output di un'istruzione di compilazione personalizzata o un evento di compilazione](https://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da).  
  
## <a name="scrolling-behavior"></a>Comportamento dello scorrimento  
 Se si usa lo scorrimento automatico nella finestra Output e quindi si naviga usando il mouse o i tasti di direzione, lo scorrimento automatico viene interrotto. Per riprendere lo scorrimento automatico, premere CTRL+FINE.  
  
## <a name="see-also"></a>Vedere anche  
 [Messaggi diagnostici nella finestra di output](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Procedura: Controllare la finestra di Output](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858)   
 [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md)  (Compilazione e creazione)  
 [Understanding Build Configurations](../../ide/understanding-build-configurations.md)  (Informazioni sulle configurazioni delle compilazioni)  
 [Panoramica della libreria di classi](https://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157)
