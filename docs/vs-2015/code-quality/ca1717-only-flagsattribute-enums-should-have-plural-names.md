---
title: 'CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aa0c51eaa10503a92c21960dc3dd074aa7541f5c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694952"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un'enumerazione visibile esternamente termina con una parola plurale e l'enumerazione non è contrassegnato con il <xref:System.FlagsAttribute?displayProperty=fullName> attributo.

## <a name="rule-description"></a>Descrizione della regola
 Convenzioni di denominazione indicano che un nome plurale per un'enumerazione indica che è possibile specificare contemporaneamente più di un valore dell'enumerazione. Il <xref:System.FlagsAttribute> indica ai compilatori di enumerazione deve essere considerato un campo di bit che consente di eseguire operazioni bit per bit su enumerazione.

 Se solo un valore di un'enumerazione può essere specificato in un momento, il nome dell'enumerazione deve essere una parola singola. Ad esempio, un'enumerazione che definisce i giorni della settimana potrebbe essere destinata all'uso in un'applicazione in cui è possibile specificare più giorni. Questa enumerazione deve avere il <xref:System.FlagsAttribute> e potrebbe essere denominata "Days". Un'enumerazione simile che consenta solo un singolo giorno specificare non include l'attributo e può essere chiamato 'Day'.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce il tempo necessario per l'apprendimento di una nuova libreria di software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Cambiare il nome dell'enumerazione di una parola singolare oppure aggiungere il <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il nome termina con una singola parola.

## <a name="related-rules"></a>Regole correlate
 [CA1714: Le enumerazioni con Flags devono avere nomi plurali](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.FlagsAttribute?displayProperty=fullName> [Progettazione di enum](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
