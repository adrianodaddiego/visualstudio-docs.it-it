---
title: 'CA2135: Gli assembly di livello 2 non devono contenere LinkDemand'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcd9032d550e79a47941540408dc6e98a15e33f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796718"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Gli assembly di livello 2 non devono contenere LinkDemand

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una classe o membro di classe Usa un <xref:System.Security.Permissions.SecurityAction> in un'applicazione che utilizza una sicurezza di livello 2.

## <a name="rule-description"></a>Descrizione della regola
 I LinkDemand sono deprecati nel set di regole per la sicurezza di livello 2. Invece di usare i LinkDemand per applicare la sicurezza in fase di compilazione just-in-time (JIT), contrassegnare i metodi, tipi e i campi con il <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il <xref:System.Security.Permissions.SecurityAction> e contrassegnare il tipo o membro con il <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, il <xref:System.Security.Permissions.SecurityAction> devono essere rimossi e il metodo contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> attributo.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]