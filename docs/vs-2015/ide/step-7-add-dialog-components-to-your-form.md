---
title: 'Passaggio 7: Aggiungere i componenti di finestra di dialogo al Form | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 54d2b83fab24aa3c9deabc979782d9b82ea5c482
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442479"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per consentire al programma di aprire i file di immagine e scegliere un colore di sfondo, in questo passaggio si aggiunge un componente **OpenFileDialog** e un componente **ColorDialog** al form.  
  
 Un componente è per alcuni aspetti simile a un controllo. Si usa la Casella degli strumenti per aggiungere un componente al form e si impostano le relative proprietà usando la finestra **Proprietà**. A differenza di un controllo, tuttavia, l'aggiunta di un componente al form non aggiunge un elemento visibile da parte dell'utente sul form. Vengono invece forniti determinati comportamenti che è possibile attivare tramite codice. L'apertura della finestra di dialogo **Apri file** viene eseguita da un componente.  
  
 ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo")per una versione video di questo argomento, vedere [esercitazione 1: Creare un Visualizzatore immagini in Visual Basic - Video 3](http://go.microsoft.com/fwlink/?LinkId=205213) o [esercitazione 1: Creare un Visualizzatore immagini in C# -Video 3](http://go.microsoft.com/fwlink/?LinkId=205202). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.  
  
### <a name="to-add-dialog-components-to-your-form"></a>Per aggiungere componenti di finestra di dialogo al form  
  
1. Scegliere Progettazione Windows Form (Form1.cs [Design] o Form1.vb [Design]) e aprire il gruppo **Finestre di dialogo** nella casella degli strumenti.  
  
    > [!NOTE]
    > Il gruppo **Finestre di dialogo** nella Casella degli strumenti ha componenti che aprono molte finestre di dialogo utili che possono essere usate per l'apertura e il salvataggio di file, l'esplorazione di cartelle e la scelta di tipi di carattere e colori. In questo progetto si usano due componenti di finestra di dialogo: **OpenFileDialog** e **ColorDialog**.  
  
2. Per aggiungere un componente denominato **openFileDialog1** al form, fare doppio clic su **OpenFileDialog**. Per aggiungere un componente denominato **colorDialog1** al form, fare doppio clic su **ColorDialog** nella Casella degli strumenti. Si utilizzerà tale componente nell'esercitazione successiva. Viene visualizzata un'area nella parte inferiore di Progettazione Windows Form (sotto al form Visualizzatore immagini) che dispone di un'icona per ognuno dei due componenti di finestra di dialogo aggiunti, come mostrato nell'immagine seguente.  
  
     ![Componenti della finestra di dialogo](../ide/media/express-dialogsadded.png "Express_DialogsAdded")  
Componenti delle finestre di dialogo  
  
3. Scegliere l'icona **openFileDialog1** nell'area nella parte inferiore di Progettazione Windows Form. Impostare due proprietà:  
  
    - Impostare la proprietà **Filtro** nel seguente modo (è possibile copiare e incollare quanto segue):  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    - Impostare la proprietà **Titolo** sul testo seguente: **Selezionare un file di immagine**  
  
         Le impostazioni della proprietà **Filtro** consentono di specificare i tipi di file visualizzati nella finestra di dialogo relativa alla **selezione di un file immagine**.  
  
    > [!NOTE]
    > Per vedere un esempio della finestra di dialogo **Apri file** in un'applicazione diversa, aprire il Blocco note o Paint sulla barra dei menu e scegliere **Apri** dal menu **File**. Si noti la presenza dell'elenco a discesa **Tipo file** in fondo. È stata usata la proprietà **Filtro** del componente **OpenFileDialog** per configurarlo. Si noti anche la formattazione in grassetto delle proprietà**Titolo** e **Filtro** nella finestra **Proprietà**. L'IDE imposta tale formattazione per evidenziare le proprietà che sono state modificate rispetto ai valori predefiniti.  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 8: Scrivere codice per mostrare un gestore eventi del pulsante immagine](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: Assegnare un nome ai pulsanti](../ide/step-6-name-your-button-controls.md).
