---
title: Programmazione con l'API UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e85fc0add84f6f6097355d1fc7a58cc954c8e538
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111753"
---
# <a name="programming-with-the-uml-api"></a>Programmazione con l'API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'API UML di Visual Studio consente di scrivere codice per creare, leggere e aggiornare modelli e diagrammi UML. Per individuare le versioni di Visual Studio che supportano i modelli UML, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Oltre alle pagine di riferimento dell'API, gli argomenti seguenti descrivono l'API.  
  
|Argomento|Tipi e i metodi di esempio descritti|Funzionalità descritte|  
|-----------|-----------------------------------------|------------------------|  
|[Esplorare relazioni con l'API UML](../modeling/navigate-relationships-with-the-uml-api.md)|Elementi UML e relative proprietà e associazioni. Ad esempio, IElement e relativi discendenti, tra cui: IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage|In Visual Studio, i modelli UML conformi alla specifica UML versione 2.1.2, che può essere ottenuto nel [pagina delle risorse UML](http://go.microsoft.com/fwlink/?LinkId=160796). Ogni tipo è un'interfaccia avente lo stesso nome del tipo UML, preceduto da "I".|  
|[Creare elementi e relazioni nei modelli UML](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Ogni tipo di elemento dispone di metodi per la creazione dei relativi elementi figlio.|  
|[Visualizzare un modello UML nei diagrammi](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape.Move()|Ogni elemento in un modello può essere rappresentato come una forma in un diagramma. In alcuni casi è possibile creare nuove forme per ogni oggetto. È possibile spostare, ridimensionare, colorare, comprimere o espandere queste forme.|  
|[Esplorare il modello UML](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|L'archivio modelli archivia il modello.<br /><br /> Il contesto del diagramma consente di accedere al diagramma e all'archivio correnti.|  
|[Collegare aggiornamenti di modelli UML tramite transazioni](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|È possibile collegare una serie di modifiche in un'unica transazione.|  
|[Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Per estendere le funzionalità di un diagramma, definire i comandi richiamati facendo doppio clic e trascinando nel diagramma.|  
|[Definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|È possibile definire regole di convalida per assicurarsi che un modello UML sia conforme ai vincoli specificati.|  
|[Ottenere elementi di modelli UML da IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|Quando un elemento viene trascinato da Esplora modelli UML o da un diagramma UML in un altro diagramma o applicazione, viene serializzato come IDataObject.|  
|[Modificare i diagrammi di sequenza UML usando l'API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|L'operazione di creazione e aggiornamento di un diagramma di interazione è leggermente diversa dall'uso di altri tipi di diagramma.|  
|[Estendere i diagrammi livello](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|È possibile scrivere codice per creare e modificare i diagrammi livello e per convalidare il codice di programma rispetto a essi.|  
  
## <a name="about-the-implementation"></a>Informazioni sull'implementazione  
 Gli strumenti di modellazione UML sono compilati in [!INCLUDE[dsl](../includes/dsl-md.md)]. Ogni pacchetto e ogni diagramma sono rappresentati da un modello [!INCLUDE[dsl](../includes/dsl-md.md)] e una raccolta di regole e altri metodi ne mantiene la coerenza tra di essi.  
  
 I tipi di questa piattaforma sono visibili in tutti gli assembly cui viene fatto riferimento per scrivere estensioni UML. Sebbene sia possibile creare estensioni agli strumenti UML effettuando l'accesso all'API [!INCLUDE[dsl](../includes/dsl-md.md)], tenere presenti le considerazioni:  
  
- Si potrebbe scoprire che alcune modifiche apparentemente semplici introducono incoerenze ed effetti imprevisti.  
  
- L'implementazione può cambiare in futuro, pertanto gli adattamenti effettuati usando l'API [!INCLUDE[dsl](../includes/dsl-md.md)] potrebbero non essere più validi.  
  
## <a name="the-api-assemblies"></a>Assembly API  
 In questa tabella sono riepilogati gli assembly che forniscono estensibilità per gli strumenti UML e gli spazi dei nomi che si consiglia di usare.  
  
|Assembly|Spazi dei nomi|Consente di accedere a:|  
|--------------|----------------|-------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces|(Tutto)|Tipi UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml>|[Metodi di creazione](../modeling/create-elements-and-relationships-in-uml-models.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation>|[Diagrammi e forme](../modeling/display-a-uml-model-on-diagrams.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility>|[Il progetto di modellazione](../modeling/read-a-uml-model-in-program-code.md)|  
|Microsoft.VisualStudio.Modeling.Sdk.[versione]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Estensione di comando di menu](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Transazioni di annullamento collegato](../modeling/link-uml-model-updates-by-using-transactions.md).|  
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Convalida](../modeling/define-validation-constraints-for-uml-models.md)|  
||(altri spazi dei nomi)|Opzione consigliata solo per utenti esperti.|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versione]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[I gestori di movimento](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|  
||(altri spazi dei nomi)|Opzione consigliata solo per utenti esperti.|  
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|<xref:Microsoft.VisualStudio.TeamFoundation.WorkItemTracking>|[I collegamenti agli elementi di lavoro](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.WorkItemTracking.Client|<xref:Microsoft.TeamFoundation.WorkItemTracking.Client>|[Elementi di lavoro e i relativi campi](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.Client|<xref:Microsoft.TeamFoundation.Client>|[Elementi di lavoro e i relativi campi](../modeling/define-a-work-item-link-handler.md).|  
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Esportazione e importazione per i componenti MEF](../modeling/define-and-install-a-modeling-extension.md)|  
|System.Linq|<xref:System.Linq>|[Semplice manipolazione di raccolte, soprattutto quando si usano le relazioni](../modeling/navigate-relationships-with-the-uml-api.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Riferimento API per l'estensibilità di modellazione UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
