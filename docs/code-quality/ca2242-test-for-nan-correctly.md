---
title: 'CA2242: Testare i valori NaN in modo corretto'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 43c2dd1f6a23c3df4d77207efb49531b97b3b381
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541402"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testare i valori NaN in modo corretto

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un valore rispetto a test di un'espressione <xref:System.Single.NaN?displayProperty=fullName> o <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Double.NaN?displayProperty=fullName>, che rappresenta non un numero, viene generato quando un'operazione aritmetica è definita. Qualsiasi espressione che consente di verificare l'uguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `false`. Qualsiasi espressione che consente di verificare la disuguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `true`.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione della regola e determinare se un valore rappresenta con precisione <xref:System.Double.NaN?displayProperty=fullName>, usare <xref:System.Single.IsNaN%2A?displayProperty=fullName> o <xref:System.Double.IsNaN%2A?displayProperty=fullName> per testare il valore.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra due espressioni che testano erroneamente un valore rispetto <xref:System.Double.NaN?displayProperty=fullName> e un'espressione che utilizza correttamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> per testare il valore.

 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]