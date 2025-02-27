---
title: Strumenti XML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 906f08c0020eb288c1bcd318327be18dc8d08ca5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695324"
---
# <a name="xml-tools-in-visual-studio"></a>Strumenti XML in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extensible Markup Language (XML) * è un linguaggio di markup che fornisce un formato per descrivere i dati. Offre una maggiore precisione per le dichiarazioni del contenuto e risultati di ricerca più significativi tra più piattaforme. Il linguaggio XML consente inoltre di separare la presentazione dai dati. Ad esempio, in HTML si usano i tag per indicare al browser di visualizzare i dati in grassetto o corsivo. In XML invece si usano i tag solo per descrivere i dati, ad esempio nome della città, temperatura e pressione barometrica. In XML si usano i fogli di stile, ad esempio XSL (Extensible Stylesheet Language) e CSS (Cascading Style Sheet) per presentare i dati in un browser. XML separa i dati dalla presentazione e dall'elaborazione. In questo modo è possibile presentare ed elaborare i dati come si vuole, applicando fogli di stile e applicazioni diversi.

 XML è un sottoinsieme di SGML ottimizzato per la distribuzione sul Web. È definito dal World Wide Web Consortium (W3C) Questa standardizzazione garantisce che i dati strutturati siano uniformi e indipendenti da applicazioni o fornitori.

 Molte funzionalità di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sono basate su XML. L'argomento seguente descrive gli strumenti e le funzionalità relativi a XML disponibili in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Per altre informazioni, vedere la [Centro per sviluppatori XML](http://go.microsoft.com/fwlink/?LinkID=100176), che fornisce la documentazione più recente, informazioni tecniche, download, newsgroup e altre risorse per gli sviluppatori XML.

## <a name="in-this-section"></a>In questa sezione
 [Uso dei dati XML](../xml-tools/working-with-xml-data.md) esamina il ruolo di XML nei dati di modalità viene gestito in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Debug di XSLT](../xml-tools/debugging-xslt.md) vengono forniti collegamenti ad argomenti sull'uso del debugger di Visual Studio per eseguire il debug di XSLT.

## <a name="reference"></a>Riferimenti
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) espone il [Editor XML](http://go.microsoft.com/fwlink/?LinkId=228249) analizzato albero tramite [perché](http://go.microsoft.com/fwlink/?LinkId=228250) per tutti i documenti XML.

 [Riferimento agli standard XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) fornisce informazioni sulle tecnologie XML, tra cui XML, definizione DTD (Document Type Definition), il linguaggio XML Schema definition (XSD) e XSLT.

 <xref:System.Xml?displayProperty=fullName> Descrive le classi e altri elementi che costituiscono il <xref:System.Xml> dello spazio dei nomi e vengono forniti collegamenti a informazioni più dettagliate su ogni elemento.

 <xref:System.Xml.Serialization?displayProperty=fullName> Descrive le classi e altri elementi che costituiscono il <xref:System.Xml.Serialization> dello spazio dei nomi e vengono forniti collegamenti a informazioni più dettagliate su ogni elemento.

## <a name="related-sections"></a>Sezioni correlate
 [Oggetto del modello DOM (Document XML)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) descrive il modo in cui il <xref:System.Xml.XmlDocument> e le relative classi associate conformano a W3C Document Object Model (Core) livello 1 e specifiche per il supporto dello spazio dei nomi di livello 2.

 [La lettura del XML con XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) descrive il modo in cui il <xref:System.Xml.XmlReader> fornisce l'accesso di sola lettura e unico e in modalità forward ai dati XML tramite un flusso XML.

 [La scrittura di XML con XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) descrive il modo in cui il <xref:System.Xml.XmlWriter> forward, forward-only, modo per generare flussi XML e consente di compilare documenti XML conformi allo standard W3C.

 [Trasformazioni XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) descrive il modo in cui il <xref:System.Xml.Xsl.XslCompiledTransform> classe implementa la raccomandazione XSLT 1.0.

 [Elaborare dati XML tramite il modello di dati XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) descrive il modo in cui il <xref:System.Xml.XPath.XPathNavigator> classe può elaborare dati XML archiviati in un <xref:System.Xml.XPath.XPathDocument> o un <xref:System.Xml.XmlDocument> oggetto. La classe <xref:System.Xml.XPath.XPathNavigator> è basata sul modello di dati XQuery 1.0 e XPath 2.0 e può essere usata per spostarsi tra i dati XML e per modificarli.

 [Modello SOM (Schema Object Model) XML](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) descrive le classi usate per la creazione e modifica di schemi XML, fornendo un <xref:System.Xml.Schema.XmlSchema> classe per caricare e modificare uno schema.
