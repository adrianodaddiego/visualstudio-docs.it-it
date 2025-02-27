---
title: Tasti di scelta rapida nella finestra di progettazione del flusso di lavoro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1a03463d292fa1d4d980c62daa74b291d6a8cb1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951957"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Tasti di scelta rapida di Progettazione flussi di lavoro
È possibile accedere a tutte le principali funzionalità di [!INCLUDE[wfd1](../includes/wfd1-md.md)] dalla tastiera.  
  
## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navigazione in Progettazione flussi di lavoro mediante la tastiera  
 In [!INCLUDE[vs2010](../includes/vs2010-md.md)] i collegamenti globali e collegamenti di debug si applicano a [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Sono stati inoltre creati tasti di scelta rapida specifici di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. In [!INCLUDE[vs2010](../includes/vs2010-md.md)] tutti i tasti di scelta rapida possono essere rimappati. In un'applicazione riallocata, tuttavia, i tasti di scelta rapida sono hardcoded.  
  
### <a name="workflow-designer-keyboard-shortcuts"></a>Tasti di scelta rapida di Progettazione flussi di lavoro  
 Nella tabella seguente vengono riepilogati i tasti di scelta rapida predefiniti assegnati ai comandi di [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Collegamento|Scopo|  
|--------------|-------------|  
|CTRL+E, A|Mostra o nasconde Progettazione argomenti.|  
|CTRL+E, C|Comprime l'attività selezionata sul posto.|  
|CTRL+E, E|Espande l'attività selezionata sul posto.|  
|CTRL+E, F|Connette le attività selezionate in un diagramma di flusso.|  
|CTRL+E, I|Mostra o nasconde la finestra di progettazione importazioni.|  
|CTRL+E, M|Sposta lo stato attivo sull'elemento successivo nell'ordine di tabulazione.|  
|CTRL+E, N|Crea una nuova variabile nell'ambito dell'attività selezionata (o quella più vicina).|  
|CTRL+E, O|Mostra o nasconde la carta panoramica.|  
|CTRL+E, P|Consente di passare all'attività padre dell'attività selezionata. Consente di salire di un livello nell'esplorazione tramite la barra di navigazione e di modificare l'attività radice nell'area di progettazione.|  
|CTRL+E, S|Aggiunge alla selezione corrente l'elemento con stato attivo.|  
|CTRL+E, V|Mostra o nasconde Progettazione variabili.|  
|CTRL+E, X|Espande tutte le attività nel flusso di lavoro.|  
|CTRL + ALT + F6|Sposta lo stato attivo dall'area dell'interfaccia utente corrente all'area successiva nella sequenza. L'ordine è il seguente:<br /><br /> 1.  Barra di navigazione.<br />2.  Area di progettazione<br />3.  Argomenti/Variabili/finestra di progettazione importazioni, se aperta<br />4.  Shell|  
  
### <a name="flowchart"></a>Diagramma di flusso  
 Nell'elenco seguente vengono presentate le operazioni necessarie per costruire un diagramma di flusso dalla tastiera. Come nella parte rimanente di [!INCLUDE[wfd2](../includes/wfd2-md.md)], le attività vengono aggiunte all'area di progettazione usando i collegamenti globali alla casella degli strumenti forniti in [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
- Per spostare un'attività, selezionarla e riposizionarla usando i tasti di direzione.  
  
- Per ridimensionare un diagramma di flusso, spostare un'attività oltre il bordo corrente del diagramma di flusso usando i tasti di direzione. Il diagramma di flusso viene ridimensionato automaticamente.  
  
- Per impostare un'attività come nodo iniziale, usare il **imposta come StartNode** comando nel menu di scelta rapida.  
  
- Per connettere le attività:  
  
  1. Selezionare l'attività di origine usando il tasto TAB.  
  
  2. Premere CTRL+E, M il numero di volte necessario per spostare lo stato attivo sull'attività di destinazione.  
  
  3. Premere CTRL+E, S per aggiungere l'attività di destinazione alla selezione.  
  
  4. Premere CTRL+E, F per aggiungere il connettore dall'origine alla destinazione.  
  
  Note sulla connessione delle attività dalla tastiera:  
  
- È possibile creare contemporaneamente più connessioni aggiungendo più attività alla selezione prima di premere CTRL+E, F. Le connessioni vengono create nell'ordine in cui le attività sono state aggiunte alla selezione.  
  
- Se una coppia di attività non può essere connessa, ad esempio se per l'attività di origine è già presente una connessione in uscita, le altre connessioni tra le attività della selezione vengono comunque create quando possibile.  
  
- Quando un **FlowDecision** è incluso nella selezione e il **FlowDecision** non dispone di alcun connettori in uscita, il connettore viene posizionato sul **True** ramo.  
  
### <a name="expression-editing"></a>Modifica dell'espressione  
 Per impostazione predefinita, i tasti di scelta rapida predefiniti per la modifica del testo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] si applicano nell'editor espressioni in [!INCLUDE[wfd2](../includes/wfd2-md.md)] con le limitazioni seguenti:  
  
- La modifica del mapping dei tasti di scelta rapida per i comandi seguenti non ha effetto. In caso di modifica di un'espressione, è possibile accedere a questi comandi solo mediante i tasti di scelta rapida predefiniti.  
  
    1. Taglia  
  
    2. Copia  
  
    3. Incolla  
  
    4. Seleziona tutto  
  
    5. Annulla  
  
    6. Ripristina  
  
- Per modificare il mapping dei tasti di scelta rapida per i comandi di modifica delle espressioni all'interno di [!INCLUDE[wfd2](../includes/wfd2-md.md)] in [!INCLUDE[vs2010](../includes/vs2010-md.md)], modificare i collegamenti nell'ambito di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Le modifiche apportate nell'ambito dell'Editor di testo non si applicano automaticamente a [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Se si desidera modificare il mapping dei collegamenti in entrambi gli ambiti, è necessario applicare le modifiche due volte, una volta per ogni ambito.