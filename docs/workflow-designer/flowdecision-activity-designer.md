---
title: Finestra di progettazione del flusso di lavoro - Activity Designer FlowDecision
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 095ffb7284b9363d3bdb04749c8cff7114927935
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949669"
---
# <a name="flowdecision-activity-designer"></a>ActivityDesigner FlowDecision

Il nodo <xref:System.Activities.Statements.FlowDecision> è un nodo condizionale che fornisce due rami alternativi per il flusso di controllo a seconda che venga soddisfatta una condizione specificata. Se il flusso richiede più di due rami, usare invece <xref:System.Activities.Statements.FlowSwitch%601>.

## <a name="the-flowdecision-node"></a>Nodo FlowDecision

Usare <xref:System.Activities.Statements.FlowDecision> quando per il flusso è possibile creare due rami in due percorsi. Un nodo <xref:System.Activities.Statements.FlowDecision> presenta un oggetto <xref:System.Activities.Statements.FlowDecision.Condition%2A> e un oggetto <xref:System.Activities.Statements.FlowNode> associato a ognuno dei due possibili risultati: <xref:System.Activities.Statements.FlowDecision.True%2A> o <xref:System.Activities.Statements.FlowDecision.False%2A>. L'elemento <xref:System.Activities.Statements.FlowDecision.Condition%2A> viene valutato e il valore di questa valutazione determina il successivo nodo <xref:System.Activities.Statements.FlowNode> da elaborare nell'oggetto <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Utilizzo dell'ActivityDesigner FlowDecision

Il **FlowDecision** è disponibili nella finestra di progettazione il **diagramma di flusso** categoria del **della casella degli strumenti**, accessibile facendo clic la **casella degli strumenti** scheda della finestra di progettazione del flusso di lavoro. In alternativa, selezionare **della casella degli strumenti** dal **View** dal menu oppure premere **Ctrl**+**Alt** + **X**.

Il **FlowDecision** finestra di progettazione può essere trascinato dal **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro all'interno di un **Flowchart** ActivityDesigner. Verrà creato un <xref:System.Activities.Statements.FlowDecision> con l'etichetta **decisione** all'interno di <xref:System.Activities.Statements.Flowchart> attività. Spostare il mouse sulla finestra di progettazione e la **True** e **False** vengono visualizzati alcuni handle quadrati per i due rami.

Dopo avere trascinato il **FlowDecision** finestra di progettazione e altre finestre di progettazione sul **diagramma di flusso**, i nodi possono essere collegati tra loro per specificare l'ordine di esecuzione. Per creare un collegamento tra un nodo di origine (inclusi i **True** e **False** rami del **FlowDecision**) e un nodo di destinazione, spostare il mouse sulla finestra di progettazione del nodo di origine e visualizzare gli handle quadrati su ogni lato. Fare clic su uno degli handle quadrati e, tenendo premuto il pulsante del mouse, trascinarlo su uno degli handle visualizzati in modo simile intorno al nodo di destinazione durante il passaggio del mouse. Dopo aver rilasciato il pulsante del mouse, verrà creato un collegamento tra questi due nodi rappresentato da una freccia che collega la finestra di progettazione di origine a quella di destinazione.

L'espressione che dichiara il <xref:System.Activities.Statements.FlowDecision.Condition%2A> possono essere digitate nel **condizione** finestra di **proprietà** dalla finestra in cui viene visualizzato il testo di suggerimento "Immettere un'espressione VB".

### <a name="the-flowdecision-properties"></a>Proprietà di FlowDecision

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.FlowDecision> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Condizione che determina il percorso seguito dal controllo di flusso.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Percorso seguito dal controllo di flusso se viene soddisfatta <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Percorso seguito dal controllo di flusso se non viene soddisfatta <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|

## <a name="see-also"></a>Vedere anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)
- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)