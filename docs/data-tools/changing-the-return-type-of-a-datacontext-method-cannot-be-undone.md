---
title: La modifica del tipo restituito di un metodo DataContext non può essere annullata
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7aee87e353cb3b69b70e78508c20a9a9c1ed5102
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460679"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>La modifica del tipo restituito di un metodo DataContext non può essere annullata

La modifica del tipo restituito di un metodo DataContext non può essere annullata. Per ripristinare il tipo generato automaticamente, è necessario trascinare nuovamente l'oggetto da **Esplora server** o **Esplora database** in Object Relational Designer. Modificare il tipo restituito?

Il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> varia a seconda della posizione in cui si rilascia l'elemento in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità. Se invece si rilascia un elemento in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], viene creato un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e fare clic sulla proprietà **Return Type** nella finestra **Proprietà**.

## <a name="to-change-the-return-type-of-a-datacontext"></a>Per modificare il tipo restituito di un metodo DataContext

- Scegliere **Sì**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Per uscire dalla finestra di messaggio e lasciare invariato il tipo restituito

- Fare clic su **No**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Per ripristinare il tipo restituito originale dopo la modifica del tipo restituito

1. Selezionare il metodo <xref:System.Data.Linq.DataContext> in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ed eliminarlo.

2. Individuare l'elemento in **Esplora server/Esplora database** e trascinarlo in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    Viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito predefinito originale.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)