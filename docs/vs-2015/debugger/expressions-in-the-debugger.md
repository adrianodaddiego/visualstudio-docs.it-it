---
title: Espressioni nel Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VBScript
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3999737a2fad04c9b513722ae11608574a72c410
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080741"
---
# <a name="expressions-in-the-debugger"></a>Espressioni nel debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debugger di Visual Studio include analizzatori di espressioni che vengono usati quando si immette un'espressione nella finestra di dialogo **Controllo immediato** , nella finestra **Espressioni di controllo** o **Immediato** . Gli analizzatori di espressioni vengono inoltre usati nella finestra **Punti di interruzione** e in molte altre posizioni all'interno del debugger.  
  
 Le sezioni seguenti forniscono informazioni dettagliate sulle espressioni in linguaggi diversi.  
  
## <a name="f-expressions-are-not-supported"></a>Le espressioni F# non sono supportate  
 Le espressioni F# non sono riconosciute. Se si esegue il debug del codice F#, è necessario tradurre le espressioni nella sintassi C# prima di immetterle in una finestra o finestra di dialogo del debugger. Quando si traducono espressioni da F# a C#, tenere presente che C# usa l'operatore `==` per verificare l'uguaglianza, mentre F# usa il segno `=`singolo.  
  
## <a name="c-expressions"></a>Espressioni C++  
 Per informazioni sull'uso degli operatori di contesto con le espressioni in C++, vedere [Context Operator (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Espressioni non supportate in C#  
  
#### <a name="constructors-destructors-and-conversions"></a>Costruttori, distruttori e conversioni  
 Non è possibile chiamare un costruttore o distruttore per un oggetto, né in modo esplicito, né in modo implicito. La seguente espressione, ad esempio, chiama in modo esplicito un costruttore e genera un messaggio di errore:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Se la destinazione della conversione è una classe, non è possibile chiamare una funzione di conversione. Tale conversione comporta la costruzione di un oggetto. Se, ad esempio, `myFraction` è un'istanza di `CFraction`che definisce l'operatore della funzione di conversione `FixedPoint`, la seguente espressione genera un errore:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Non è possibile chiamare gli operatori new o delete. Non è ad esempio supportata l'espressione seguente:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Macro del preprocessore  
 Le macro del preprocessore non sono supportate nel debugger. Ad esempio, se una costante `VALUE` viene dichiarata come `#define VALUE 3`, non è possibile usare `VALUE` nella finestra **Espressioni di controllo** . Per evitare questa limitazione, sostituire `#define`con enumerazioni e funzioni quando possibile.  
  
### <a name="using-namespace-declarations"></a>uso delle dichiarazioni dello spazio dei nomi  
 Non è possibile usare le dichiarazioni `using namespace` .  Per accedere a una variabile o a un nome di tipo all'esterno di spazio dei nomi corrente, è necessario usare il nome completo.  
  
### <a name="anonymous-namespaces"></a>Spazi dei nomi anonimi  
 Gli spazi dei nomi anonimi non sono supportati. In presenza del codice seguente, non è possibile aggiungere `test` alla finestra Espressioni di controllo:  
  
```cpp  
namespace mars   
{   
    namespace  
    {  
        int test = 0;   
    }   
}   
int main()   
{   
    // Adding a watch on test does not work.   
    mars::test++;   
    return 0;   
}  
  
```  
  
### <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Uso di funzioni intrinseche del debugger per mantenere lo stato  
 Le funzioni intrinseche del debugger consentono di chiamare alcune funzioni C/C++ nelle espressioni senza modificare lo stato dell'applicazione.  
  
 Funzioni intrinseche del debugger:  
  
- Garantite come sicure: l'esecuzione di una funzione intrinseca del debugger non danneggia il processo sottoposto a debug.  
  
- Consentite in tutte le espressioni, anche negli scenari in cui gli effetti collaterali e la valutazione delle funzioni non sono consentiti.  
  
- Supportate negli scenari in cui le chiamate a funzioni regolari non sono possibili, ad esempio il debug di un minidump.  
  
  Le funzioni intrinseche del debugger rendono più pratica la valutazione delle espressioni. Ad esempio, è molto più facile scrivere `strncmp(str, “asd”)` in una condizione del punto di interruzione piuttosto che `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`. )  
  
|Area|Funzioni intrinseche|  
|----------|-------------------------|  
|**Lunghezza delle stringhe**|strlen, wcslen, strnlen, wcsnlen|  
|**Confronto tra stringhe**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Ricerca di stringhe**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Queste funzioni richiedono che il processo sottoposto a debug sia eseguito in Windows 8. Il debug dei file dump generati da un dispositivo Windows 8 richiede inoltre che nel computer Visual Studio sia eseguito Windows 8. Tuttavia, se si esegue il debug di un dispositivo Windows 8 in modalità remota, nel computer Visual Studio può essere eseguito Windows 7.|  
|**Varie**|__log2<br /><br /> Restituisce il logaritmo in base 2 dell'intero specificato, arrotondato all'intero più basso più prossimo.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLI - Espressioni non supportate  
  
