---
title: Scelta di un modello di soluzione Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 36b821219b02fa77171d89214d8cf4813ce92303
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433396"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Scelta di un modello di soluzione per un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per creare una soluzione domain-specific language, scegliere uno dei modelli di soluzione che sono disponibili nella procedura guidata finestra di progettazione di linguaggio specifico di dominio. Scegliendo il modello che rispecchia maggiormente la lingua che si desidera creare, è possibile ridurre al minimo le modifiche da apportare alla soluzione di partenza.  
  
 I seguenti modelli di soluzione sono disponibili nella procedura guidata finestra di progettazione di linguaggio specifico di dominio.  
  
> [!NOTE]
> Lo scopo dei modelli è fornire un linguaggio specifico di dominio iniziale. I modelli di diagrammi classi e componenti denominati non sono diagrammi UML completi. Se si desidera creare un modello UML, prendere in considerazione gli strumenti che offrono un set di diagrammi integrati attorno a un singolo modello di modellazione UML. Sono estensibili e possono essere integrati con il linguaggio DSL con ModelBus. Per altre informazioni, vedere [creare modelli per l'app](../modeling/create-models-for-your-app.md).  
  
|Modello|Funzionalità|Descrizione|  
|--------------|--------------|-----------------|  
|Diagrammi classi|-Forme raggruppamento<br />-Ereditarietà classe<br />-Ereditarietà relazione<br />: Ereditarietà delle forme<br />-Proprietà relazione|Usare questo modello di soluzione se il linguaggio specifico di dominio include entità e relazioni che dispongono di proprietà. Questo modello crea un linguaggio specifico di dominio che è simile a diagrammi classi UML. Le entità principali sono le classi e interfacce, insieme alle relazioni di associazione, generalizzazione e l'implementazione. Una classe o interfaccia viene visualizzata come una casella che contiene un elenco di attributi.|  
|Diagrammi dei componenti|-Le porte|Usare questo modello di soluzione se il linguaggio specifico di dominio include i componenti, ovvero parti di un sistema software. Questo modello crea un linguaggio specifico di dominio che è simile a diagrammi dei componenti UML. Le entità principali sono i componenti e le porte, che vengono visualizzati come forme di piccole dimensioni all'esterno dei componenti.|  
|Diagrammi di flusso attività|-Immagini e forme geometriche<br />-   *Corsie*|Usare questo modello di soluzione se il linguaggio specifico di dominio sono inclusi i flussi di lavoro, stati o le sequenze. Questo modello crea un linguaggio specifico di dominio che è simile a diagrammi di attività UML. L'entità principale è un'attività e la relazione principale è una transizione tra le attività. Il modello include diversi altri elementi, ad esempio stato di avvio, lo stato finale e una barra di sincronizzazione.|  
|Linguaggio minimo|-Una classe e forma<br />-Una relazione e connettore|Usare questo modello di soluzione se il linguaggio specifico di dominio non corrisponde a altri modelli. Questo modello consente di creare un linguaggio specifico di dominio che dispone di due classi e una relazione, che sono rappresentati nel **casella degli strumenti** come **casella** e **riga**. La classe e la relazione di avere una proprietà di stringa di esempio.|  
|Progettazione Windows Form minimo|-Un modello di piccole dimensioni.<br />-Un Windows Form che consente di visualizzare il modello.|Usare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un modulo di Windows, anziché una finestra di progettazione grafica.<br /><br /> Il form che funge da interfaccia utente per la lingua è nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione di form.<br /><br /> Per altre informazioni, vedere [creazione di un linguaggio specifico di dominio Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Finestra di progettazione WPF minimo|-Un modello di piccole dimensioni<br />-Un'interfaccia utente di Windows Presentation Foundation che consente di visualizzare il modello|Usare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un'interfaccia utente WPF, anziché una finestra di progettazione grafica.<br /><br /> La finestra di progettazione per l'interfaccia utente si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione dell'interfaccia utente.<br /><br /> Per altre informazioni, vedere [creazione di un linguaggio specifico di dominio WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|Libreria DSL|-Una libreria minima|Usare questo modello se si desidera compilare una definizione DSL parziale che può essere importata in altre definizioni DSL.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
