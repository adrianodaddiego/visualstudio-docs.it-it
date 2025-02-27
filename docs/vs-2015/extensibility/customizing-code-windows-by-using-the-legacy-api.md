---
title: Personalizzazione di Windows di codice usando l'API Legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62556133"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personalizzazione di Windows di codice usando l'API Legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una finestra del codice è un oggetto finestra di documento che supporta uno o più visualizzazioni di testo. Esattamente le stesse funzionalità di una finestra del codice dipendono dal servizio di linguaggio associato. In modalità interfaccia a documenti multipli (MDI), la finestra del codice è la cornice figlio MDI.  
  
 Finestre del codice sono controllate da servizi di linguaggio e ogni servizio di linguaggio può fornire un proprio gestore di finestra di codice. In questo modo il servizio di linguaggio aggiungere le proprie aree di controllo alla finestra del codice, ad esempio linee a zigzag, la colorazione e altro ancora. Per altre informazioni su come creare una finestra di core, vedere [creazione di un'istanza di Core Editor tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Una finestra del codice è un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto con una visualizzazione di testo e tutte le aree di controllo ospitati nell'oggetto. Quando si crea la finestra del codice durante la creazione di un'istanza di una core editor, il servizio di linguaggio è possibile collegare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> alla finestra del codice, come è illustrato nella figura seguente.  
  
 ![Immagine di CodeWindow](../extensibility/media/vscodewindow.gif "oggetto vscodewindow")  
Finestra del codice  
  
 Il servizio di linguaggio implementa la gestione di finestre di codice ed è responsabile della gestione delle aree di controllo, ad esempio una barra di riepilogo a discesa. La finestra di codice chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metodo durante l'inizializzazione finestra del codice. Quando viene effettuata la chiamata, il servizio di linguaggio è possibile aggiungere una barra di riepilogo a discesa o una barra dei pulsanti (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) alla finestra del codice.  
  
## <a name="in-this-section"></a>In questa sezione  
 `Customizing Code Windows by Using the Legacy API`  
 Viene illustrato come personalizzare le finestre di codice usando l'API legacy.  
  
 [Procedura: Ospitare un Editor in un altro Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Viene illustrato come ospitare un editor secondo all'interno di una finestra dell'editor.  
  
 [Procedura: Generare gli eventi quando l'Editor perde lo stato attivo](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Spiega come collegare una visualizzazione del documento a un oggetto dati del documento.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Creare un'istanza di Editor principale con l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Accesso alla visualizzazione testo tramite l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
