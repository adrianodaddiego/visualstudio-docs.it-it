---
title: Linee guida di controllo di origine aggiuntivi per i progetti ed editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9c04623ed276bf10784ccdf895c5abb1c6e9903
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315863"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Linee guida di controllo di origine aggiuntivi per i progetti ed editor
Esistono una serie di linee guida che progetti ed editor deve rispettare per supportare il controllo del codice sorgente.

## <a name="guidelines"></a>Indicazioni
 Il progetto o l'editor deve anche eseguire le operazioni seguenti per il supporto di controllo del codice sorgente:

|Area|Progetto|Editor|Dettagli|
|----------|-------------|------------|-------------|
|Copia privata dei file|x||L'ambiente supporta private copie dei file. Vale a dire, ogni persona integrata nel progetto ha il proprio copia privata dei file in tale progetto.|
|Persistenza di ANSI o Unicode|x|x|Se si scrive il codice di persistenza, rendere persistenti i file in formato ANSI poiché la maggior parte dei programmi di controllo di origine attualmente non supportano Unicode.|
|Enumerare i file|x||Il progetto deve contenere un elenco specifico di tutti i file in esso contenuti e deve essere in grado di enumerare l'elenco di file usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Il progetto deve anche esporre i nomi di elemento tramite relativi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementazione e supporto per la ricerca del nome (tra cui file speciali) tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementazione.|
|Formato di testo|x|x|Quando possibile, i file devono essere in formato testo per supportare l'unione di versioni diverse. File che non sono in formato testo non è possibile unire con altre versioni del file in un secondo momento. Il formato di testo preferito è XML.|
|In base al riferimento|x||I progetti in base al riferimento facilmente sono supportati nel controllo del codice sorgente. Tuttavia, i progetti basati su directory supportati anche dal controllo del codice sorgente, purché il progetto può produrre un elenco dei relativi file su richiesta, indipendentemente dall'esistono di tali file sul disco. Quando si apre un progetto dal controllo del codice sorgente, il file di progetto diventa inattivo prima di qualsiasi file.|
|Rendere persistenti gli oggetti e proprietà in ordine prevedibile|x|x|Rendi permanenti i file in un ordine prevedibile, ad esempio un ordine alfabetico, per facilitare l'unione.|
|Ricarica|x|x|Quando viene modificato un file su disco, l'editor deve essere in grado di ricaricarlo. Quando si partecipa controllo del codice sorgente, l'ambiente verrà ricaricare i dati per l'utente chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementazione. Il caso di ricaricamento più difficile è quando si verifica un checkpoint quando è stata chiamata IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e l'elaborazione di informazioni. Tuttavia, il codice di ricaricamento deve essere in grado di eseguire in questa situazione.<br /><br /> L'ambiente ricarica automaticamente i file di progetto. Tuttavia, è necessario implementare un progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> se l'area è nidificata gerarchie per supportare il ricaricamento di nidificare i file di progetto.|

## <a name="see-also"></a>Vedere anche
- [Supporto di controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)