---
title: avvisi di prestazioni
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d44c9a4a5c59907c527c47523c6c758adaf7ee51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825494"
---
# <a name="performance-warnings"></a>avvisi di prestazioni
Gli avvisi di prestazioni supportano applicazioni e librerie ad alte prestazioni.

## <a name="in-this-section"></a>In questa sezione

| Regola | Descrizione |
| - | - |
| [CA1800: Non eseguire il cast inutilmente](../code-quality/ca1800-do-not-cast-unnecessarily.md) | I cast duplicati comportano una riduzione delle prestazioni, in particolare quando i cast vengono eseguiti in istruzioni di iterazione compatte. |
| [CA1801: Controllare i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md) | Una firma di metodo include un parametro non utilizzato nel corpo del metodo. |
| [CA1802: Usare valori letterali dove appropriato](../code-quality/ca1802-use-literals-where-appropriate.md) | Un campo viene dichiarato static e read-only (Shared e ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e viene inizializzata con un valore calcolabile in fase di compilazione. Poiché il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione in una variabile const (Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) in modo che il valore viene calcolato in fase di compilazione anziché in fase di esecuzione. |
| [CA1804: Rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md) | Le variabili locali inutilizzate e le assegnazioni non necessarie comportano un aumento delle dimensioni dell'assembly e una riduzione delle prestazioni. |
| [CA1806: Non ignorare i risultati dei metodi](../code-quality/ca1806-do-not-ignore-method-results.md) | Un nuovo oggetto viene creato ma mai usato, viene chiamato un metodo che crea e restituisce una nuova stringa e la nuova stringa non viene mai usata, o un metodo Component Object Model (COM) o P/Invoke restituisce un codice di errore o HRESULT che non viene mai usato. |
| [CA1809: Evitare un numero eccessivo di variabili locali](../code-quality/ca1809-avoid-excessive-locals.md) | Un'ottimizzazione comune delle prestazioni consiste nell'archiviare un valore in un registro del processore anziché in memoria. Tale procedura è definita "registrazione del valore".  Per aumentare la probabilità che tutte le variabili locali siano registrate, limitare il numero di variabili a 64. |
| [CA1810: Inizializzare i campi statici del tipo di riferimento inline](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md) | Quando un tipo dichiara un costruttore statico esplicito, tramite il compilatore JIT (Just-In-Time) viene aggiunto un controllo a ogni metodo statico del tipo e a ogni costruttore di istanza del tipo per assicurare che il costruttore statico sia stato precedentemente chiamato. I controlli dei costruttori statici possono ridurre le prestazioni. |
| [CA1811: Evitare il codice privato](../code-quality/ca1811-avoid-uncalled-private-code.md) | Membro privato o interno (a livello di assembly) non presenta chiamanti nell'assembly, non viene richiamato da common language runtime e non viene richiamato dal delegato. |
| [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md) | Un'istanza di un tipo a livello di assembly non viene creata dal codice nell'assembly. |
| [CA1813: Evitare attributi unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md) | La libreria di classi .NET Framework fornisce metodi per recuperare gli attributi personalizzati. Per impostazione predefinita, questi metodi eseguono ricerche nella gerarchia di ereditarietà dell'attributo. L'utilizzo di attributi sealed elimina la ricerca nella gerarchia di ereditarietà e può migliorare le prestazioni. |
| [CA1814: Preferire matrici di matrici multidimensionali](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md) | Una matrice di matrici è una matrice i cui elementi sono costituiti da matrici. Le matrici che costituiscono gli elementi possono essere di dimensioni diverse, che possono comportare spazio inutilizzato sarà inferiore per alcuni set di dati. |
| [CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md) | Per i tipi di valore, l'implementazione ereditata di Equals utilizza la libreria Reflection e confronta il contenuto di tutti i campi. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti confrontino o ordinino le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare Equals. |
| [CA1816: Chiamare GC. SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md) | Un metodo che è un'implementazione di Dispose non chiama GC. SuppressFinalize oppure un metodo che non è un'implementazione di Dispose chiama GC. SuppressFinalize oppure un metodo chiama GC. SuppressFinalize e passa un valore diverso da ciò (Me in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md) | Le matrici restituite dalle proprietà non sono protette in scrittura, anche se la proprietà è di sola lettura. Affinché la matrice sia protetta da eventuali alterazioni, la proprietà deve restituire una copia della matrice. In genere, gli utenti non comprendono le implicazioni negative sulle prestazioni derivanti dalla chiamata di tale proprietà. |
| [CA1820: Testare le stringhe vuote utilizzando la lunghezza della stringa](../code-quality/ca1820-test-for-empty-strings-using-string-length.md) | Il confronto tra stringhe mediante la proprietà String.Length o il metodo String.IsNullOrEmpty è notevolmente più veloce rispetto all'utilizzo di Equals. |
| [CA1821: Rimuovere i finalizzatori vuoti](../code-quality/ca1821-remove-empty-finalizers.md) | Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto. Un finalizzatore vuoto provoca un sovraccarico aggiuntivo senza alcun vantaggio. |
| [CA1822: Contrassegna i membri come statici](../code-quality/ca1822-mark-members-as-static.md) | I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. Si potrà così ottenere un sensibile miglioramento delle prestazioni per codici sensibili alle prestazioni. |
| [CA1823: Evitare campi privati non utilizzati](../code-quality/ca1823-avoid-unused-private-fields.md) | Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly. |
| [CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | L'attributo NeutralResourcesLanguage indica a ResourceManager la lingua utilizzata per visualizzare le risorse delle impostazioni cultura non associate ad alcun paese per un assembly. Tale approccio migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set. |
