---
title: Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d28c9456afdc60b1bddadf759ec3090ba37f2040
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445487"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità
  Gli strumenti di sviluppo di Office in Visual Studio forniscono classi e finestre di progettazione che gestiscono molti dettagli di implementazione quando vengono usate per creare riquadri attività personalizzati, personalizzazioni della barra multifunzione e aree del modulo di Outlook in un componente aggiuntivo VSTO. Tuttavia, se sono necessari requisiti speciali è anche possibile implementare *l'interfaccia di estendibilità* per ogni funzionalità.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Panoramica delle interfacce di estendibilità
 Microsoft Office definisce un set di interfacce di estendibilità che possono essere implementate nei componenti aggiuntivi VSTO COM per personalizzare determinate funzionalità, ad esempio la barra multifunzione. Queste interfacce forniscono il controllo completo sulle funzionalità alle quali forniscono l'accesso. Tuttavia, l'implementazione di queste interfacce richiede una certa conoscenza dell'interoperabilità COM nel codice gestito. In alcuni casi, il modello di programmazione di queste interfacce non è intuitivo neppure per gli sviluppatori abituati a .NET Framework.

 Quando si crea un componente aggiuntivo VSTO usando i modelli di progetto di Office in Visual Studio, non è necessario implementare interfacce di estendibilità per personalizzare funzionalità come la barra multifunzione. Queste interfacce vengono implementate automaticamente da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Al contrario, è possibile usare classi e finestre di progettazione più intuitive fornite da Visual Studio. Tuttavia, è anche possibile implementare le interfacce di estendibilità direttamente nel componente aggiuntivo VSTO.

 Per altre informazioni sulle classi e finestre di progettazione fornite da Visual Studio per queste funzionalità, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md), [progettazione della barra multifunzione](../vsto/ribbon-designer.md), e [aree del modulo Outlook creare](../vsto/creating-outlook-form-regions.md).

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Interfacce di estendibilità che implementabili in un componente aggiuntivo VSTO
 La tabella seguente elenca le interfacce di estendibilità implementabili e le applicazioni che le supportano.

|Interfaccia|Descrizione|Applicazioni|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implementare questa interfaccia per personalizzare l'interfaccia utente della barra multifunzione. **Nota:**  È possibile aggiungere un **sulla barra multifunzione (XML)** elemento a un progetto per generare un valore predefinito <xref:Microsoft.Office.Core.IRibbonExtensibility> implementazione nel componente aggiuntivo VSTO. Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Progetto<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implementare questa interfaccia per creare un riquadro attività personalizzato.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implementare questa interfaccia per creare un'area di modulo Outlook.|Outlook|

 Esistono diverse altre interfacce di estendibilità definite dalle applicazioni di Microsoft Office, ad esempio <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>e <xref:Microsoft.Office.Core.SignatureProvider>. In Visual Studio l'implementazione di queste interfacce in un componente aggiuntivo VSTO creato usando i modelli di progetto di Office non è supportata.

## <a name="use-extensibility-interfaces"></a>Usare interfacce di estendibilità
 Per personalizzare una funzionalità dell'interfaccia utente usando un'interfaccia di estendibilità, implementare l'interfaccia appropriata nel progetto del componente aggiuntivo VSTO. Eseguire quindi l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> in modo da ottenere un'istanza della classe che implementi l'interfaccia.

 Per un'applicazione di esempio che illustra come implementare il <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, e <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> interfacce in un componente aggiuntivo VSTO per Outlook, vedere l'esempio di gestione dell'interfaccia utente in [esempi di sviluppo Office](../vsto/office-development-samples.md).

### <a name="example-of-implementing-an-extensibility-interface"></a>Esempio di implementazione di un'interfaccia di estendibilità
 Nell'esempio di codice riportato di seguito viene illustrata l'implementazione dell'interfaccia <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> per creare un riquadro attività personalizzato. Nell'esempio vengono definite due classi:

- La classe `TaskPaneHelper` implementa <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> per creare e visualizzare un riquadro attività personalizzato.

- La classe `TaskPaneUI` fornisce l'interfaccia utente del riquadro attività. Gli attributi della classe `TaskPaneUI` rendono la classe visibile a COM, permettendo alle applicazioni di Microsoft Office di individuare la classe. In questo esempio, <xref:System.Windows.Forms.UserControl>è un'interfaccia utente vuota, ma è possibile aggiungere i controlli modificando il codice.

  > [!NOTE]
  > Per esporre la classe `TaskPaneUI` a COM è necessario impostare anche la proprietà **Registra per interoperabilità COM** per il progetto.

  [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
  [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]

  Per altre informazioni sull'implementazione <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, vedere [creare riquadri attività personalizzati in Office system 2007](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) nella documentazione di Microsoft Office.

### <a name="example-of-overriding-the-requestservice-method"></a>Esempio di override del metodo RequestService
 L'esempio di codice seguente illustra come eseguire l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> per ottenere un'istanza della classe `TaskPaneHelper` dall'esempio di codice precedente. Viene verificato il valore del parametro *serviceGuid* per determinare l'interfaccia necessaria e quindi viene restituito un oggetto che implementa l'interfaccia.

 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]

## <a name="see-also"></a>Vedere anche
- [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)
- [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)
- [Sviluppare soluzioni Office](../vsto/developing-office-solutions.md)
- [Chiamare il codice nei componenti aggiuntivi VSTO da altre soluzioni Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
