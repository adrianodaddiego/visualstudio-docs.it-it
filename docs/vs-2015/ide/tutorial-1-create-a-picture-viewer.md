---
title: 'Esercitazione 1: Creare un Visualizzatore immagini | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c382ff2a16e47f52a33e5c6728f0c57d57e4315b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703058"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Esercitazione 1: Creare un Visualizzatore immagini
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa esercitazione si compila un programma che carica un'immagine da un file e la visualizza in una finestra. Viene illustrato come trascinare i controlli quali pulsanti e caselle immagine sul form, impostare le relative proprietà e utilizzare i contenitori per ridimensionare agevolmente il form. Si inizia inoltre a scrivere il codice. Vengono illustrate le seguenti procedure:  
  
- Creare un nuovo progetto.  
  
- Testare un'applicazione (eseguirne il debug).  
  
- Aggiungere controlli di base come caselle di controllo e pulsanti a un form.  
  
- Posizionare i controlli sul form utilizzando i layout.  
  
- Aggiungere le finestre di dialogo **Apri file** e **Colore** a un form.  
  
- Creare codice utilizzando IntelliSense e frammenti di codice.  
  
- Scrivere metodi per la gestione eventi.  
  
  Al termine delle varie procedure, il programma sarà simile all'immagine che segue.  
  
  ![Immagine creata in questa esercitazione](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone")  
  Immagine che si creerà in questa esercitazione  
  
  Per scaricare una versione completa di esempio, vedere [Complete Picture Viewer tutorial sample](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8) (Esempio di esercitazione per un visualizzatore immagini completo).  
  
  ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo")per una versione video di questo argomento, vedere [procedura: Creare un Visualizzatore immagini in Visual Basic? ](http://go.microsoft.com/fwlink/?LinkId=205207) o [ricerca per categorie Creare un Visualizzatore immagini in C#? ](http://go.microsoft.com/fwlink/?LinkId=205198).  
  
> [!NOTE]
> In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio. In questa esercitazione sono trattati sia Visual C# sia Visual Basic; concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.  
>   
> Per visualizzare il codice per Visual Basic, scegliere la scheda **VB** all'inizio dei blocchi di codice; per visualizzare il codice per Visual C#, scegliere la scheda **C#**. Per altre informazioni su Visual C++, vedere l'[Introduzione](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) e l'[esercitazione sul linguaggio C++](http://www.cplusplus.com/doc/tutorial/).  
>   
> Per informazioni sulla scrittura di app Visual C# o Visual Basic per Windows Store, vedere [Creare la prima app di Windows Runtime in C# o Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Per informazioni sulla creazione di app JavaScript per Windows Store, vedere [Creazione della prima app di Windows Runtime in JavaScript](https://msdn.microsoft.com/library/windows/apps/br211385.aspx).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Passaggio 1: Creare un progetto di Windows Forms Application](../ide/step-1-create-a-windows-forms-application-project.md)|Iniziare creando un progetto di applicazione Windows Forms.|  
|[Passaggio 2: Eseguire il programma](../ide/step-2-run-your-program.md)|Eseguire il programma applicativo Windows Forms creato nel passaggio precedente.|  
|[Passaggio 3: Impostare le proprietà del modulo](../ide/step-3-set-your-form-properties.md)|Modificare l'aspetto del form usando la finestra **Proprietà**.|  
|[Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Aggiungere un oggetto `TableLayoutPanel` al form.|  
|[Passaggio 5: Aggiungere controlli al modulo](../ide/step-5-add-controls-to-your-form.md)|Aggiungere controlli, ad esempio un controllo `PictureBox` e un controllo `CheckBox`, al form. Aggiungere pulsanti al form.|  
|[Passaggio 6: Assegnare un nome ai pulsanti](../ide/step-6-name-your-button-controls.md)|Rinominare i pulsanti con nomi più significativi.|  
|[Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo](../ide/step-7-add-dialog-components-to-your-form.md)|Aggiungere un componente **OpenFileDialog** e un componente **ColorDialog** al form.|  
|[Passaggio 8: Scrivere il codice per il gestore dell'evento del pulsante Mostra immagine](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Creare codice utilizzando lo strumento IntelliSense.|  
|[Passaggio 9: Esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md)|Esaminare e testare il codice. Aggiungere commenti in base alle necessità.|  
|[Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Scrivere codice per far funzionare altri pulsanti e una casella di controllo utilizzando IntelliSense.|  
|[Passaggio 11: Eseguire il programma e provare altre funzionalità](../ide/step-11-run-your-program-and-try-other-features.md)|Eseguire il programma e impostare il colore di sfondo. Provare altre funzionalità, ad esempio la modifica di colori, tipi di carattere e bordi.|
