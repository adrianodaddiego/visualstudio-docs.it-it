---
title: 'Procedura: Utilizzare la ricerca nella finestra di progettazione del flusso di lavoro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1d62f1936e4cf424bde526301210e61f38e5b767
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931168"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procedura: Usare la ricerca in Progettazione flussi di lavoro
Per facilitare la creazione di flussi di lavoro più ampi e complessi, è possibile usare la ricerca in Progettazione flussi di lavoro per trovare gli elementi per parola chiave. Notare che la finestra di progettazione non supporta la sostituzione. La ricerca nella finestra di progettazione verrà trovato quanto segue:  
  
## <a name="quick-find"></a>Ricerca veloce  
 La ricerca rapida troverà nella finestra di progettazione quanto segue:  
  
- Proprietà degli oggetti <xref:System.Activities.Activity>, <xref:System.Activities.Statements.FlowNode>, <xref:System.Activities.Statements.State>, transizioni, nonché altri elementi di controllo del flusso personalizzati.  
  
- Variabili  
  
- Argomenti  
  
- Espressioni  
  
#### <a name="using-quick-find"></a>Uso di Ricerca veloce  
  
1. Con Progettazione flussi di lavoro aperta, premere **Ctrl + F**, o selezionare **Edit**, **Trova e sostituisci**, **ricerca veloce**.  
  
2. Immettere il termine di ricerca nel **Find what** nella casella di testo e fare clic su **Trova successivo**.  
  
3. Il termine di ricerca è posizionato nel flusso di lavoro corrente. Nella schermata seguente viene illustrato un nome visualizzato dell'attività che si trova nella finestra di progettazione.  
  
     ![Nei risultati della ricerca nella finestra di progettazione del flusso di lavoro](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>Cercare nei file  
 Tramite l'uso di Cerca nei file è possibile trovare le stringhe nei file del flusso di lavoro, inclusi i file XAML.  
  
#### <a name="using-find-in-files"></a>Uso di Cerca nei file  
  
1. In Visual Studio, premere **Ctrl + Maiusc + F**, o selezionare **Edit**, **Trova e sostituisci**, **Cerca nei file**  
  
2. Immettere l'elemento cercato nel **Find what** nella casella di testo e fare clic su **Trova tutto**  
  
3. Verrà visualizzato il risultato di ricerca nel [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **risultati di ricerca** visualizzazione. Facendo doppio clic su un elemento del risultato verrà visualizzata l'attività contenente la corrispondenza nella finestra di progettazione del flusso di lavoro.