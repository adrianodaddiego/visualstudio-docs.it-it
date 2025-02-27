---
title: 'Procedura: Aprire gli editor di documenti aperti | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8342947681bcd8f698c2a646e917b353ec6c9dd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319320"
---
# <a name="how-to-open-editors-for-open-documents"></a>Procedura: Aprire gli editor di documenti aperti
Prima di una finestra del documento viene aperto un progetto, il progetto prima di tutto necessario determinare se il file è già aperto nella finestra del documento per un altro editor. Il file è possibile aprire in un editor specifico del progetto o uno degli editor standard registrato con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="open-a-project-specific-editor"></a>Aprire un editor specifico del progetto
 Usare la procedura seguente per aprire un editor specifico del progetto per un file che è già aperto.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Per aprire un editor specifico del progetto per un file aperto

1. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.

    Questa chiamata restituisce puntatori alla gerarchia del documento, elemento della gerarchia e cornice della finestra, se appropriato.

2. Se il documento è aperto, il progetto deve verificare se è presente solo un oggetto dati del documento o se è presente anche un oggetto visualizzazione del documento.

   - Se è presente un oggetto visualizzazione del documento e questa visualizzazione è per una gerarchia diversa o un elemento della gerarchia, il progetto utilizza il puntatore alla cornice della finestra della visualizzazione per resurface finestra esistente.

   - Se è presente un oggetto visualizzazione del documento e questa visualizzazione è disponibile per la stessa gerarchia ed elemento di gerarchia, il progetto può aprire una seconda vista se è possibile collegare all'oggetto dati documento sottostante. In caso contrario, il progetto deve utilizzare il puntatore alla cornice della finestra della visualizzazione a resurface finestra esistente.

   - Se esiste l'oggetto dati del documento, solo il progetto deve determinare se l'oggetto dati del documento possono utilizzare per la relativa visualizzazione. Se l'oggetto dati del documento è compatibile, completato i passaggi descritti in [aprire un editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).

     Se l'oggetto dati del documento non è compatibile, dovrebbe essere visualizzato un errore all'utente che indica che il file è attualmente in uso. Questo errore deve essere visualizzato solo in casi temporanei, ad esempio quando un file è in fase di compilazione nello stesso momento l'utente sta tentando di aprire il file utilizzando un editor diverso il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor di testo principale. L'editor di testo principale può condividere l'oggetto dati del documento con il compilatore.

3. Se il documento non è aperto perché non esiste un oggetto dati del documento o un oggetto visualizzazione del documento, completare i passaggi descritti in [aprire un editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).

## <a name="open-a-standard-editor"></a>Aprire un editor standard
 Utilizzare la procedura seguente per aprire un editor standard di un file che è già aprire.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Per aprire un editor standard di un file aperto

1. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Questo metodo verifica innanzitutto che il documento non è già aperto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Se il documento è già aperto, la finestra dell'editor è riapparire.

2. Se il documento non è aperto, quindi completare la procedura descritta in [come: Aprire gli editor standard](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vedere anche
- [Aprire e salvare elementi del progetto](../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: Apri editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: Apri editor standard](../extensibility/how-to-open-standard-editors.md)
