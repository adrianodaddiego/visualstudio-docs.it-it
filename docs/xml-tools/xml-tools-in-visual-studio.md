---
title: Editor XML e Progettazione schema
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8854aee047fa961c4f0973397cfc2fe6ac6e6ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808171"
---
# <a name="xml-tools-in-visual-studio"></a>Strumenti XML in Visual Studio

*Extensible Markup Language (XML)* è un linguaggio di markup che fornisce un formato per descrivere i dati. XML separa i dati e relativa presentazione con fogli di stile, ad esempio fogli di stile XSL (Extensible Language) e fogli di stile (CSS) associati. Visual Studio comprende strumenti e funzionalità che semplificano l'uso del codice XML, XSLT e degli schemi XML.

## <a name="xml-editor"></a>Editor XML

Il [editor XML](xml-editor.md) consente di modificare i documenti XML. Fornisce sintassi XML completa, controllo, convalida dello schema durante la digitazione, la codifica a colori e IntelliSense. Se viene fornita una definizione dello schema o del tipo di documento, essa verrà usata da IntelliSense per elencare gli elementi e gli attributi disponibili.

Le funzionalità aggiuntive comprendono:

- Supporto per i frammenti XML, inclusi i frammenti generati da uno schema

- Documentare la struttura in modo che gli elementi possono essere espansa e compressa

- La possibilità di eseguire le trasformazioni XSLT e per visualizzare i risultati come testo, XML o HTML

- La possibilità di generare schemi XML Schema definition language (XSD) dal documento di istanza XML

- Supporto per la modifica di fogli di stile XSLT, incluso il supporto di IntelliSense

- XML Schema Explorer

## <a name="xml-schema-designer"></a>Progettazione XML Schema

Il [Progettazione XML Schema](xml-schema-designer.md) è integrato con Visual Studio e l'editor XML per consentire di lavorare con schemi XML schema definition language (XSD).

## <a name="xslt-debugging"></a>Debug XSLT

Visual Studio supporta [debug di fogli di stile XSLT](../xml-tools/debugging-xslt.md). Usando il debugger, è possibile impostare i punti di interruzione in un foglio di stile XSLT, eseguire l'istruzione del codice di un foglio di stile XSLT e così via.

> [!NOTE]
> Il debugger XSLT è disponibile solo nell'edizione Enterprise di Visual Studio.

## <a name="see-also"></a>Vedere anche

- <xref:System.Xml?displayProperty=fullName>
- [Trasformazioni XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Elaborare dati XML con il modello di dati XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [Modello DOM (Document Object Mode) XML](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [SOM (Schema Object Model) XML](/dotnet/standard/data/xml/xml-schema-object-model-som)