---
title: Persistenza e l'esecuzione del documento nella tabella | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80932ab926b7ef26eaef10991e4f5782e81c4b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328529"
---
# <a name="persistence-and-the-running-document-table"></a>Salvataggio permanente e tabella documenti in esecuzione
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, i progetti sono completamente responsabili per la gestione di elementi di progetto, che sono portare a termine usando il servizio, la persistenza <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. I documenti sono l'unità di base di persistenza nell'ambiente di Visual Studio. I progetti di coordinare l'apertura, salvataggio e ridenominazione dei documenti con la tabella documenti in esecuzione (RDT), una risorsa che controlla lo stato di tutti i documenti aperti.

## <a name="managing-persistence"></a>Gestione della persistenza
 Progetti consentono di controllare il servizio di persistenza dell'ambiente mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfaccia. Mentre l'ambiente chiede mai direttamente un documento in modo permanente se stessa, viene richiesto il progetto proprietario (o gerarchia) per salvare il documento. Questo rende possibile per il progetto salvare i dati di elemento di progetto in file locali, i file remoti, un database, un repository o altro supporto.

 L'ambiente globale conserva RDT. L'ambiente mantiene le voci per tutte le finestre aperte e i documenti nella RDT, che rende possibile per poter ricevano le notifiche speciali, ad esempio quando viene chiusa una soluzione. Inoltre, RDT rende possibile per l'ambiente rilevare i nodi corrispondenti nella **Esplora soluzioni**. RDT mantiene un record per ogni oggetto aperto, persistente, inclusi i file di progetto e i documenti di elementi di progetto.

## <a name="see-also"></a>Vedere anche
- [Tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)