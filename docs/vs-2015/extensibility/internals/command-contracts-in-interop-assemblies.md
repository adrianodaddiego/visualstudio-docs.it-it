---
title: Comando contratti negli assembly di interoperabilità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50d48d3a8ff55559cce1c3a40142e31b8eebd85f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969759"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratti dei comandi negli assembly di interoperabilità
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il contratto di base per la gestione dei comandi tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia è che l'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo per determinare se il comando è supportato e, se supportato, per determinarne lo stato e testo. Quindi, l'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per eseguire il comando.  
  
 Il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo viene gestito in modo identico per tutti i comandi. Ulteriori comunicazioni, se necessario (ad esempio, con elenchi a discesa), vengano gestita chiamando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo con i parametri appropriati. L'interpretazione di questi parametri dipende il comando specificato.  
  
 Se la destinazione del comando restituisce i valori nel parametro di output, il chiamante è sempre responsabile della liberazione tutte le risorse che sono state allocate. Poiché questo parametro è una variante, la cancellazione di variant libera le risorse.  
  
 Nei casi in cui i comandi devono operare all'interno di una finestra della gerarchia, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia deve essere usata. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia dispone di un contratto analogo con metodi simili: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementazione](../../extensibility/internals/command-implementation.md)
