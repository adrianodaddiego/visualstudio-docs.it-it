---
title: 'CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bd801e7afc1fa0a4edf043aba560bc4afcdae9de
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682837"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente non sealed fornisce un'implementazione di metodo esplicita di un'interfaccia pubblica e non fornisce un metodo visibile esternamente alternativo con lo stesso nome.

## <a name="rule-description"></a>Descrizione della regola
 Si consideri un tipo di base che implementa in modo esplicito un metodo di interfaccia pubblica. Un tipo che deriva dal tipo di base possa accedere al metodo di interfaccia ereditati solo tramite un riferimento all'istanza corrente (`this` in c#) che viene eseguito il cast all'interfaccia. Se il tipo derivato (esplicitamente) implementa nuovamente il metodo di interfaccia ereditati, l'implementazione di base non saranno più accessibili. La chiamata tramite il riferimento all'istanza corrente richiamerà l'implementazione derivata; In questo modo la ricorsione e un overflow dello stack finale.

 Questa regola non genera un report per un'implementazione esplicita di una violazione <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> quando visibile esternamente `Close()` o `System.IDisposable.Dispose(Boolean)` viene fornito il metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare un nuovo metodo che espone la stessa funzionalità ed è visibile ai tipi derivati oppure passare a un'implementazione non esplicita. Se una modifica di rilievo è accettabile, un'alternativa consiste nel rendere il tipo sealed.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se viene fornito con la stessa funzionalità, ma un nome diverso rispetto al metodo implementato in modo esplicito un metodo visibile esternamente.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `ViolatingBase`, che viola la regola e un tipo, `FixedBase`, che mostra una correzione per la violazione.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Vedere anche
 [Interfacce](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
