---
title: "CA1026: Evitare l'uso di parametri predefiniti"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5dc7f7e62526050eeabdb91a557bbdf0fbcf6da
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779521"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Evitare l'uso di parametri predefiniti

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente contiene un metodo visibile esternamente che usa un parametro predefinito.

## <a name="rule-description"></a>Descrizione della regola
 I metodi che utilizzano parametri predefiniti sono consentiti con la specifica CLS (Common Language); Tuttavia, la specifica CLS consente ai compilatori di ignorare i valori assegnati a questi parametri. Il codice scritto per i compilatori che ignorano i valori predefiniti dei parametri deve fornire esplicitamente gli argomenti per ogni parametro predefinito. Per mantenere il comportamento desiderato tra diversi linguaggi di programmazione, i metodi che utilizzano parametri predefiniti devono essere sostituiti con overload di metodi che forniscono i parametri predefiniti.

 Il compilatore ignora i valori dei parametri predefiniti per estensioni gestite per C++ durante l'accesso al codice gestito. Il compilatore Visual Basic supporta metodi che hanno parametri predefiniti che utilizzano le [facoltativo](/dotnet/visual-basic/language-reference/modifiers/optional) (parola chiave).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire il metodo che usa i parametri predefiniti con overload di metodi che forniscono i parametri predefiniti.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che usa i parametri predefiniti e i metodi di overload che forniscono una funzionalità equivalente.

 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Vedere anche
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)