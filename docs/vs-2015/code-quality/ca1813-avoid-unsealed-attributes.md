---
title: 'CA1813: Evitare attributi unsealed | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0624ff6ed890b6f0c14f3a03fe774c422334737d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690285"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Evitare attributi unsealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Category|Microsoft.Performance|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico eredita da <xref:System.Attribute?displayProperty=fullName>, non è astratta e non è bloccato (`NotInheritable` in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 La libreria di classi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] fornisce metodi per recuperare attributi personalizzati. Per impostazione predefinita, questi metodi eseguono ricerche nella gerarchia di ereditarietà attributo; ad esempio <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> Cerca il tipo di attributo specificato o qualsiasi tipo di attributo che estende il tipo di attributo specificato. Utilizzo di attributi sealed Elimina la ricerca nella gerarchia di ereditarietà e può migliorare le prestazioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere sealed il tipo di attributo o renderla astratta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. È consigliabile farlo solo se si sta definendo una gerarchia dell'attributo e non è possibile bloccare l'attributo o renderla astratta.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un attributo personalizzato che soddisfa questa regola.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Contrassegnare gli attributi con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Vedere anche
 [Attributi](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
