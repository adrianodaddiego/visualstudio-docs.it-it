---
title: L'accesso ai Buffer di testo usando l'API Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661bf39e82fef5c040861bc9386dcb7f897d25cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313633"
---
# <a name="access-the-text-buffer-by-using-the-legacy-api"></a>Accedere al buffer di testo usando l'API legacy
Il testo è responsabile della gestione dei flussi di testo e salvataggio permanente dei file. Anche se il buffer può leggere o scrivere altri formati, tutte le comunicazioni normali con il buffer viene eseguita utilizzando Unicode. Nelle API legacy, il buffer di testo può usare unidimensionale o un sistema di coordinate bidimensionale per identificare le posizioni di carattere nel buffer.

## <a name="one--and-two-dimension-coordinate-systems"></a>Dimensione di uno e due sistemi di coordinate
 Una posizione delle coordinate unidimensionale è basata sulla posizione di un carattere dal primo carattere nel buffer, ad esempio 147. Si utilizza il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaccia per accedere a una posizione nel buffer unidimensionale. Un sistema di coordinate bidimensionale si basa sulla coppia di riga e indice. Ad esempio, un carattere nel buffer da 43, 5 sarebbe nella riga 43, cinque caratteri a destra del primo carattere nella riga. Si accede a una posizione nel buffer tramite bidimensionale il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaccia. Sia la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfacce vengono implementate dall'oggetto del buffer di testo (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) e sono accessibili tra loro usando `QueryInterface`. Il diagramma seguente illustra queste e altre interfacce principali in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

 ![Oggetto TextBuffer](../extensibility/media/vstextbuffer.gif "oggetto vsTextBuffer") oggetto del buffer di testo

 Anche se uno dei due sistemi di coordinate funziona nel buffer di testo, è ottimizzato per utilizzare le coordinate bidimensionali. Un sistema di coordinate unidimensionale è possibile creare un overhead delle prestazioni. Pertanto, utilizzare il sistema di coordinate bidimensionale laddove possibile.

 Il responsabilità di secondo del buffer di testo è salvataggio permanente dei file. A tale scopo, l'oggetto del buffer di testo implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e agisce come il componente di oggetti dati documenti per gli elementi del progetto e altri componenti dell'ambiente coinvolte nella persistenza. Per altre informazioni, vedere [di apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md).

## <a name="in-this-section"></a>Contenuto della sezione
- [Modificare le impostazioni di visualizzazione tramite l'API legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md) spiega come modificare le impostazioni di visualizzazione tramite l'API legacy.

- [Usare la gestione di testo per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md) spiega come usare la gestione di testo per monitorare le impostazioni globali.

## <a name="see-also"></a>Vedere anche
- [All'interno dell'editor di base](../extensibility/inside-the-core-editor.md)