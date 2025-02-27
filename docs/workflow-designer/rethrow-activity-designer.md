---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner Rethrow
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 558ff5a36d172b8cd1fef0b811d1eaa920b90c6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009275"
---
# <a name="rethrow-activity-designer"></a>ActivityDesigner Rethrow

Il **Rethrow** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Rethrow> attività.

## <a name="the-rethrow-activity"></a>Attività Rethrow

L'attività <xref:System.Activities.Statements.Rethrow> genera un'eccezione generata precedentemente. Questa attività può essere usata solo in un gestore <xref:System.Activities.Statements.Catch> nell'attività <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Utilizzo dell'ActivityDesigner ReThrow

Accesso di **Rethrow** ActivityDesigner nel **Error Handling** categoria del **della casella degli strumenti**. Il **Rethrow** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. La finestra di progettazione di attività di rilascio crea un <xref:System.Activities.Statements.Rethrow> attività con un valore predefinito **DisplayName** throw. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **Rethrow** ActivityDesigner, o nel **DisplayName** finestra della griglia delle proprietà.

### <a name="the-rethrow-properties"></a>Proprietà di Rethrow

La tabella seguente illustra il <xref:System.Activities.Statements.Rethrow> proprietà e viene descritto l'utilizzo nella finestra di progettazione:

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Rethrow>. Il valore predefinito è Rethrow.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)