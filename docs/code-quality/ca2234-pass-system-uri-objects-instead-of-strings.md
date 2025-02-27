---
title: 'CA2234: Passare oggetti System.Uri invece di stringhe'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6e7f333ae6f9e938261c0f91196120f3376d0388
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841592"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Passare oggetti System.Uri invece di stringhe

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Viene eseguita una chiamata a un metodo che ha un parametro di stringa il cui nome contiene "uri", "Uri", "urn", "Urn", "url" o "Url" e il tipo dichiarante del metodo contiene un overload del metodo corrispondente che ha un <xref:System.Uri?displayProperty=fullName> parametro.

Per impostazione predefinita, questa regola cerca solo metodi visibili esternamente e i tipi, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Un nome di parametro è suddiviso in token in base alla convenzione camel, e quindi ogni token viene controllato per verificare se è uguale a "uri", "Uri", "urn", "Urn", "url" o "Url". Se non esiste una corrispondenza, si presuppone che il parametro rappresenti un uniform resource identifier (URI). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. Il <xref:System.Uri> classe fornisce questi servizi in modo sicuro e affidabile. Quando è possibile scegliere tra due overload che differiscono solo per quanto riguarda la rappresentazione di un URI, l'utente deve scegliere l'overload che accetta un <xref:System.Uri> argomento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, chiamare l'overload che accetta il <xref:System.Uri> argomento.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se il parametro della stringa non rappresenta un URI.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```ini
dotnet_code_quality.ca2234.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (utilizzo). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un metodo, `ErrorProne`, che viola la regola e un metodo `SaferWay`, che chiama correttamente la <xref:System.Uri> overload:

[!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
[!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
[!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA1057: Stringa chiamano gli overload System. Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
- [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055: URI restituiscono valori non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)