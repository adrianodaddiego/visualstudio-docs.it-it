---
title: "CA1043: Usare l'argomento di stringa o integrale per gli indicizzatori | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 643d91ad51e9511bbd4440d2f84fbd441c768a53
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968026"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Usare un argomento di tipo stringa o integrale per gli indicizzatori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene un indicizzatore pubblico o protetto che utilizza un tipo di indice diverso da <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, o <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Gli indicizzatori, ovvero, le proprietà indicizzate, devono utilizzare tipi integer o stringa per l'indice. Questi tipi vengono generalmente usati per indicizzare strutture di dati e aumentano l'usabilità della libreria. Usare il <xref:System.Object> tipo deve essere limitato ai casi in cui non è possibile specificare il tipo specifico di tipo integer o stringa in fase di progettazione. Se la struttura richiede altri tipi per l'indice, verificare che il tipo rappresenta un archivio dati logici. Se non rappresenta un archivio dati logici, utilizzare un metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'indice in un tipo integer o stringa o usare un metodo invece l'indicizzatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo dopo aver considerato con attenzione la necessità per l'indicizzatore non standard.

## <a name="example"></a>Esempio
 L'esempio seguente mostra un indicizzatore che usa un <xref:System.Int32> indice.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1023: Gli indicizzatori non devono essere multidimensionali](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)
