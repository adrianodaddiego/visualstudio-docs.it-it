---
title: 'CA1054: I parametri URI non devono essere stringhe'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 659ea1008cd70571d035d0b178d01587c6b2ba0d
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842062"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: I parametri URI non devono essere stringhe

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo dichiara un metodo con un parametro di stringa il cui nome contiene "uri", "Uri", "urn", "Urn", "url" o "Url" e il tipo non dichiara un overload corrispondente che accetta un <xref:System.Uri?displayProperty=fullName> parametro.

Per impostazione predefinita, questa regola cerca solo tipi visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Questa regola il nome del parametro di suddivide in token in base alla convenzione camel e verifica se ogni token uguale a "uri", "Uri", "urn", "Urn", "url" o "Url". Se non esiste una corrispondenza, la regola presuppone che il parametro rappresenti un uniform resource identifier (URI). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. Se un metodo accetta una rappresentazione di stringa di un URI, un overload corrispondente deve essere fornito che accetta un'istanza del <xref:System.Uri> (classe), che fornisce questi servizi in modo sicuro e affidabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare il parametro in un <xref:System.Uri> digitare; si tratta di una modifica sostanziale. In alternativa, fornire un overload del metodo che accetta un <xref:System.Uri> parametro; si tratta di una modifica non sostanziale.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se il parametro non rappresenta un URI.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```ini
dotnet_code_quality.ca1054.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo, `ErrorProne`, che viola la regola e un tipo, `SaferWay`, che soddisfa la regola.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Regole correlate

- [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1055: URI restituiscono valori non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234: Passare oggetti System. Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Stringa chiamano gli overload System. Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)