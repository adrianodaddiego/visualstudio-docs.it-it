---
title: Oggetti aggiunti alla finestra di progettazione usano una connessione dati diversa
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c85e0c17eeb4cfbd786faac338c8b908c5a7f363
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260932"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Gli oggetti a cui che si aggiunge alla finestra di progettazione utilizzano una connessione dati diversa da quella della finestra di progettazione

Gli oggetti in corso di aggiunta alla finestra di progettazione usano una connessione dati diversa da quella usata per la finestra di progettazione. Sostituire la connessione usata per la finestra di progettazione?

Quando si aggiungono elementi per il **Object Relational Designer** (**O/R Designer**), tutti gli elementi usano una sola connessione dei dati condivisa. (l'area di progettazione rappresenta l'oggetto <xref:System.Data.Linq.DataContext>, che usa una sola connessione per tutti gli oggetti nell'area). Questo messaggio viene visualizzato se si aggiunge alla finestra di progettazione un oggetto che usa una connessione dati differente da quella attualmente usata per la finestra di progettazione. Per correggere l'errore, è possibile scegliere di mantenere la connessione esistente. In questo caso, l'oggetto selezionato non verrà aggiunto. In alternativa, è possibile scegliere di aggiungere l'oggetto e reimpostare la connessione di <xref:System.Data.Linq.DataContext> sulla nuova connessione.

## <a name="connection-options"></a>Opzioni di connessione

- Per sostituire la connessione esistente con la connessione utilizzata dall'oggetto selezionato, fare clic su **Sì**.

   L'oggetto selezionato viene aggiunto per il **O/R Designer**e il *DataContext* è impostato sulla nuova connessione.

   > [!NOTE]
   > Se si sceglie **Yes**, classi di tutte le entità nel **O/R Designer** viene eseguito il mapping alla nuova connessione.

- Per continuare a usare la connessione esistente e Annulla aggiunta dell'oggetto selezionato, fare clic su **No**.

   L'azione viene annullata e l'oggetto *DataContext.Connection* resta impostato sulla connessione esistente.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
