---
title: "CA1046: Non eseguire l'overload dell'operatore \"uguale a\" per i tipi di riferimento"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f9304fcd86a9b36a729b1436fe16471b449ac0d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778723"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento

|||
|-|-|
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo di riferimento pubblica pubblica o annidata esegue l'overload dell'operatore di uguaglianza.

## <a name="rule-description"></a>Descrizione della regola
 Per i tipi di riferimento, l'implementazione predefinita dell'operatore di uguaglianza è quasi sempre corretta. Per impostazione predefinita, i due riferimenti sono uguali solo se puntano allo stesso oggetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'implementazione dell'operatore di uguaglianza.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola quando il tipo di riferimento si comporta come un tipo di valore predefinito. Se è significativo per eseguire operazioni di addizione o sottrazione nelle istanze del tipo, è probabilmente corretta implementare l'operatore di uguaglianza e sopprimere la violazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato il comportamento predefinito quando si confrontano due riferimenti.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Esempio

La seguente applicazione confronta alcuni riferimenti.

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

Questo esempio produce il seguente output:

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>Regole correlate

[CA1013: Overload di operatore equals all'overload degli operatori di addizione e sottrazione](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators)