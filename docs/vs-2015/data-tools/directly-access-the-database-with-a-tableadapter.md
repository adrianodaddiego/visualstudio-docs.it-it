---
title: Accedere direttamente al database con un TableAdapter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 924a14cc3938420f32a1a2c25265ebe94e261b15
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431956"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accedere direttamente al database mediante un oggetto TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oltre al `InsertCommand`, `UpdateCommand`, e `DeleteCommand`, vengono creati oggetti TableAdapter con metodi che possono essere eseguiti direttamente sul database. Questi metodi (`TableAdapter.Insert`, `TableAdapter.Update`, e `TableAdapter.Delete`) può essere chiamato per manipolare i dati direttamente nel database.  
  
 Se non si desidera creare questi metodi diretti, impostare dell'oggetto TableAdapter `GenerateDbDirectMethods` proprietà `false` nel **proprietà** finestra. Se tutte le query vengono aggiunti a un oggetto TableAdapter oltre la query TableAdapter principale, sono query autonomo che non generano questi metodi DbDirect.  
  
## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly a un database  
 Chiamare il metodo DbDirect di TableAdapter che esegue l'attività che si intende eseguire.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Per inserire nuovi record direttamente in un database  
  
- Chiamata dell'oggetto TableAdapter `Insert` , passando i valori per ogni colonna come parametri. La procedura seguente usa il `Region` tabella il databaseas Northwind un esempio.  
  
    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza di oggetto TableAdapter che si desidera utilizzare.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Per aggiornare i record direttamente in un database  
  
- Chiamata dell'oggetto TableAdapter `Update` , passando i valori originale e nuovi per ogni colonna come parametri.  
  
    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza di oggetto TableAdapter che si desidera utilizzare.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Per eliminare i record direttamente da un database  
  
- Chiamata dell'oggetto TableAdapter `Delete` , passando i valori per ogni colonna come parametri del `Delete` (metodo). La procedura seguente usa il `Region` tabella il databaseas Northwind un esempio.  
  
    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza di oggetto TableAdapter che si desidera utilizzare.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Vedere anche  
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
