---
title: Comandi della JavaScript Console | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript Console commands [Windows Store apps]
- JavaScript debugging, console [Windows Store apps]
- debugging JavaScript, console [Windows Store apps]
ms.assetid: 359e2b24-6bb7-48e7-8b55-b570df0cb774
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5c4223699c720750514aaf2b9abc18b34ae4269
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690589"
---
# <a name="javascript-console-commands"></a>JavaScript Console commands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica a Windows e Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 È possibile usare i comandi per inviare messaggi ed eseguire altre attività nella finestra della console JavaScript di Visual Studio. Per esempi che illustrano come utilizzare tale finestra, vedere [Guida introduttiva: Eseguire il debug JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md). Le informazioni contenute in questo argomento si applicano alle app di Windows Store, alle app di Windows Phone Store e alle app create con Visual Studio Tools per Apache Cordova. Per informazioni sui comandi della console supportati nelle app di Cordova, vedere [Debug Your App](https://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1). Per informazioni sull'uso della console negli strumenti F12 di Internet Explorer, vedere [questo argomento](https://msdn.microsoft.com/library/ie/dn255006.aspx).  
  
 Se la finestra della console JavaScript è chiusa, è possibile aprirla durante il debug in Visual Studio scegliendo **Debug** > **Finestre** > **Console JavaScript**.  
  
> [!NOTE]
> Se la finestra non è disponibile durante una sessione di debug, assicurarsi che il tipo di debugger sia impostato su **Script** nelle proprietà di debug per il progetto.  
  
## <a name="console-object-commands"></a>Comandi dell'oggetto console  
 Questa tabella mostra la sintassi per i comandi dell'oggetto `console` che è possibile usare nella finestra della console JavaScript o per inviare messaggi alla console dal codice. Questo oggetto fornisce numerosi formati in modo che sia possibile distinguere i messaggi informativi dai messaggi di errore, se lo si desidera.  
  
 È possibile usare il formato del comando più lungo `window.console.[command]` se è necessario evitare possibili confusioni con gli oggetti locali denominati console.  
  
> [!TIP]
> Le versioni precedenti di Visual Studio non supportano il set completo di comandi. Usare IntelliSense sull'oggetto console per ottenere informazioni rapide sui comandi supportati.  
  
