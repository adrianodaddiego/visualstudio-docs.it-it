---
title: Gestione di annullamento e ripristino con l'API Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a223d23cb792f13f1df9f869a540ffa61f50f9b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340636"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Gestire l'annullamento e ripristino con l'API legacy
Editor devono supportare operazioni di annullamento che consentono agli utenti di annullare le modifiche recenti quando si modificano codice. La maggior parte degli editor implementati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] può avere il supporto di annullamento fornito automaticamente dall'ambiente di sviluppo integrato (IDE).

## <a name="in-this-section"></a>Contenuto della sezione
- [Procedura: Implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md) fornisce funzionalità di annullamento per gli editor con uno o più visualizzazioni.

- [Procedura: Cancella lo stack di annullamento](../extensibility/how-to-clear-the-undo-stack.md) viene descritto come cancellare un stack di annullamento.

- [Procedura: Usare la gestione di annullamento collegata](../extensibility/how-to-use-linked-undo-management.md) incorpora collegato nell'editor di gestione dell'annullamento.

## <a name="reference"></a>Riferimenti
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Fornisce la gestione di annullamento per un editor che supporta più visualizzazioni.
