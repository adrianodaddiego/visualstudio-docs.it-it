---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30281d8cd5d5ed94ed89a980006f9618292a778d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951970"
---
# <a name="invokedelegate"></a>InvokeDelegate

Il **InvokeDelegate** designer viene utilizzato per creare e configurare un <xref:System.Activities.Statements.InvokeDelegate> attività.

## <a name="the-invokedelegate-activity"></a>L'attività InvokeDelegate

L'oggetto <xref:System.Activities.Statements.InvokeDelegate> chiama un delegato pubblico.

### <a name="using-the-invokedelegate-activity-designer"></a>Utilizzo dell'ActivityDesigner InvokeDelegate

Il **InvokeDelegate** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic di **dellacaselladeglistrumenti** della scheda [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu o premere CTRL + ALT + X.)

Il **InvokeDelegate** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie in cui le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.InvokeDelegate> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito InvokeDelegate. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InvokeDelegate** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.

### <a name="the-invokedelegate-properties"></a>Proprietà di InvokeDelegate

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeDelegate> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeDelegate>. Il valore predefinito è InvokeDelegate.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nome dell'elemento <xref:System.Activities.ActivityDelegate> da richiamare quando viene eseguita l'attività. È possibile modificare questa proprietà nell'area della finestra di progettazione. Si tratta di una proprietà obbligatoria.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Raccolta dell'argomento del delegato chiamato. Le chiavi sono i nomi degli oggetti <xref:System.Activities.DelegateArgument> su <xref:System.Activities.ActivityDelegate> e i valori sono gli argomenti le cui espressioni vengono valutate ed assegnate agli oggetti corrispondenti <xref:System.Activities.DelegateArgument>. Nella griglia delle proprietà, fare clic sul pulsante puntini di sospensione il **DelegateArguments** campo, viene visualizzato il **DelegateArguments** finestra di dialogo che consente di impostare questa proprietà. Scegliere il **Crea argomento** campo da aggiungere gli argomenti.|

## <a name="see-also"></a>Vedere anche

- [Procedura: Definire e usare delegati di attività in Progettazione flussi di lavoro](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)