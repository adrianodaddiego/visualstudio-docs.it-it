---
title: Modello per i pacchetti del controllo origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65f212496d152236579e63ba037fe351a4dd3370
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349214"
---
# <a name="model-for-source-control-packages"></a>Modello per i pacchetti del controllo del codice sorgente
Il modello seguente rappresenta un esempio di implementazione di un controllo di origine. Nel modello, vengono visualizzati le interfacce da implementare e i servizi di ambiente che è necessario chiamare. Come tutti i servizi, è effettivamente chiamare i metodi di una determinata interfaccia che è possibile ottenere tramite il servizio. I nomi delle classi vengono identificati per renderne più semplice visualizzare come controllo del codice sorgente viene eseguito.

 ![Controllo del codice sorgente&#95;esempi di SCRIP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") progetto di controllo sorgente di esempio

## <a name="interfaces"></a>Interfacce
 È possibile implementare il codice sorgente per i nuovi tipi di progetto in Visual Studio usando l'elenco delle interfacce illustrato nella tabella seguente.

|Interfaccia|Usa|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chiamato dai progetti e gli editor prima che di salvataggio o i file di modifica (modificato). Questa interfaccia è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servizio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chiamato dai progetti per richiedere l'autorizzazione per aggiungere, rimuovere o rinominare un file o directory. Questa interfaccia viene anche chiamata dai progetti per informare l'ambiente quando un'operazione di aggiunta approvati, rimuovere o rinominare l'azione è stata completata. È possibile accedervi usando il <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> servizio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementata da qualsiasi entità che esegue la registrazione per ricevere una notifica quando i progetti aggiungono, rinominano o rimuovere un file o directory. Per registrare la notifica dell'evento, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Chiamato dai progetti per registrare con il pacchetto del controllo codice sorgente e per ottenere informazioni sullo stato del controllo origine. Questa interfaccia è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servizio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementata dal progetto di rispondere alle richieste di controllo di origine per informazioni sui file e per ottenere le impostazioni di controllo richiesto per il file di progetto di origine.|

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)