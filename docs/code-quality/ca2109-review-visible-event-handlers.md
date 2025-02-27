---
title: 'CA2109: Controllare i gestori di eventi visibili'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de5ab1fac368f1da1ceea39df19b198a22d999c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808289"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Controllare i gestori di eventi visibili

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 È stato rilevato un metodo di gestione eventi pubblico o protetto.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo visibile esternamente di gestione degli eventi presenta un problema di sicurezza che è necessario esaminare.

Non esporre metodi di gestione degli eventi a meno che non assolutamente necessario. Un gestore eventi, un tipo delegato, che richiama il metodo esposto può essere aggiunti a qualsiasi evento, purché il gestore dell'evento sia le firme corrispondano. Gli eventi possono potenzialmente essere generati da qualsiasi codice e spesso vengono generati dal codice altamente attendibile del sistema in risposta alle azioni dell'utente, ad esempio facendo clic su un pulsante. Aggiunta di un controllo di sicurezza a un metodo di gestione degli eventi non impedisce al codice di registrazione di un gestore eventi che richiama il metodo.

 Una richiesta non è possibile proteggere in modo affidabile un metodo richiamato da un gestore eventi. Richieste di sicurezza consentono il codice dai chiamanti non attendibili esaminando i chiamanti nello stack di chiamate. Il codice che aggiunge un gestore eventi a un evento non è necessariamente presente nello stack di chiamate durante l'esecuzione dei metodi del gestore eventi. Pertanto, lo stack di chiamate potrebbe contenere solo altamente attendibili ai chiamanti quando viene richiamato il metodo del gestore eventi. In questo modo le richieste effettuate dal metodo del gestore eventi abbia esito positivo. Inoltre, le autorizzazioni richieste potrebbero essere asserite quando viene richiamato il metodo. Per questi motivi, il rischio di non correggere una violazione di questa regola può essere valutato solo dopo aver esaminato il metodo di gestione degli eventi. Durante la revisione del codice, tenere presente quanto segue:

- Il gestore eventi esegue tutte le operazioni pericolose o vulnerabile, ad esempio di asserzione di autorizzazioni o l'eliminazione dell'autorizzazione di codice non gestito?

- Quali sono le minacce alla sicurezza da e verso il codice, poiché possono essere eseguiti in qualsiasi momento con solo altamente attendibili i chiamanti nello stack?

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, esaminare il metodo e valutare quanto segue:

- Sarà possibile rendere il metodo di gestione degli eventi non pubblici?

- È possibile spostare tutte le funzionalità pericolose fuori del gestore eventi?

- Se una richiesta di sicurezza viene imposto, possa essere eseguita in altro modo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Eliminare un avviso da questa regola solo dopo un'attenta revisione della sicurezza per assicurarsi che il codice non costituisce una minaccia alla sicurezza.

## <a name="example"></a>Esempio
 Il codice seguente viene illustrato un metodo di gestione degli eventi che possa essere usati in modo improprio da codice dannoso.

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>
- <xref:System.EventArgs?displayProperty=fullName>