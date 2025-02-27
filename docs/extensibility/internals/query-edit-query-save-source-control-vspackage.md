---
title: Query Edit Query Save (VSPackage di controllo codice sorgente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3bffdac79a9f4274fbd6465c33e8659caf9d1f6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341456"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Query Edit Query Save (VSPackage di controllo del codice sorgente)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gli editor possono trasmettere gli eventi di Query Edit Query salvare (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Stub di controllo di origine implementa il servizio QEQS, in modo che sia il destinatario di eventi QEQS. Questi eventi vengono poi delegati a VSPackage di controllo del codice sorgente attualmente attivo. Il controllo del codice sorgente attivo pacchetto VSPackage implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e i relativi metodi. I metodi del `IVsQueryEditQuerySave2` interfaccia vengono in genere chiamato immediatamente prima che il documento viene modificato per la prima volta e immediatamente prima del salvataggio di un documento.

## <a name="queryeditquerysave-events"></a>QueryEditQuerySave Events
 Il controllo del codice sorgente VSPackage deve gestire gli eventi QEQS implementando il `IVsQueryEditQuerySave2` interfaccia e i metodi necessari. Di seguito è una breve descrizione dei due metodi che il pacchetto VSPackage deve implementare almeno. L'implementazione effettiva deve essere in base alla logica di controllo del modello di origine.

### <a name="queryeditfiles-method"></a>Metodo QueryEditFiles
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> viene chiamato quando un editor o un progetto desidera modificare un file. In teoria, questo metodo viene chiamato *prima di* il file viene modificato e quando viene salvato un file. Quando viene richiamato, il `IVsQueryEditQuerySave2::QueryEditFiles` metodo controlla se i file specificati sono disponibili in controllo del codice sorgente, se è necessario per l'estrazione e se può essere ricaricati. Se circostanze impediscono i file modificabili, le `IVsQueryEditQuerySave2::QueryEditFiles` metodo indica al programma chiama per annullare la modifica. È anche possibile che il chiamante di specificare una modalità di chiamata. In modalità "invisibile", questo metodo accetta azione solo se non comporta alcuna interfaccia utente venga visualizzato. Se è inevitabile dell'interfaccia utente, è necessario che venga restituito un flag per indicare il problema.

 Il metodo si comporta in modo transazionale. vale a dire, se la modifica viene annullata in un singolo file, la modifica è stata annullata per tutti i file. Viceversa, se è consentita la modifica, è consentito per tutti i file. Se questo metodo consente la modifica di una sola volta per un determinato set di file, è necessario consentire sempre la modifica per le chiamate successive per lo stesso set di file. Consenti modifica ciclo continua fino a quando i file vengono chiusi, salvati e ricaricati; finché non cambiano; i relativi attributi (proprietà) o fino a quando non viene modificato il pacchetto del controllo codice sorgente. Casi da considerare quando si implementa il `IVsQueryEditQuerySave2::QueryEditFiles` metodo includono più file, file speciali, annullare dall'utente e le modifiche in memoria.

### <a name="querysavefiles-method"></a>Metodo QuerySaveFiles
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> viene chiamato quando un editor o il progetto deve salvare un set di file. Quando viene richiamato, il `IVsQueryEditQuerySave2::QuerySaveFiles` metodo controlla se i file specificati sono di sola lettura e che sono sotto controllo del codice sorgente. Se i file devono essere estratti, la chiamata viene delegata al pacchetto del controllo origine. Se circostanze impediscono che i file di salvataggio, il `IVsQueryEditQuerySave2::QuerySaveFiles` metodo deve indicare all'editor per annullare il salvataggio. Come con la `IVsQueryEditQuerySave2::QueryEditFiles` metodo, è possibile che il chiamante di specificare una modalità di chiamata. In modalità "invisibile", questo metodo accetta azione solo se non comporta alcuna interfaccia utente venga visualizzato. Se è inevitabile dell'interfaccia utente, è necessario che venga restituito un flag per indicare il problema.

 Questo metodo deve comportarsi in modo transazionale. vale a dire, se il salvataggio viene annullato in un singolo file, il salvataggio è stato annullato per tutti i file. Viceversa, se è consentito il salvataggio, deve essere abilitato per tutti i file. Come con le `IVsQueryEditQuerySave2::QueryEditFiles` metodo, casi da considerare quando si implementa il `IVsQueryEditQuerySave2::QuerySaveFiles` metodo includono più file, file speciali, annullare dall'utente e le modifiche in memoria.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>