---
title: Funzionalità disponibili in base al tipo di progetto e applicazioni di Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: df645fc7f53bbcd0ad5294182d13e96b57b5d42d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431581"
---
# <a name="features-available-by-office-application-and-project-type"></a>Funzionalità disponibili in base al tipo di progetto e applicazioni di Office
  In Visual Studio sono disponibili numerosi tipi di modelli di progetto che supportano scenari aziendali diversi per le applicazioni di Microsoft Office, inclusi i tipi seguenti:

- Personalizzazioni a livello di documento.

- Componenti aggiuntivi VSTO.

  Non tutte le applicazioni possono utilizzare ogni tipo di progetto. Ad esempio, i progetti a livello di documento sono disponibili solo per Microsoft Office Word e Microsoft Office Excel. Analogamente, alcune funzionalità sono disponibili solo per determinati tipi di progetti o applicazioni. Ad esempio, il riquadro azioni è disponibile solo nei progetti a livello di documento e le estensioni della barra multifunzione sono disponibili solo per alcune applicazioni. Per altre informazioni sui diversi tipi di progetto, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

> [!NOTE]
> Modelli di progetto di Office sono disponibili solo in alcune edizioni di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni, vedere [configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Tipi di progetto disponibili per diverse applicazioni di Microsoft Office
 Nella tabella seguente sono indicate le applicazioni che è possibile utilizzare con ogni tipo di progetto.

|Tipi di progetto|Applicazione Microsoft Office|
|-------------------|----------------------------------|
|Personalizzazioni a livello di documento|Excel<br /><br /> Word|
|Componenti aggiuntivi VSTO|Excel<br /><br /> InfoPath (solo InfoPath 2013 e InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Progetto<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>Funzionalità disponibili in diversi tipi di progetto
 Nella tabella seguente sono indicati i tipi di progetto che forniscono ciascuna funzionalità.

|Funzionalità|Tipi di progetto che forniscono la funzionalità|Ulteriori informazioni|
|-------------|--------------------------------------------|---------------------|
|Riquadro azioni.|Progetti a livello di documento.|[Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)|
|Distribuzione ClickOnce.|Progetti a livello di documento e VS.|[Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)|
|Riquadri attività personalizzati.|Progetti di componente aggiuntivo VSTO per le applicazioni seguenti:<br /><br /> -   Excel<br />-InfoPath (InfoPath 2013 e InfoPath 2010 solo)<br />-   Outlook<br />-   PowerPoint<br />-   Word|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|
|Parti XML personalizzate.|Progetti a livello di documento.<br /><br /> Progetti di livello applicazione per le applicazioni seguenti:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|[Panoramica delle parti XML personalizzata](../vsto/custom-xml-parts-overview.md)|
|Cache dei dati.|Progetti a livello di documento.|[Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)|
|Esporre un oggetto in un componente aggiuntivo VSTO ad altre soluzioni Microsoft Office.|Progetti di componente aggiuntivo VSTO.|[Chiamare il codice nei componenti aggiuntivi VSTO da altre soluzioni Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|I controlli host seguenti:<br /><br /> -Grafico<br />-ListObject<br />-NamedRange<br />-Controlli contenuto<br />-Segnalibro|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO per Word ed Excel.|[Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)|
|I controlli host seguenti:<br /><br /> -   XMLMappedRange<br />-XMLNode<br />-XMLNodes|Progetti a livello di documento.|[Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)|
|Distribuzione di più progetti.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO.|[Procedura dettagliata: Distribuire più soluzioni Office in un singolo programma di installazione di ClickOnce](https://msdn.microsoft.com/051223c0-4082-4799-b78b-a4763a9def55)|
|Aree di modulo di Outlook.|Progetti di componente aggiuntivo VSTO per Outlook.|[Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)|
|Azioni di post-distribuzione.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO.|[Procedura dettagliata: Copia un documento al computer dell'utente finale dopo un'installazione ClickOnce](https://msdn.microsoft.com/100090f7-bc63-4152-b3e1-19b48bc27466)|
|Personalizzazioni della barra multifunzione.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO per le applicazioni seguenti:<br /><br /> -   Excel<br />-InfoPath (InfoPath 2013 e InfoPath 2010 solo)<br />-   Outlook<br />-   PowerPoint<br />-Progetto<br />-Visio<br />-   Word|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|
|Programma di creazione documenti visivi.|Progetti a livello di documento.|[Progetti di Office in ambiente di Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Vedere anche
- [Iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
