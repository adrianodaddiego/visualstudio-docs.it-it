---
title: 'CA2220: I finalizzatori devono chiamare il finalizzatore della classe di base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 034f80c9198ab098070e6642f4a4d96cff1744c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541858"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: I finalizzatori devono chiamare il finalizzatore della classe di base

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un tipo che esegue l'override <xref:System.Object.Finalize%2A?displayProperty=fullName> non chiama il <xref:System.Object.Finalize%2A> metodo nella classe base.

## <a name="rule-description"></a>Descrizione della regola

La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. A tale scopo, i tipi devono chiamare la relativa classe base <xref:System.Object.Finalize%2A> metodo all'interno di proprie <xref:System.Object.Finalize%2A> (metodo). Il compilatore c# aggiunge automaticamente la chiamata al finalizzatore della classe base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, chiamare il tipo di base <xref:System.Object.Finalize%2A> metodo di <xref:System.Object.Finalize%2A> (metodo).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola. Alcuni compilatori destinati a common language runtime inserire una chiamata a finalizzatore del tipo di base in Microsoft intermediate language (MSIL). Se viene segnalato un avviso da questa regola, il compilatore di non inserire la chiamata e aggiungerla al codice.

## <a name="example"></a>Esempio

Nell'esempio Visual Basic seguente viene illustrato un tipo `TypeB` che chiama correttamente la <xref:System.Object.Finalize%2A> metodo nella classe base.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Vedere anche

- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)