---
title: "CA2224: Eseguire l'override di Equals all'overload dell'operatore \"uguale a\""
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fa6bfa5b590d330d791eb8c735099e619ffaf3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541910"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Eseguire l'override di Equals all'overload dell'operatore "uguale a"

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un tipo pubblico implementa l'operatore di uguaglianza, ma non esegue l'override <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola

L'operatore di uguaglianza deve essere un modo pratico sintatticamente per accedere alla funzionalità del <xref:System.Object.Equals%2A> (metodo). Se si implementa l'operatore di uguaglianza, la logica deve essere identica a quello di <xref:System.Object.Equals%2A>.

Il compilatore c# genera un avviso se il codice viola questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, è necessario rimuovere l'implementazione dell'operatore di uguaglianza oppure eseguire l'override <xref:System.Object.Equals%2A> e dispone di due metodi restituiscono gli stessi valori. Se l'operatore di uguaglianza non introduce un comportamento incoerente, è possibile correggere la violazione, fornendo un'implementazione di <xref:System.Object.Equals%2A> che chiama il <xref:System.Object.Equals%2A> metodo nella classe di base.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se l'operatore di uguaglianza restituisce lo stesso valore come l'implementazione ereditata di <xref:System.Object.Equals%2A>. Gli esempi in questo articolo includono un tipo che è stato possibile eliminare in modo sicuro un avviso da questa regola.

## <a name="examples-of-inconsistent-equality-definitions"></a>Esempi di definizioni di uguaglianza incoerenti

Nell'esempio seguente viene illustrato un tipo con definizioni incoerenti dell'uguaglianza. `BadPoint` la modifica del significato di uguaglianza, fornendo un'implementazione personalizzata dell'operatore di uguaglianza, ma non esegue l'override <xref:System.Object.Equals%2A> in modo che si comporta in modo identico.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Il codice seguente verifica il comportamento di `BadPoint`.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

Questo esempio produce il seguente output:

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

Nell'esempio seguente viene illustrato un tipo che tecnicamente viola questa regola, ma non si comporta in modo incoerente.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Il codice seguente verifica il comportamento di `GoodPoint`.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

Questo esempio produce il seguente output:

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>Esempio di classe

Nell'esempio seguente viene illustrata una classe (tipo riferimento) che violano questa regola.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

Nell'esempio seguente la violazione viene corretta eseguendo l'override <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Esempio di struttura

L'esempio seguente illustra una struttura (tipo di valore) che violano questa regola:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

Nell'esempio seguente la violazione viene corretta eseguendo l'override <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Regole correlate

[CA1046: Non eseguire l'overload dell'operatore di uguaglianza sui tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)