|Comando|Descrizione|Esempio|  
|-------------|-----------------|-------------|  
|`assert(expression, message)`|Invia un messaggio quando `expression` restituisce **false**.|`console.assert((x == 1), "assert message: x != 1");`|  
|`clear()`|Cancella i messaggi dalla finestra della console, inclusi i messaggi di errore di script, e cancella inoltre lo script visualizzato nella finestra della console. Non cancella lo script immesso nella richiesta di input della console.|`console.clear();`|  
|`count(title)`|Invia il numero di volte in cui è stato chiamato il comando count nella finestra della console. Ogni chiamata al comando count viene identificata in modo univoco dal parametro `title`facoltativo.<br /><br /> La voce esistente nella finestra della console viene identificata dal parametro `title` (se presente) e aggiornata dal comando count. Viene ora creata una nuova voce.|`console.count();`<br /><br /> `console.count("inner loop");`|  
|`debug(message)`|Invia `message` alla finestra della console.<br /><br /> Questo comando è identico a console.log.<br /><br /> Gli oggetti passati usando tale comando vengono convertiti in un valore stringa.|`console.debug("logging message");`|  
|`dir(object)`|Invia l'oggetto specificato alla finestra della console e lo visualizza in un visualizzatore oggetti. È possibile usare il visualizzatore per controllare le proprietà nella finestra della console.|`console.dir(obj);`|  
|`dirxml(object)`|Invia il nodo XML `object` specificato alla finestra della console e lo visualizza in un albero del nodo XML.|`console.dirxaml(xmlNode);`|  
|`error(message)`|Invia `message` alla finestra della console. Il testo del messaggio è rosso ed è preceduto da un simbolo di errore.<br /><br /> Gli oggetti passati usando tale comando vengono convertiti in un valore stringa.|`console.error("error message");`|  
|`group(title)`|Avvia un raggruppamento per i messaggi inviati alla finestra della console e invia il parametro `title` facoltativo come etichetta di gruppo. I gruppi possono essere annidati e visualizzati in una visualizzazione struttura ad albero nella finestra della console.<br /><br /> I comandi del gruppo* possono semplificare la visualizzazione dell'output della finestra della console in alcuni scenari, ad esempio quando viene usato un modello componente.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|  
|`groupCollapsed(title)`|Avvia un raggruppamento per i messaggi inviati alla finestra della console e invia il parametro `title` facoltativo come etichetta di gruppo. I gruppi inviati tramite `groupCollapsed` vengono visualizzati per impostazione predefinita in una visualizzazione compressa. I gruppi possono essere annidati e visualizzati in una visualizzazione struttura ad albero nella finestra della console.|L'utilizzo è identico a quello del comando `group` .<br /><br /> Vedere l'esempio per il comando `group` .|  
|`groupEnd()`|Termina il gruppo corrente.<br /><br /> Requisiti:<br /><br /> Visual Studio 2013|Vedere l'esempio per il comando `group` .|  
|`info(message)`|Invia `message` alla finestra della console. Il messaggio è preceduto da un simbolo di informazioni.|`console.info("info message");`<br /><br /> Per altri esempi, vedere [Formatting console.log output](#ConsoleLog) più avanti in questo argomento.|  
|`log(message)`|Invia `message` alla finestra della console.<br /><br /> Se si passa un oggetto, questo comando lo invia alla finestra della console e lo visualizza in un visualizzatore oggetti. È possibile usare il visualizzatore per controllare le proprietà nella finestra della console.|`console.log("logging message");`|  
|`msIsIndependentlyComposed(element)`|Usato nelle app Web. Non supportato nelle app di Store in JavaScript.|Non supportato.|  
|`profile(reportName)`|Usato nelle app Web. Non supportato nelle app di Store in JavaScript.|Non supportato.|  
|`profileEnd()`|Usato nelle app Web. Non supportato nelle app di Store in JavaScript.|Non supportato.|  
|`select(element)`|Seleziona l'elemento HTML `element` specificato in [DOM Explorer](../debugger/quickstart-debug-html-and-css.md).|console.select(element);|  
|`time (name)`|Avvia un timer identificato dal parametro facoltativo `name` . Se usato con `console.timeEnd`, calcola il tempo che intercorre tra `time` e `timeEnd`e invia il risultato (misurato in ms) alla console usando la stringa `name` come prefisso. Usato per abilitare la strumentazione del codice dell'app per la misurazione delle prestazioni.|`console.time("app start");  app.start();  console.timeEnd("app start");`|  
|`timeEnd(name)`|Arresta un timer identificato dal parametro facoltativo `name` . Vedere il comando della console `time` .|`console.time("app start"); app.start(); console.timeEnd("app start");`|  
|`trace()`|Invia una traccia dello stack alla finestra della console. La traccia include lo stack di chiamate completo e informazioni quali il nome file, il numero di riga e il numero di colonna.|`console.trace();`|  
|`warn(message)`|Invia `message` alla finestra della console, preceduto da un simbolo di avviso.<br /><br /> Gli oggetti passati usando tale comando vengono convertiti in un valore stringa.|`console.warn("warning message");`|  
  
## <a name="miscellaneous-commands"></a>Comandi vari  
 Questi comandi sono disponibili anche nella finestra della console JavaScript (non sono disponibili dal codice).  
  
|Comando|Descrizione|Esempio|  
|-------------|-----------------|-------------|  
|`$0`, `$1`, `$2`, `$3`, `$4`|Restituisce l'elemento specificato nella finestra della console. `$0` restituisce l'elemento al momento selezionato in DOM Explorer, `$1` restituisce l'elemento selezionato in precedenza in DOM Explorer e così via, fino al quarto elemento selezionato in precedenza.|$3|  
|`$(id)`|Restituisce un elemento in base all'ID. Si tratta di un comando di scelta rapida per `document.getElementById(id)`, dove `id` è una stringa che rappresenta l'ID dell'elemento.|`$("contenthost")`|  
|`$$(selector)`|Restituisce una matrice di elementi che corrispondono al selettore specificato usando la sintassi del selettore CSS. Si tratta di un comando di scelta rapida per `document.querySelectorAll()`.|`$$(".itemlist")`|  
|`cd()`<br /><br /> `cd(window)`|Consente di modificare il contesto per la valutazione di un'espressione dalla finestra di primo livello predefinita della pagina alla finestra del frame specificato. Chiamando `cd()` senza parametri, viene restituito il contesto nella finestra di primo livello.|`cd();`<br /><br /> `cd(myframe);`|  
|`select(element)`|Seleziona l'elemento specificato in [DOM Explorer](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|  
|`dir(object)`|Restituisce un visualizzatore per l'oggetto specificato. È possibile usare il visualizzatore per controllare le proprietà nella finestra della console.|`dir(obj);`|  
  
## <a name="checking-whether-a-console-command-exists"></a>Verifica dell'esistenza di un comando della console  
 È possibile verificare l'esistenza di un comando specifico prima di tentare di usarlo. In questo esempio viene verificata l'esistenza del comando `console.log` . Se `console.log` esiste, viene chiamato dal codice.  
  
```javascript  
if (console && console.log) {  
    console.log("msg");  
}  
  
```  
  
## <a name="examining-objects-in-the-javascript-console-window"></a>Esame degli oggetti nella finestra della console JavaScript  
 È possibile interagire con qualsiasi oggetto all'interno dell'ambito quando si usa la finestra della console JavaScript. Per controllare un oggetto esterno all'ambito nella finestra della console, usare `console.log` , `console.dir`o altri comandi del codice. In alternativa, è possibile interagire con l'oggetto dalla finestra della console mentre si trova nell'ambito impostando un punto di interruzione nel codice (**Punto di interruzione** > **Insert Punto di interruzione**).  
  
## <a name="ConsoleLog"></a> Formattazione dell'output di console.log  
 Se si passano più argomenti a `console.log`, la console li considererà come una matrice e concatenerà l'output.  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
  
console.log(user.first, user.last);  
// Output:  
// Fred Smith  
  
```  
  
 Per formattare l'output, in `console.log` sono anche supportati i modelli di sostituzione "printf". Se si usano i modelli di sostituzione nel primo argomento, verranno usati altri argomenti per sostituire i modelli specificati nell'ordine in cui sono usati.  
  
 Sono supportati i modelli di sostituzione seguenti:  
  
- %s - stringa  
   %i - intero  
   %d - intero  
   %f - float  
   %o - oggetto  
   %b - binario  
   %x - esadecimale  
   %e - esponente  
  
  Ecco alcuni esempi di utilizzo dei modelli di sostituzione in `console.log`:  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
user.age = 10.01;  
console.log("Hi, %s %s!", user.first, user.last);  
console.log("%s is %i years old!", user.first, user.age);  
console.log("%s is %f years old!", user.first, user.age);  
  
// Output:  
// Hi, Fred Smith!  
// Fred is 10 years old!  
// Fred is 10.01 years old!  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio rapido: Eseguire il debug di JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)   
 [Avvio rapido: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)
