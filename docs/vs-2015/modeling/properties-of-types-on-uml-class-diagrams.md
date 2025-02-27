---
title: Proprietà dei tipi su UML diagrammi classi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 996f2f75499a54e0d5514590f2b087130b73ffb5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387781"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Proprietà di tipi in diagrammi classi UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma classi UML, un *tipo* è una classe, un'interfaccia o enumerazione.  
  
> [!NOTE]
> Questo argomento illustra le proprietà dei tipi nei diagrammi classi UML Per altre informazioni, vedere i seguenti argomenti:  
  
- [Diagrammi delle classi UML: riferimenti](../modeling/uml-class-diagrams-reference.md)  
  
- [Diagrammi delle classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)  
  
- [Proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [Proprietà di operazioni in diagrammi classi UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
- [Proprietà delle associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
## <a name="properties"></a>Proprietà  
 Sono le proprietà di una classe, un'interfaccia o un'enumerazione.  
  
 Per visualizzare le proprietà di un tipo, fare clic sul tipo nel diagramma o nel **Esplora modelli UML**, quindi fare clic su **proprietà**. Le proprietà vengono visualizzate nel **proprietà** finestra.  
  
|**Property**|**Default**|Viene visualizzato in|Descrizione|  
|------------------|-----------------|----------------|-----------------|  
|**Name**|Nome predefinito|Tutti gli elementi|Identifica l'elemento.|  
|**Nome completo**|Pacchetto contenitore:: Nome tipo|Tutti gli elementi|Identifica l'elemento in modo univoco. Preceduto dal nome completo del pacchetto che lo contiene.|  
|**Colore**|Valore predefinito per il genere del tipo|Tutti gli elementi|Colore di questa forma. A differenza delle altre proprietà, questa non è una proprietà dell'elemento del modello sottostante. Visualizzazioni diverse dello stesso tipo possono avere colori diversi.|  
|**È di tipo Abstract**|False|Classe|Se true, non è possibile creare un'istanza della classe che deve essere usata come classe base.|  
|**È nodo foglia**|False|Classe, interfaccia|Se true, il tipo non può contenere tipi derivati.|  
|**È attivo**|False|Classe|Se true, ciascuna istanza del tipo è associata a un thread di controllo.|  
|**Visibilità**|Public|Classe, interfaccia, enumerazione|-Public: visibile globalmente.<br />-Private - questo tipo è visibile all'interno del pacchetto che ne è proprietario.<br />-Package: visibile all'interno del pacchetto.|  
|**Elementi di lavoro**|0 elementi associati|Tutti gli elementi|Numero di elementi di lavoro associati a questo elemento. Per associare gli elementi di lavoro, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).|  
|**Descrizione**|(vuoto)|Tutti gli elementi|È possibile inserire note generali sull'elemento.|  
|**Associazione di modelli**|(nessuno)|Classe, interfaccia, enumerazione|Se non è vuoto, questo tipo viene definito associando i valori dei parametri a questa classe di modello. Espandere la proprietà per visualizzare i binding dei parametri del modello.|  
|**Parametri di modelli**|(nessuno)|Classe, interfaccia, enumerazione|Se non è vuoto, è una classe di modello che contiene i parametri elencati. Per aggiungere i parametri o visualizzare le proprietà dei singoli parametri, fare clic su **[...]** .|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Proprietà di operazioni in diagrammi classi UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Proprietà delle associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [Diagrammi delle classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)
