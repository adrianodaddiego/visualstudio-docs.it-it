---
title: Aggiornare i dati mediante un TableAdapter | Microsoft Docs
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30d1fd3ee211d6b30f435104a2e2f9b42ed100c0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692342"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aggiornare i dati mediante un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dopo aver modificati i dati nel set di dati e convalidati, è possibile inviare i dati aggiornati all'oggetto chiamando il metodo databaseby il `Update` metodo di un oggetto TableAdapter. Il `Update` metodo aggiorna una singola tabella di dati ed esegue il comando corretto (INSERT, UPDATE o DELETE) in base il <xref:System.Data.DataRow.RowState%2A> di ogni riga di dati nella tabella. Quando un set di dati dispone di tabelle correlate, Visual Studio genera una classe di TableAdapterManager utilizzabili per eseguire gli aggiornamenti. La classe di TableAdapterManager assicura che gli aggiornamenti vengono eseguiti nell'ordine corretto in base ai vincoli di chiave esterna che sono definiti nel database. Quando si usano controlli associati a dati, l'architettura di Data Binding crea una variabile membro della classe TableAdapterManager chiamata tableAdapterManager. Per altre informazioni, vedere [Cenni preliminari sull'aggiornamento gerarchico](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
> Quando si tenta di aggiornare un'origine dati con il contenuto di un set di dati, è possibile ottenere gli errori. Per evitare errori, è consigliabile si inserire il codice che chiama l'adapter `Update` metodo all'interno di un `try` / `catch` blocco.  
  
 La procedura esatta per l'aggiornamento di un'origine dati può variare a seconda delle esigenze aziendali, ma i passaggi seguenti:  
  
1. Chiamare l'adattatore `Update` metodo in un `try` / `catch` blocco.  
  
2. Se viene rilevata un'eccezione, individuare la riga di dati che ha causato l'errore. Per altre informazioni, vedere [Procedura: Individuare le righe che contengono errori](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3. Risolvere il problema nei dati di riga (a livello di codice se possibile, o presentando la riga non valida per l'utente per la modifica) e quindi ripetere l'operazione di aggiornamento (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="savedata-to-a-database"></a>SaveData a un database  
 Chiamare il `Update` metodo di un oggetto TableAdapter. Passare il nome della tabella dati contenente i valori da scrivere nel database.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Per aggiornare un database mediante un TableAdapter  
  
- Racchiudere dell'oggetto TableAdapter`Update` metodo in un `try` / `catch` blocco. Nell'esempio seguente viene illustrato come aggiornare il contenuto del `Customers` nella tabella `NorthwindDataSet` dall'interno una `try` / `catch` blocco.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
