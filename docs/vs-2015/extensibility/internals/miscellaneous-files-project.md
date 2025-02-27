---
title: Progetto file esterni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c128475ad9f5cb71b98325bbece4e524507a08b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966446"
---
# <a name="miscellaneous-files-project"></a>Progetto di file esterni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando un utente apre gli elementi del progetto, l'IDE assegna al progetto file esterni tutti gli elementi che non sono membri di tutti i progetti in una soluzione.  
  
 I progetti svolgono un ruolo significativo nel determinare quale editor da utilizzare quando un utente apre un elemento del progetto. Un progetto può essere progettato per aprire determinati file usando un editor specifico del progetto o un editor standard.  
  
 In genere, un editor specifico del progetto richiede che l'utente dispone di conoscenze specializzate o utilizzare interfacce speciale dal progetto. Per altre informazioni, vedere [Procedura: Aprire Editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Un editor standard è possibile aprire qualsiasi file con un'estensione specifica in qualsiasi progetto. L'utente può personalizzare alcuni editor standard, ad esempio il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor di testo, per i progetti ancora, mantenendo tuttavia il carattere pubblico. Editor standard vengono create utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> (metodo).  
  
 Se nessun progetto nella soluzione risponde che è possibile aprire un elemento del progetto, l'IDE fornisce un progetto speciale denominato il progetto file esterni che consente di aprire qualsiasi file.  
  
 Questo progetto speciale fornisce per l'apertura di un file all'esterno del contesto di un progetto. Durante l'elaborazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metodo, il progetto file esterni è sempre risponde con una priorità molto bassa. Di conseguenza, i vari file progetto sempre rese a qualsiasi progetto con priorità più alta che è possibile aprire i file.  
  
 Il progetto file esterni non richiede all'utente di creare in modo esplicito con la **nuovo progetto** nella finestra di dialogo. Inoltre, il progetto file esterni non gestisce in modo permanente un elenco di membri del progetto. Per registrare un elenco dei file utilizzati di recente per ogni utente usa una funzionalità facoltativa.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Procedura: Apri editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: Aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md)   
 [Aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
