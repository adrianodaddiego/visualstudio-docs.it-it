---
title: Ereditarietà delle classi di dati (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a8df3d39e44bf1d40f3abfd4d6218d2c9a72b690
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567806"
---
# <a name="data-class-inheritance-or-designer"></a>Ereditarietà delle classi di dati (Object Relational Designer)

Analogamente ad altri oggetti, classi LINQ to SQL può usare l'ereditarietà ed essere derivate da altre classi. Nel codice è possibile specificare le relazioni di ereditarietà tra oggetti dichiarando che una classe eredita da un'altra. In un database le relazioni di ereditarietà vengono create in diversi modi. Il **Object Relational Designer** (**O/R Designer**) supporta il concetto di ereditarietà a tabella singola come viene spesso implementato nei sistemi relazionali.

Nell'ereditarietà a tabella singola è presente una singola tabella di database che contiene colonne per le classi base e derivate. Insieme ai dati relazionali, una colonna discriminante contiene il valore che determina la classe a cui appartiene uno specifico record. Si consideri, ad esempio, un `Persons` tabella che contiene tutte le persone impiegate in una società. alcune delle quali sono dipendenti mentre altre sono manager. Il `Persons` tabella contiene una colonna denominata `Type` che presenta un valore pari a 1 per i responsabili e il valore 2 per i dipendenti. Il `Type` colonna è la colonna discriminatore. In questo scenario, è possibile creare una sottoclasse di dipendenti e popolare la classe solo con i record che hanno un `Type` valore 2.

Quando si configura l'ereditarietà nelle classi dell'entità usando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], trascinare due volte la singola tabella che contiene i dati di ereditarietà sulla finestra di progettazione: una volta per ogni classe nella gerarchia di ereditarietà. Dopo avere aggiunto le tabelle alla finestra di progettazione, connetterle con un elemento di ereditarietà dalla casella degli strumenti **Object Relational Designer** e quindi impostare le quattro proprietà nella finestra **Proprietà**.

## <a name="inheritance-properties"></a>Proprietà di ereditarietà

Nella tabella seguente sono elencate le proprietà di ereditarietà e le rispettive descrizioni:

|Proprietà|Descrizione|
|--------------|-----------------|
|**Proprietà Discriminator**|Proprietà (mappata alla colonna) che determina a quale classe appartiene il record corrente.|
|**Valore discriminante classe di base**|Valore (nella colonna definita come **proprietà del discriminatore**) che determina che un record fa parte della classe di base.|
|**Valore discriminante classe derivata**|Valore (nella proprietà definita come **proprietà del discriminatore**) che determina che un record fa parte della classe derivata.|
|**Valore predefinito di ereditarietà**|La classe che viene popolata quando il valore nella proprietà definita come il **proprietà Discriminator** corrisponde a uno il **Base Class Discriminator Value** o **classe derivata da Valore discriminante**.|

La creazione di un modello a oggetti che usa l'ereditarietà e corrisponde ai dati relazionali può generare una certa confusione. Questo argomento fornisce informazioni sui concetti di base e sulle proprietà singole richieste per la configurazione dell'ereditarietà. Gli argomenti seguenti forniscono una spiegazione più chiara di come configurare l'ereditarietà con il **O/R Designer**.

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: Configurare l'ereditarietà usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Viene descritto come configurare le classi di entità che usano l'ereditarietà a tabella singola tramite il **O/R Designer**.|
|[Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Vengono fornite istruzioni dettagliate su come configurare le classi di entità che usano l'ereditarietà a tabella singola tramite il **O/R Designer**.|

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introduzione](/dotnet/framework/data/adonet/sql/linq/getting-started)