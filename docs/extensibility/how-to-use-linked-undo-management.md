---
title: 'Procedura: Usare la gestione di annullamento collegato | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c26a07a573b682d8be569cb3e406e96cf486a4c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324735"
---
# <a name="how-to-use-linked-undo-management"></a>Procedura: Usare la gestione di annullamento collegato
Fase di rollback collegata consente all'utente di annullare contemporaneamente le stesse modifiche in più file. Ad esempio, le modifiche simultanee testo su più file di programma, ad esempio un file di intestazione e un file di Visual C++, è una transazione di annullamento collegata. Funzionalità di annullamento collegata è incorporata nell'implementazione dell'ambiente di gestione degli annullamenti, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> consente di modificare questa funzionalità. Fase di rollback collegata è implementata da un'unità di annullamento padre che è possibile collegare gli stack di annullamento separato insieme deve essere considerata come una sola unità di annullamento. La procedura per l'uso di annullamento collegata è descritta in dettaglio nella sezione seguente.

## <a name="to-use-linked-undo"></a>Per usare l'operazione di annullamento collegato

1. Chiamare `QueryService` sul `SVsLinkedUndoManager` per ottenere un puntatore a `IVsLinkedUndoTransactionManager`.

2. Creare l'unità di annullamento collegato padre iniziale chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Consente di impostare il punto di partenza per un set di campioni di stack di annullamento per volta essere raggruppati in stack di annullamento collegata. Nel `OpenLinkedUndo` metodo è necessario anche per specificare se si desidera che l'operazione di annullamento collegato non strict o strict. Comportamento di annullamento collegata non strict significa che alcuni dei documenti con elementi di pari livello di annullamento collegato può chiudere e lasciare l'altra collegato annullare nei rispettivi stack di elementi di pari livello. Il comportamento di annullamento collegato Strict specifica che tutti gli stack di pari livello di annullamento collegato devono essere annullata insieme o non ereditarli affatto. Aggiungere successivo collegati gli stack di annullamento chiamando [IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) (metodo).

3. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> per implementare tutte le unità di annullamento collegato come uno.

    > [!NOTE]
    > Per implementare la gestione di annullamento collegato in un editor, aggiungere la gestione di annullamento. Per altre informazioni sull'implementazione della gestione dell'annullamento collegato, vedere [come: Implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>
- [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)
- [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)
- [Procedura: Gestione dell'annullamento implementare](../extensibility/how-to-implement-undo-management.md)