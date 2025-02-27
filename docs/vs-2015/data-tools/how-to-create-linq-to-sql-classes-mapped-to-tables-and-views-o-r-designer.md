---
title: 'Procedura: Creare LINQ to SQL classi mappate a tabelle e visualizzazioni (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b9bff102fbf87149e3adc80029eea17132e9b1b7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697721"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Procedura: Creare classi LINQ to SQL mappate a tabelle e viste (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Classi LINQ to SQL mappate a tabelle di database e le viste vengono chiamati *le classi di entità*. Per la classe di entità viene eseguito il mapping a un record, mentre per le singole proprietà di una classe di entità viene eseguito il mapping alle singole colonne che costituiscono un record. Creare classi di entità che si basano su viste o tabelle di database trascinando le tabelle o viste dal **Esplora Server**/**Database Explorer** nel [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] genera le classi e applica le specifiche [! LINQ agli attributi SQL per abilitare [! LINQ alle funzionalità di SQL (la comunicazione dei dati e le funzionalità di modifica di <xref:System.Data.Linq.DataContext>). Per informazioni dettagliate su [! Classi LINQ to SQL, vedere [LINQ al modello a oggetti SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> Il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] è un mapper relazionale a oggetti semplice, perché supporta solo le relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, quale il mapping di una classe di entità a più tabelle, non è supportato. Tuttavia, è possibile eseguire il mapping di una classe di entità a una visualizzazione che crea un join tra più tabelle correlate.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Creazione di classi LINQ to SQL con mapping a tabelle o visualizzazioni di database
 Trascinamento di tabelle o viste dal **Esplora Server**/**Esplora Database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] consente di creare classi di entità oltre al <xref:System.Data.Linq.DataContext> i metodi utilizzati per esegue gli aggiornamenti.

 Per impostazione predefinita, il [! Runtime LINQ to SQL consente di creare la logica per salvare le modifiche apportate da una classe di entità aggiornabile nel database. Tale logica si basa sullo schema della tabella (definizioni di colonna e informazioni sulla chiave primaria). Se non si desidera questo comportamento, è possibile configurare una classe di entità per l'utilizzo di stored procedure per eseguire inserimenti, aggiornamenti ed eliminazione anziché usare il valore predefinito [! LINQ al comportamento di runtime SQL. Per altre informazioni, vedere [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Per creare classi LINQ to SQL con mapping a tabelle o visualizzazioni di database

1. Nelle **Server**/**Esplora Database**, espandere **tabelle** oppure **viste** e individuare la tabella di database o visualizzare da da utilizzare nell'applicazione.

2. Trascinare la tabella o la visualizzazione in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. Tale classe presenta proprietà con mapping alle colonne nella tabella o visualizzazione selezionata.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Creazione dell'origine dati di un oggetto e visualizzazione dei dati in un form
 Dopo aver creato le classi di entità usando il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], è possibile creare un'origine dati oggetto e popolare il [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) con le classi di entità.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Per creare l'origine dati di un oggetto in base alle classi di entità LINQ to SQL

1. Scegliere **Compila soluzione** dal menu **Compila** per compilare il progetto.

2. Scegliere **Mostra origini dati** dal menu **Dati**.

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

4. Nella pagina **Seleziona un tipo di origine dati** fare clic su **Oggetto** e quindi su **Avanti**.

5. Espandere i nodi, quindi individuare e selezionare la classe.

    > [!NOTE]
    > Se la classe **Customer** non è disponibile, chiudere la procedura guidata, compilare il progetto ed eseguire nuovamente la procedura guidata.

6. Fare clic su **Fine** per creare l'origine dati e aggiungere la classe di entità **Customer** alla finestra **Origini dati**.

7. Trascinare gli elementi dalla finestra **Origini dati** in un form.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: Creare metodi DataContext di cui viene eseguito il mapping a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Modello a oggetti LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Procedura dettagliata: Personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procedura dettagliata: Aggiunta della convalida alle classi di entità](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Procedura: Creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)