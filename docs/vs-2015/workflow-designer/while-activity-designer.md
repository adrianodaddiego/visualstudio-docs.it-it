---
title: Activity Designer while | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 36752df3d8ffbf33b8ea95570d6a4efe8c8cd3be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855394"
---
# <a name="while-activity-designer"></a>ActivityDesigner While

Il <xref:System.Activities.Statements.While> attività viene eseguita l'attività contenuta nel relativo <xref:System.Activities.Statements.While.Body%2A> mentre la condizione specificata restituisce **true**. L'attività contenuta potrebbe non essere mai eseguita. Se si desidera eseguirla almeno una volta, usare l'attività <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Proprietà di While in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.While> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.While> nell'intestazione. Il valore predefinito è While. Il valore può essere modificato nel **proprietà** finestra o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Contiene l'attività da eseguire durante la <xref:System.Activities.Statements.While.Condition%2A> restituisca **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contiene l'espressione [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] valutata per determinare se è necessario eseguire l'attività contenuta in <xref:System.Activities.Statements.While.Body%2A>.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)