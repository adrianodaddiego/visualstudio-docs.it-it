---
title: 'CA1059: I membri non devono esporre tipi concreti specifici'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ea06de685d5e73f55e3fa8921d6785bc222da87
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788624"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: I membri non devono esporre tipi concreti specifici

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un membro visibile esternamente è un certo tipo concreto o espone tipi concreti specifici tramite uno dei relativi parametri o valore restituito. Attualmente, questa regola segnala l'esposizione dei tipi concreti seguenti:

- Un tipo derivato da <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo concreto è un tipo con implementazione completa, pertanto è possibile crearne un'istanza. Per consentire un utilizzo esteso del membro, sostituire il tipo concreto con l'interfaccia suggerita. In questo modo il membro accettare qualsiasi tipo che implementa l'interfaccia oppure essere usato in cui è previsto un tipo che implementa l'interfaccia.

 La tabella seguente elenca i tipi concreti di destinazione e le relative sostituzioni consigliate.

|Tipo concreto|Sostituzione|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Tramite l'interfaccia consente di disaccoppiare il membro da un'implementazione specifica di un'origine dati XML.|

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il tipo concreto per l'interfaccia suggerita.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un messaggio da questa regola se la funzionalità specifica fornita dal tipo concreto è obbligatorio.

## <a name="related-rules"></a>Regole correlate
 [CA1011: Considerare il passaggio di tipi di base come parametri](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)