---
title: 'CA1058: I tipi non devono estendere tipi di base specifici | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1ce67a70b6cbe955ef13bf6475a672bcbb687d95
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046539"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: I tipi non devono estendere tipi di base specifici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente estende tipi di base specifici. Attualmente, questa regola segnala i tipi che derivano dai tipi seguenti:

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
 Per la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versione 1, era consigliabile derivare nuove eccezioni da <xref:System.ApplicationException>. La raccomandazione è stato modificato e nuove eccezioni devono derivare da <xref:System.Exception?displayProperty=fullName> o una delle sue sottoclassi nel <xref:System> dello spazio dei nomi.

 Non creare una sottoclasse di <xref:System.Xml.XmlDocument> se si desidera creare una vista XML di un'origine dati o del modello di oggetto sottostante.

### <a name="non-generic-collections"></a>Raccolte non generiche
 Usare e/o di estendere le raccolte generiche, laddove possibile. Non si estendono le raccolte non generiche nel codice, a meno che non sono stati inviati in precedenza.

 **Esempi di utilizzo non corretto**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Esempi di utilizzo corretto**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, derivare il tipo da un tipo di base diverso o una raccolta generica.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola per le violazioni sulle <xref:System.ApplicationException>. È possibile eliminare un avviso da questa regola per le violazioni su <xref:System.Xml.XmlDocument>. È possibile eliminare un avviso relativo a una raccolta non generiche se il codice è stato rilasciato in precedenza.
