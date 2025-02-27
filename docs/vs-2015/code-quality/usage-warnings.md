---
title: Avvisi di utilizzo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 679c12eb99e3cad7486384999a2393e09dbd277f
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "59001175"
---
# <a name="usage-warnings"></a>avvisi di utilizzo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avvisi di utilizzo supportano l'utilizzo corretto di .NET Framework.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Regola|Descrizione|  
|----------|-----------------|  
|[CA1801: Controllare i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)|Una firma di metodo include un parametro non utilizzato nel corpo del metodo.|  
|[CA1806: Non ignorare i risultati dei metodi](../code-quality/ca1806-do-not-ignore-method-results.md)|Un nuovo oggetto viene creato, ma non viene mai utilizzato oppure viene chiamato un metodo che crea e restituisce una nuova stringa e la nuova stringa non viene mai utilizzata oppure un metodo COM o P/Invoke restituisce un HRESULT o un codice di errore che non viene mai utilizzato.|  
|[CA1816: Chiamare GC. SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Un metodo che è un'implementazione di Dispose non chiama GC. SuppressFinalize; o un metodo che non è un'implementazione di Dispose chiama GC. SuppressFinalize; o un metodo chiama GC. SuppressFinalize e passa un valore diverso da this (Me in Visual Basic).|  
|[CA2200: Eseguire il rethrow per conservare i dettagli dello stack](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Viene nuovamente generata un'eccezione e l'eccezione viene specificato in modo esplicito nell'istruzione throw. Se viene nuovamente generata un'eccezione, specificando l'eccezione nell'istruzione throw, l'elenco di chiamate al metodo tra il metodo originale che ha generato l'eccezione e il metodo corrente viene perso.|  
|[CA2201: Non generare tipi di eccezione riservati](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Ciò rende difficile da rilevare ed eseguire il debug dell'errore originale.|  
|[CA2202: Non eliminare oggetti più volte](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Un'implementazione di metodo contiene percorsi del codice che potrebbero comportare più chiamate a System.IDisposable.Dispose o a un equivalente di Dispose (ad esempio un metodo Close() per alcuni tipi) sullo stesso oggetto.|  
|[CA2204: Valori letterali devono essere digitati correttamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Una stringa letterale in un corpo del metodo contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.|  
|[CA2205: Utilizzare equivalenti gestiti dell'API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Un platform invoke viene definito metodo e un metodo con la funzionalità equivalente è presente nella libreria di classi .NET Framework.|  
|[CA2207: Inizializzare i campi statici del tipo di valore inline](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Un tipo di valore dichiara un costruttore statico esplicito. Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando vengono dichiarati e rimuovere il costruttore statico.|  
|[CA2208: Creare un'istanza di eccezioni di argomento correttamente](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Viene effettuata una chiamata al costruttore predefinito (senza parametri) di un tipo di eccezione che corrisponde a o deriva da ArgumentException oppure viene passato un argomento stringa non corretto a un costruttore con parametri di un tipo di eccezione che corrisponde a o deriva da ArgumentException.|  
|[CA2211: I campi non costanti non devono essere visibili](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|I campi statici che non sono costanti né in sola lettura non sono thread-safe. Accesso a tale campo deve essere controllato attentamente e richiede tecniche di programmazione avanzate per la sincronizzazione dell'accesso all'oggetto classe.|  
|[CA2212: Non contrassegnare componenti serviti con WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Un metodo in un tipo che eredita da ServicedComponent è contrassegnato con WebMethodAttribute. Poiché WebMethodAttribute e un metodo ServicedComponent presentano comportamenti e requisiti di contesto e flusso di transazioni in conflitto tra loro, il comportamento del metodo non sarà corretto in determinati scenari.|  
|[CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Un tipo che implementa System.IDisposable dichiara i campi di tipi che implementano anch'essi IDisposable. Il metodo Dispose del campo non viene chiamato dal metodo Dispose del tipo dichiarante.|  
|[CA2214: Non chiamare metodi sottoponibili a override nei costruttori](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non è stata eseguita.|  
|[CA2215: I metodi Dispose devono chiamare dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Se un tipo eredita da un tipo eliminabile, deve chiamare il metodo Dispose del tipo di base dal proprio metodo Dispose.|  
|[CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Un tipo che implementa System. IDisposable e include campi che suggeriscono l'utilizzo delle risorse non gestite, non implementare un finalizzatore, come descritto da Object. Finalize.|  
|[CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Un'enumerazione visibile esternamente è contrassegnata con FlagsAttribute e presenta uno o più valori che non sono potenze di due o una combinazione di altri valori definiti nell'enumerazione.|  
|[CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode restituisce un valore, basato sull'istanza corrente, appropriato per algoritmi di hash e strutture dei dati come una tabella hash. Due oggetti dello stesso tipo e uguali devono restituire lo stesso codice hash.|  
|[CA2219: Non generare eccezioni in clausole di eccezione](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Quando un'eccezione viene generata in una clausola finally o in una clausola fault, la nuova eccezione nasconde l'eccezione attiva. Quando un'eccezione viene generata in una clausola filter, il runtime rileva l'eccezione automaticamente. Ciò rende difficile da rilevare ed eseguire il debug dell'errore originale.|  
|[CA2220: I finalizzatori devono chiamare il finalizzatore di classe di base](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. A tale scopo, i tipi devono chiamare il metodo Finalize della classe di base nel proprio metodo Finalize.|  
|[CA2221: I finalizzatori devono essere protetti](../code-quality/ca2221-finalizers-should-be-protected.md)|I finalizzatori devono utilizzare il modificatore di accesso a livello di famiglia.|  
|[CA2222: Non diminuire la visibilità di membri ereditati](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Non modificare il modificatore di accesso per i membri ereditati. La modifica in privato di un membro ereditato non impedisce ai chiamanti di accedere all'implementazione della classe base del metodo.|  
|[CA2223: I membri devono limitarsi al tipo restituito](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Nonostante Common Language Runtime consenta l'utilizzo di tipi restituiti per differenziare membri altrimenti identici, questa funzionalità non è inclusa nella specifica CLS (Common Language Specification) e non è una funzionalità comune dei linguaggi di programmazione .NET.|  
|[CA2224: Override di equals all'overload dell'operatore è uguale a](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Un tipo pubblico implementa l'operatore di uguaglianza, ma non esegue l'override di Object. Equals.|  
|[CA2225: Overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|È stato rilevato un overload di operatore e il metodo alternativo denominato previsto non è stato trovato. Il membro alternativo denominato fornisce l'accesso per la stessa funzionalità dell'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano gli operatori di overload.|  
|[CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Un tipo implementa l'operatore di uguaglianza o disuguaglianza e non implementa l'operatore opposto.|  
|[CA2227: Le proprietà della raccolta devono essere di sola lettura](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Una proprietà di raccolta scrivibile consente a un utente di sostituire la raccolta con una raccolta diversa. Una proprietà di sola lettura interrompe la sostituzione della raccolta ma consente ancora l'impostazione dei singoli membri.|  
|[CA2228: Non fornire formati di risorse non rilasciati](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|File di risorse che sono stati compilati usando versioni non definitive di .NET Framework potrebbero non essere utilizzabili dalle versioni supportate di .NET Framework.|  
|[CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)|Per correggere una violazione di questa regola, implementare il costruttore di serializzazione. Per una classe sealed, rendere il costruttore privato; in caso contrario renderlo protetto.|  
|[CA2230: Utilizzare params per argomenti variabili](../code-quality/ca2230-use-params-for-variable-arguments.md)|Un tipo pubblico o protetto contiene un metodo pubblico o protetto che utilizza la convenzione di chiamata VarArgs anziché la parola chiave params.|  
|[CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Un tipo di valore esegue l'override di Object.Equals, ma non implementa l'operatore di uguaglianza.|  
|[CA2232: Punti di ingresso di Mark Windows Form con STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute indica che il modello di threading COM per l'applicazione è un apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente.|  
|[CA2233: Evitare l'overflow delle operazioni](../code-quality/ca2233-operations-should-not-overflow.md)|Operazioni aritmetiche non devono essere eseguite solo dopo aver convalidato gli operandi, assicurarsi che il risultato dell'operazione non è compreso nell'intervallo di valori possibili per i tipi di dati coinvolti.|  
|[CA2234: Passare oggetti System. Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Viene effettuata una chiamata a un metodo che dispone di un parametro di stringa il cui nome contiene "uri", "URI", "urn", "URN", "url" o "URL".  Il tipo dichiarante del metodo contiene un overload del metodo corrispondente con un parametro System.Uri.|  
|[CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile.|  
|[CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Per correggere una violazione di questa regola, chiamare il costruttore di serializzazione o il metodo GetObjectData del tipo di base dal costruttore o dal metodo del tipo derivato corrispondente.|  
|[CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Per essere riconosciuti da common language runtime come serializzabili, tipi devono essere contrassegnati con l'attributo SerializableAttribute anche se il tipo Usa una routine di serializzazione personalizzata tramite l'implementazione dell'interfaccia ISerializable.|  
|[CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Un metodo che gestisce un evento di serializzazione non dispone della visibilità, del tipo restituito o della firma corretta.|  
|[CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Un tipo ha un campo contrassegnato con l'attributo OptionalFieldAttribute e il tipo non fornisce i metodi di gestione degli eventi di deserializzazione.|  
|[CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)|Per correggere una violazione di questa regola, impostare il metodo GetObjectData come visibile e sottoponibile a override e assicurarsi che tutti i campi di istanza sono inclusi nel processo di serializzazione o contrassegnati in modo esplicito con l'attributo NonSerializedAttribute.|  
|[CA2241: Fornire argomenti corretti ai metodi di formattazione](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|L'argomento format passato a Format non contiene un elemento di formato che corrisponde a ogni argomento di oggetto, o viceversa.|  
|[CA2242: Testare i valori NaN in modo corretto](../code-quality/ca2242-test-for-nan-correctly.md)|Questa espressione consente di testare un valore rispetto a Single.Nan o Double.Nan. Utilizzare Single.IsNan(Single) o Double.IsNan(Double) per testare il valore.|  
|[CA2243: Valori letterali stringa di attributo devono essere analizzate correttamente](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Parametro dell'attributo del valore letterale stringa non analizza correttamente per un URL, un GUID o una versione.|
