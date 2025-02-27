---
title: Personalizzare il modello con profili e stereotipi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f7e9aee38208a96ab75318a86810359392b5b8e1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433350"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Personalizzare il modello con profili e stereotipi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile adattare gli elementi di modello UML standard, come classi e componenti, in modo da personalizzarli per scopi specifici. È possibile applicare una *stereotipo* a un elemento del modello che è possibile modificare l'elenco di proprietà dell'elemento. Gli stereotipi vengono definiti all'interno di raccolte chiamate *profili*.  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Per usare uno stereotipo, è necessario collegare un pacchetto a un profilo. In questo modo, è possibile applicare gli stereotipi definiti nel profilo agli elementi nel pacchetto. Alcuni profili vengono installati con Visual Studio. È anche possibile definire profili personalizzati.  
  
 Gli stereotipi possono essere impostati nell'elenco Proprietà di un elemento. Per i tipi di forma principali in un diagramma, gli stereotipi applicati vengono visualizzati anche nella forma, come mostrato nell'esempio.  
  
 ![Una classe UML con uno stereotipo. ](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")  
  
> [!NOTE]
> Se si usa un profilo per creare un modello e quindi si condivide il modello con altri utenti, questi non potranno visualizzare gli stereotipi a meno che non abbiano installato lo stesso profilo nel proprio computer.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Aggiungere stereotipi a elementi del modello UML](../modeling/add-stereotypes-to-uml-model-elements.md)|Inserimento di un elemento di modello in un pacchetto, collegamento del pacchetto a un profilo e applicazione di uno stereotipo all'elemento.|  
|[Stereotipi standard per modelli UML](../modeling/standard-stereotypes-for-uml-models.md)|I profili standard UML L2 e L3 vengono installati con Visual Studio e a essi è collegato ogni modello per impostazione predefinita. Questi profili forniscono stereotipi che è possibile usare per annotare i modelli.<br /><br /> Ad esempio, è possibile applicare lo stereotipo «specificazione» a una classe per indicare che è destinata solo a definire il comportamento visibile esternamente delle sue istanze.|  
|[Definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md)|È possibile definire stereotipi e strumenti personalizzati, adattati all'area della propria applicazione.<br /><br /> Ad esempio, se si sviluppa software bancario, si potrebbe definire uno stereotipo «conto» da applicare alle classi. Sarebbe quindi possibile usare diagrammi classi per definire tipi diversi di conto e le rispettive relazioni.|  
|[Installare un profilo UML](../modeling/install-a-uml-profile.md)|Se si è ricevuto un profilo UML da un altro utente, è possibile installarlo nel proprio computer.|  
|[Definire un elemento della casella degli strumenti di modellazione personalizzata](../modeling/define-a-custom-modeling-toolbox-item.md)|Un elemento personalizzato della Casella degli strumenti evita la necessità di ripetere l'impostazione di uno stereotipo in nuovi elementi.|  
|[Colorare le classi UML per stereotipo](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Questo codice di esempio estende i diagrammi UML, impostando automaticamente il colore di una forma UML in base allo stereotipo dell'elemento.|
