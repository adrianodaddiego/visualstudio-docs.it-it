---
title: 'Procedura dettagliata: Personalizzazione della visualizzazione di testo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117317"
---
# <a name="walkthrough-customizing-the-text-view"></a>Procedura dettagliata: Personalizzazione della visualizzazione di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile personalizzare una visualizzazione di testo, modificando le proprietà seguenti nella mappa dell'editor-format:  
  
- Margine indicatore  
  
- Punto di inserimento  
  
- Sovrascrittura del punto di inserimento  
  
- Testo selezionato  
  
- Testo selezionato inattivo (vale a dire, selezionato testo che ha perso lo stato attivo)  
  
- Spazio vuoto visibile  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1. Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `ViewPropertyTest`.  
  
2. Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Eliminare i file di classe esistenti.  
  
## <a name="defining-the-content-type"></a>Definizione del tipo di contenuto  
  
1. Aggiungere un file di classe e assegnargli il nome `ViewPropertyModifier`.  
  
2. Aggiungere il codice seguente `using` direttive:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Dichiarare una classe denominata `TestViewCreationListener` che eredita da <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Esportare questa classe con gli attributi seguenti:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Per specificare il tipo di contenuto a cui si applica questo listener.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Per specificare il ruolo di questo listener.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. In questa classe, importare il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Modifica delle proprietà di visualizzazione  
  
1. Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che le proprietà della vista vengono modificate quando viene aperta la visualizzazione. Per apportare la modifica, trovare prima il <xref:System.Windows.ResourceDictionary> che corrisponde all'aspetto della visualizzazione da trovare. Quindi modificare la proprietà appropriata nel dizionario risorse e impostare le proprietà. Batch le chiamate per il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metodo chiamando il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metodo prima di impostare le proprietà e quindi il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> dopo aver impostato le proprietà.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
  
1. Compilare la soluzione.  
  
     Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
2. Creare un file di testo e digitare alcune parole.  
  
    - Il punto di inserimento deve essere magenta e il punto di inserimento di sovrascrittura deve essere turchese.  
  
    - Il margine indicatore (a sinistra della visualizzazione di testo) deve essere luce verde.  
  
3. Selezionare il testo che appena digitato. Il colore del testo selezionato deve essere chiaro rosa.  
  
4. Mentre il testo è selezionato, fare clic su un punto qualsiasi all'esterno dell'intervallo di testo. Il colore del testo selezionato deve essere Rosa scuro.  
  
5. Attivare lo spazio vuoto visibile. (Nelle **Edit** dal menu **avanzate** e quindi fare clic su **Mostra/Nascondi spazi**). Digitare alcune schede nel testo. Le frecce rosse rappresentano le schede devono essere visualizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
