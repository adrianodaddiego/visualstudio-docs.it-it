---
title: 'CA1065: Non generare eccezioni in posizioni non previste'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9dd45410a2c928a0ffbbe827b100edd119cf59f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797483"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Non generare eccezioni in posizioni non previste

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Category|Microsoft.Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un metodo che normalmente non genera eccezioni genera un'eccezione.

## <a name="rule-description"></a>Descrizione della regola

I metodi che non possono generare eccezioni possono essere suddivisi in categorie come indicato di seguito:

- Metodi Get di proprietà

- Metodi della funzione di accesso agli eventi

- Metodi Equals

- Metodi GetHashCode

- Metodi ToString

- Costruttori statici

- Finalizzatori

- Eliminazione dei metodi

- Operatori di uguaglianza

- Operatori di Cast impliciti

Le sezioni seguenti illustrano questi tipi di metodo.

### <a name="property-get-methods"></a>Metodi Get di proprietà

Le proprietà sono fondamentalmente intelligente. Pertanto, devono comportarsi come un campo quanto più possibile. I campi non generano eccezioni ed è opportuno proprietà. Se si dispone di una proprietà che genera un'eccezione, prendere in considerazione un metodo.

Le eccezioni seguenti possono essere generate da un metodo get di proprietà:

- <xref:System.InvalidOperationException?displayProperty=fullName> e tutte le derivazioni (tra cui <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> e tutte le derivazioni

- <xref:System.ArgumentException?displayProperty=fullName> (solo da indicizzare get)

- <xref:System.Collections.Generic.KeyNotFoundException> (solo da indicizzare get)

### <a name="event-accessor-methods"></a>Metodi della funzione di accesso agli eventi

Queste funzioni devono essere semplici operazioni che non generano eccezioni. Un evento non deve generare un'eccezione quando si tenta di aggiungere o rimuovere un gestore eventi.

Le eccezioni seguenti possono essere generate da una funzione di accesso eventi:

- <xref:System.InvalidOperationException?displayProperty=fullName> e tutte le derivazioni (tra cui <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> e tutte le derivazioni

- <xref:System.ArgumentException> i derivati

### <a name="equals-methods"></a>Metodi Equals

Quanto segue **è uguale a** metodi non devono generare eccezioni:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

Un' **è uguale a** metodo dovrebbe restituire `true` o `false` anziché generare un'eccezione. Ad esempio, se non viene passato è uguale a due tipi non corrispondenti deve semplicemente restituire `false` anziché generare un <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Metodi GetHashCode

Quanto segue **GetHashCode** metodi in genere non devono generare eccezioni:

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**GetHashCode** deve sempre restituire un valore. In caso contrario, è possibile perdere gli elementi nella tabella hash.

Le versioni di **GetHashCode** che accettano un argomento può generare un <xref:System.ArgumentException>. Tuttavia **Object. GetHashCode** non deve mai generare un'eccezione.

### <a name="tostring-methods"></a>Metodi ToString

Il debugger usa <xref:System.Object.ToString%2A?displayProperty=fullName> per consentire di visualizzare informazioni sugli oggetti in formato stringa. Pertanto **ToString** non dovrebbe modificare lo stato di un oggetto, e non dovrà generare eccezioni.

### <a name="static-constructors"></a>Costruttori statici

Generazione di eccezioni da un costruttore statico, fa sì che il tipo sarà inutilizzabile nel dominio dell'applicazione corrente. È consigliabile utilizzare un buon motivo (ad esempio un problema di sicurezza) per generare un'eccezione da un costruttore statico.

### <a name="finalizers"></a>Finalizzatori

Generare un'eccezione da un finalizzatore fa sì che CLR a fallire, che elimina il processo. Pertanto, la generazione di eccezioni in un finalizzatore deve essere sempre evitata.

### <a name="dispose-methods"></a>Eliminazione dei metodi

Oggetto <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo non deve generare un'eccezione. Dispose viene spesso definito come parte della logica di pulizia in un `finally` clausola. Pertanto, in modo esplicito un'eccezione dal metodo Dispose impone all'utente di aggiungere la gestione delle eccezioni di `finally` clausola.

Il **Dispose (false)** percorso di codice non dovrebbe mai generare eccezioni, poiché Dispose viene quasi sempre chiamato da un finalizzatore.

### <a name="equality-operators--"></a>Gli operatori di uguaglianza (= =,! =)

Come i metodi Equals, devono restituire gli operatori di uguaglianza `true` o `false`e non devono generare eccezioni.

### <a name="implicit-cast-operators"></a>Operatori di Cast impliciti

Poiché l'utente è spesso a conoscenza che è stato chiamato un operatore cast implicito, un'eccezione generata dall'operatore di cast implicito è imprevista. Di conseguenza, nessuna eccezione devono essere generata dagli operatori di cast impliciti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per il getter di proprietà, di modificare la logica in modo che non sia più associata generare un'eccezione o modificare la proprietà in un metodo.

Per tutti gli altri metodo tipi elencati in precedenza, modificare la logica in modo che non è più necessario generare un'eccezione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Se la violazione è stata causata da una dichiarazione di eccezione anziché un'eccezione generata, è possibile eliminare un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate

- [CA2219: Non generare eccezioni in clausole di eccezione](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Vedere anche

- [Avvisi di progettazione](../code-quality/design-warnings.md)