---
title: Inserire nuovi record in un database | Microsoft Docs
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3f7ccd6af16d89c18f5a5bba63f6afc50de391c4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688723"
---
# <a name="insert-new-records-into-a-database"></a>Inserire nuovi record in un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per inserire nuovi record in un database, è possibile usare la `TableAdapter.Update` metodo, o uno dei metodi DBDirect di TableAdapter (in particolare il `TableAdapter.Insert` (metodo)).
  
 Se l'applicazione non usa gli oggetti TableAdapter, è possibile usare gli oggetti comando (ad esempio, <xref:System.Data.SqlClient.SqlCommand>) per inserire nuovi record nel database.  
  
 Se l'applicazione usa set di dati per archiviare i dati, usare il `TableAdapter.Update` (metodo). Il `Update` metodo invia tutte le modifiche (aggiornamenti, inserimenti ed eliminazioni) nel database.  
  
 Se l'applicazione usa gli oggetti per archiviare i dati oppure, se si desidera un maggiore controllo sulla creazione di nuovi record nel database, utilizzare il `TableAdapter.Insert` (metodo).  
  
 Se l'oggetto TableAdapter non ha un `Insert` metodo, significa che il TableAdapter sia configurato per utilizzare le stored procedure o dai relativi `GenerateDBDirectMethods` è impostata su `false`. Provare a impostare dell'oggetto TableAdapter `GenerateDBDirectMethods` proprietà `true` all'interno di progettazione set di dati e quindi salvare il set di dati. Questa operazione rigenererà il TableAdapter. Se l'oggetto TableAdapter non ancora un `Insert` (metodo), quindi la tabella non vengono fornite informazioni sufficienti dello schema per distinguere tra le singole righe (ad esempio, non potrebbe esserci alcun set di chiavi primarie nella tabella).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Inserire nuovi record usando oggetti TableAdapter  
 Gli oggetti TableAdapter forniscono diversi modi per inserire nuovi record in un database, a seconda dei requisiti dell'applicazione.  
  
 Se l'applicazione usa set di dati per archiviare i dati, quindi è semplicemente possibile aggiungere nuovi record per il valore desiderato <xref:System.Data.DataTable> nel set di dati e quindi chiamare il `TableAdapter.Update` (metodo). Il `TableAdapter.Update` metodo invia tutte le modifiche <xref:System.Data.DataTable> al database (inclusi i record modificati ed eliminati).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Per inserire nuovi record in un database usando il metodo di TableAdapter  
  
1. Aggiungere nuovi record per il valore desiderato <xref:System.Data.DataTable> creando un nuovo <xref:System.Data.DataRow> e aggiungendolo al <xref:System.Data.DataTable.Rows%2A> raccolta. Per altre informazioni, vedere [Procedura: Aggiungere righe a un oggetto DataTable](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).  
  
2. Dopo aver aggiunto le nuove righe per il <xref:System.Data.DataTable>, chiamare il `TableAdapter.Update` (metodo). È possibile controllare la quantità di dati da aggiornare passando un un'intera <xref:System.Data.DataSet>, una <xref:System.Data.DataTable>, una matrice di <xref:System.Data.DataRow>s o un singolo <xref:System.Data.DataRow>.  
  
    Il codice seguente viene illustrato come aggiungere un nuovo record a un <xref:System.Data.DataTable> e quindi chiamare il `TableAdapter.Update` metodo per salvare la nuova riga per il database. (Questo esempio viene usato il `Region` tabella nel database Northwind.)  
  
    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]  
  
   Se l'applicazione usa gli oggetti per archiviare i dati, è possibile usare il `TableAdapter.Insert` metodo per creare nuove righe direttamente nel database. Il `Insert` metodo accetta i singoli valori per ogni colonna come parametri. La chiamata al metodo inserisce un nuovo record nel database con i valori dei parametri passati.  
  
   La procedura seguente usa il `Region` tabella nel database Northwind come esempio.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Per inserire nuovi record in un database usando il metodo di TableAdapter  
  
- Chiamata dell'oggetto TableAdapter `Insert` , passando i valori per ogni colonna come parametri.  
  
    > [!NOTE]
    > Se non si dispone di un'istanza disponibile, creare un'istanza del TableAdapter che si desidera utilizzare.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Inserire nuovi record con gli oggetti comando  
 L'esempio seguente inserisce nuovi record direttamente in un database utilizzando oggetti command.
  
 La procedura seguente usa il `Region` tabella nel database Northwind come esempio.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Per inserire nuovi record in un database utilizzando oggetti comando  
  
- Creare un nuovo oggetto comando e quindi impostare relativi `Connection`, `CommandType`, e `CommandText` proprietà.  
  
     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 È necessario avere accesso a si sta tentando di connettersi al database, nonché dell'autorizzazione per eseguire l'inserimento nella tabella desiderata.  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
