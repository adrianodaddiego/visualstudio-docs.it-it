---
title: 'CA2146: I tipi devono essere Critical almeno come le interfacce e i tipi base relativi'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01a8a5609394f0dd428066e32fb425a2abb486c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542053"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: I tipi devono essere Critical almeno come le interfacce e i tipi base relativi

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo trasparente è derivato da un tipo contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> o il <xref:System.Security.SecurityCriticalAttribute>, o un tipo contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo deriva da un tipo contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata quando un tipo derivato dispone di un attributo di trasparenza di sicurezza che non è critico come il tipo di base o l'interfaccia implementata. Solo i tipi critici possono derivare da tipi di base critici o implementare interfacce critiche e solo tipi critici o critici per la sicurezza possono derivare da tipi di base critici per la sicurezza o implementare interfacce critiche per la sicurezza. Le violazioni di questa regola di trasparenza di livello 2 comportare un <xref:System.TypeLoadException> per i tipi derivati.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere questa violazione, contrassegnare il tipo derivato o di implementazione con un attributo di trasparenza è critical almeno come il tipo di base o interfaccia.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]