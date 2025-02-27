---
title: L'accesso a theText visualizzazione tramite l'API Legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954617"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>L'accesso a theText visualizzazione tramite l'API Legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una visualizzazione di testo è una presentazione del testo archiviato in un buffer di testo. È possibile accedere alla visualizzazione di testo con l'API legacy, come illustrato nella sezione seguente.  
  
## <a name="text-view-object"></a>Oggetto visualizzazione di testo  
 Ogni visualizzazione è associato un proprio buffer di testo e la visualizzazione è una finestra sui dati nel buffer. Il diagramma seguente mostra le interfacce principali dell'oggetto di visualizzazione del testo, che è rappresentato dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Visualizzazione oggetto testo di Visual Studio](../extensibility/media/vstextview.gif "oggetto vstextview")  
Oggetto visualizzazione di testo  
  
 La vista è un modo per presentare il testo nel buffer. Include funzionalità quali ritorno a capo automatico e la modalità struttura, in modo che ciò che viene visualizzato nella vista non è una rappresentazione esatta del testo nel buffer.  
  
 Una vista consente di altri servizi o processi per intercettare i comandi in ingresso e agire su di esse prima della visualizzazione interviene su di essi. Il servizio più comune per eseguire questa operazione è un servizio di linguaggio. Un servizio di linguaggio potrebbe essere necessario, ad esempio, di intercettare il comando per il tasto INVIO fornire suggerimenti di comportamento o lo strumento rientri personalizzati.  
  
## <a name="adding-functionality-to-the-text-view"></a>Aggiunta di funzionalità per la visualizzazione di testo  
 È possibile personalizzare il comportamento di visualizzazione di testo mediante la gestione di specifiche combinazioni di tasti. Per intercettare le pressioni di tasti, si implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> sull'oggetto e fornire una destinazione comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) per monitorare e intercetta comandi.  
  
 La visualizzazione di testo utilizza architettura sequenziale per i filtri di comando. Nuovi filtri di comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetti) vengono aggiunte alla sequenza chiamando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (metodo).  
  
 Notifica degli eventi per la visualizzazione di testo viene fornita tramite il `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interfaccia. Implementare questa interfaccia sull'oggetto client di ricevere notifica delle modifiche apportate alla visualizzazione di testo. Esporre questa interfaccia per la visualizzazione di testo usando il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaccia nella visualizzazione di testo per ricevere notifica delle modifiche apportate dalla vista.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica delle impostazioni di visualizzazione tramite l'API Legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Uso della gestione testi per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