- I cast che coinvolgono puntatori o i cast definiti dall'utente non sono supportati.  
  
- Il confronto e l'assegnazione di oggetti non sono supportati.  
  
- Gli operatori di overload di e le funzioni in overload non sono supportati.  
  
- Le conversioni boxing e unboxing non sono supportate.  
  
- L'operatore`Sizeof` non è supportato.  
  
## <a name="c---unsupported-expressions"></a>C# - Espressioni non supportate  
  
### <a name="dynamic-objects"></a>Oggetti dinamici  
 Nelle espressioni del debugger è possibile usare variabili tipizzate staticamente come dinamiche. Quando gli oggetti che implementano <xref:System.Dynamic.IDynamicMetaObjectProvider> vengono valutati nella finestra Espressioni di controllo, viene aggiunto un nodo Visualizzazione dinamica. Il nodo Visualizzazione dinamica mostra i membri dell'oggetto, ma non consente la modifica dei valori dei membri.  
  
 Le funzionalità seguenti degli oggetti dinamici non sono supportate:  
  
- Gli operatori composti `+=`, `-=`, `%=`, `/=`e `*=`  
  
- Molti cast, inclusi cast numerici e cast dell'argomento di tipo  
  
- Chiamate al metodo con più di due argomenti  
  
- Metodi Get di proprietà con più di due argomenti  
  
- Metodi set di proprietà con argomenti  
  
- Assegnazione a un indicizzatore  
  
- Operatori booleani `&&` e `||`  
  
### <a name="anonymous-methods"></a>Metodi anonimi  
 La creazione di nuovi metodi anonimi non è supportata.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - Espressioni non supportate  
  
### <a name="dynamic-objects"></a>Oggetti dinamici  
 Nelle espressioni del debugger è possibile usare variabili tipizzate staticamente come dinamiche. Quando gli oggetti che implementano <xref:System.Dynamic.IDynamicMetaObjectProvider> vengono valutati nella finestra Espressioni di controllo, viene aggiunto un nodo Visualizzazione dinamica. Il nodo Visualizzazione dinamica mostra i membri dell'oggetto, ma non consente la modifica dei valori dei membri.  
  
 Le funzionalità seguenti degli oggetti dinamici non sono supportate:  
  
- Gli operatori composti `+=`, `-=`, `%=`, `/=`e `*=`  
  
- Molti cast, inclusi cast numerici e cast dell'argomento di tipo  
  
- Chiamate al metodo con più di due argomenti  
  
- Metodi Get di proprietà con più di due argomenti  
  
- Metodi set di proprietà con argomenti  
  
- Assegnazione a un indicizzatore  
  
- Operatori booleani `&&` e `||`  
  
### <a name="local-constants"></a>Costanti locali  
 Le costanti locali non sono supportate.  
  
### <a name="import-aliases"></a>Alias di importazione  
 Gli alias di importazione non sono supportati.  
  
### <a name="variable-declarations"></a>Dichiarazione di variabili  
 Non è possibile dichiarare nuove variabili esplicite nelle finestre del debugger. È invece possibile assegnare un valore a una variabile implicita nella finestra **Controllo immediato** . Queste variabili implicite hanno un ambito limitato alla sessione di debug e non sono accessibili all'esterno del debugger. L'istruzione `o = 5` , ad esempio, crea in modo implicito una nuova variabile `o` alla quale assegna il valore 5. Tali variabili implicite sono di tipo **Object** , a meno che il tipo non possa essere dedotto dal debugger.  
  
### <a name="unsupported-keywords"></a>Parole chiave non supportate  
  
- `AddressOf`  
  
- `End`  
  
- `Error`  
  
- `Exit`  
  
- `Goto`  
  
- `On Error`  
  
- `Resume`  
  
- `Return`  
  
- `Select/Case`  
  
- `Stop`  
  
- `SyncLock`  
  
- `Throw`  
  
- `Try/Catch/Finally`  
  
- `With`  
  
- Parole chiave a livello di spazio dei nomi o di modulo, ad esempio `End Sub` o `Module`.  
  
## <a name="see-also"></a>Vedere anche  
 [Identificatori di formato in C++](../debugger/format-specifiers-in-cpp.md)   
 [Context Operator (C++)](../debugger/context-operator-cpp.md)   
 [Identificatori di formato in C#](../debugger/format-specifiers-in-csharp.md)   
 [Pseudo variabili](../debugger/pseudovariables.md)
