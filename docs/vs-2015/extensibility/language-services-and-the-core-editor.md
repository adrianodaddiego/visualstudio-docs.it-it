---
title: Servizi di linguaggio e l'Editor principale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954976"
---
# <a name="language-services-and-the-core-editor"></a>Servizi di linguaggio e l'Editor principale di
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor di Visual Studio sono spesso associati a un servizio di linguaggio. Tra le altre cose, un servizio di linguaggio fornisce la colorazione della sintassi, completamento delle istruzioni, IntelliSense e la formattazione del testo.  
  
## <a name="core-editors-and-document-data-objects"></a>Editor principale e oggetti dati documenti  
 Quando si accede l'editor principale, non è creare i dati del documento e gli oggetti di visualizzazione documento. L'IDE crea e ne controlla questi due oggetti e si ottengono handle per loro, rendendo le chiamate appropriate nell'editor di implementazione della factory.  
  
 Per altre informazioni, vedere [determinare quale Editor viene aperto un File in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Servizi di linguaggio e l'Editor principale di  
 Implementando un servizio di linguaggio, è possibile controllare la modalità di visualizzazione dei dati nella visualizzazione dei documenti. Un servizio di linguaggio fornisce informazioni e il comportamento specifico per una determinata lingua, ad esempio Visual C++. Quando si crea un buffer di testo e determinare l'estensione per il documento che si sta aprendo, buffer di testo determina il servizio di linguaggio associato a questa estensione del nome file da una chiave del Registro di sistema, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors \\\Extensions {YourLanguageService GUID}. Il pacchetto VSPackage standard caricamento procedure quindi carica il pacchetto VSPackage e viene creata un'istanza del servizio di linguaggio.  
  
 Nella figura seguente viene illustrato un servizio di linguaggio di base.  
  
 ![Rappresentazione grafica del modello di servizio di linguaggio](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Oggetti principali editor e linguaggio di servizio  
  
 Oggetto dati del documento per l'editor principale viene chiamato un buffer di testo ed è rappresentato dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto. Oggetto visualizzazione del documento viene chiamato una visualizzazione di testo ed è rappresentato dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> oggetto. Questi due oggetti interagiscono tramite il servizio di linguaggio per fornire una visualizzazione unificata dell'editor principale. Le informazioni dal buffer di testo e la vista visualizzi il testo in una finestra del documento denominato una finestra del codice. Il documento di finestra di codice è gestito da un gestore di finestra di codice.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Fornire un contesto del servizio linguaggio con l'API Legacy](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hosting di IntelliSense](../extensibility/intellisense-hosting.md)   
 [Linguaggi contenuti](../extensibility/contained-languages.md)   
 [Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)
