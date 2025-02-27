---
title: 'CA1027: Contrassegnare le enumerazioni con FlagsAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6603e0869a9eb7947735c52a4c438b39d64b9140
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964396"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Contrassegnare le enumerazioni con FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 I valori di enumerazione pubblica sono potenze di due o combinazioni di altri valori definiti nell'enumerazione, e il <xref:System.FlagsAttribute?displayProperty=fullName> attributo non è presente. Per ridurre i falsi positivi, questa regola non segnala una violazione per enumerazioni associate a valori contigui.

## <a name="rule-description"></a>Descrizione della regola
 Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Applicare <xref:System.FlagsAttribute> a un'enumerazione quando le relative costanti denominate possono essere combinate. Si consideri, ad esempio, un'enumerazione dei giorni della settimana in un'applicazione che tiene traccia delle risorse del giorno in cui sono disponibili. Se la disponibilità di ogni risorsa viene codificata utilizzando l'enumerazione con <xref:System.FlagsAttribute> present, qualsiasi combinazione di giorni può essere rappresentato. Senza l'attributo può essere rappresentato un solo giorno della settimana.

 Per i campi che archiviano le enumerazioni combinable, singoli valori di enumerazione sono considerati come gruppi di bit del campo. Di conseguenza, questi campi sono talvolta detti *campi di bit*. Per combinare i valori di enumerazione per l'archiviazione in un campo di bit, usare gli operatori booleani condizionali. Per testare un campo di bit per determinare se è presente un valore di enumerazione specifico, usare gli operatori logici booleani. Per un campo di bit archiviare e recuperare valori di enumerazione correttamente, ogni valore definito nell'enumerazione deve essere una potenza di due. In caso contrario, gli operatori logici booleani non sarà in grado di estrarre i singoli valori di enumerazione che sono archiviati nel campo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere <xref:System.FlagsAttribute> all'enumerazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se non si desidera valori di enumerazione da combinabili.

## <a name="example"></a>Esempio
 Nell'esempio riportato di seguito `DaysEnumNeedsFlags` è un'enumerazione che soddisfi i requisiti per l'uso di <xref:System.FlagsAttribute>, ma non è presente. Il `ColorEnumShouldNotHaveFlag` enumerazione non ha i valori che sono potenze di due, ma specifica erroneamente <xref:System.FlagsAttribute>. Questa condizione viola regola [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.FlagsAttribute?displayProperty=fullName>
