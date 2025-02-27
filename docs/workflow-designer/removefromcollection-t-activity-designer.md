---
title: Finestra di progettazione del flusso di lavoro - RemoveFromCollection&lt;T&gt; ActivityDesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b3a43c05f8be4806cf10098a4df673903494756
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62933744"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T > ActivityDesigner

Il **RemoveFromCollection\<T >** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.RemoveFromCollection%601> attività.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection\<T > attività

L'attività <xref:System.Activities.Statements.RemoveFromCollection%601> rimuove un determinato elemento da una raccolta specifica.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Usando RemoveFromCollection\<T > ActivityDesigner

Accesso di **RemoveFromCollection\<T >** ActivityDesigner nel **raccolta** categoria del **casella degli strumenti**.
Il **RemoveFromCollection\<T >** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Ciò consente di creare un <xref:System.Activities.Statements.RemoveFromCollection%601> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> removefromcollection < Int32\>. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **RemoveFromCollection < T\>**  ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T\> proprietà

La tabella seguente illustra il <xref:System.Activities.Statements.RemoveFromCollection%601> proprietà e viene descritto come usarle nella finestra di progettazione:

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.RemoveFromCollection%601>. Il valore predefinito è RemoveFromCollection < Int32\>.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Elemento da rimuovere dal **Collection\<T >**. Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Raccolta da cui deve essere rimosso l'elemento. Questa raccolta è di tipo **ICollection < TypeArgument\>.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, ciò *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore della *TypeArgument* nella casella combinata nella griglia delle proprietà.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valore che indica se l'elemento specificato è stato rimosso dalla raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)