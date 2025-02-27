---
title: Usa caratteri jolly
ms.date: 03/26/2018
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d62f999f485acaba168a50d404f2b5cbb272ef14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821078"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Usare espressioni regolari in Visual Studio

usa [espressioni regolari di .NET Framework](/dotnet/standard/base-types/regular-expressions) per trovare e sostituire il testo.

## <a name="replacement-patterns"></a>Modelli di sostituzione

Per usare un gruppo di acquisizione numerato, racchiudere il gruppo tra parentesi nel criterio dell'espressione regolare. Usare `$number`, dove `number` è un numero intero a partire da 1 per specificare un gruppo numerato specifico in un criterio di sostituzione. Ad esempio, l'espressione regolare raggruppata `(\d)([a-z])` definisce due gruppi: il primo gruppo contiene una singola cifra decimale e il secondo gruppo contiene un carattere singolo compreso tra **a** e **z**. L'espressione trova quattro corrispondenze nella stringa seguente: **1a 2b 3c 4d**. La stringa di sostituzione `z$1` fa riferimento solo al primo gruppo e converte la stringa in **z1 z2 z3 z4**.

Per informazioni sulle espressioni regolari usate nei criteri di sostituzione, vedere [Sostituzioni nelle espressioni regolari (Guida di .NET)](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="regular-expression-examples"></a>Esempi di espressioni regolari

Ecco alcuni esempi:

|Scopo|Espressione|Esempio|
|-------------|----------------|-------------|
|Trovare la corrispondenza con qualsiasi carattere singolo (tranne un'interruzione di riga)|.|`a.o` trova "aro" in "around" e "abo" in "about", ma non "acro" in "across".|
|Trovare la corrispondenza con zero o più occorrenze dell'espressione precedente (trovare quanti più caratteri corrispondenti possibile)|*|`a*r` trova "r" in "rack", "ar" in "ark" e "aar" in "aardvark"|
|Trovare la corrispondenza con qualsiasi carattere zero o più volte (carattere jolly *)|.*|`c.*e` trova "cke" in "racket", "comme" in "comment" e "code" in "code"|
|Trovare la corrispondenza con una o più occorrenze dell'espressione precedente (trovare quanti più caratteri corrispondenti possibile)|+|`e.+d` trova "eed" in "feeder" ma non "ed".|
|Trovare la corrispondenza con qualsiasi carattere una o più volte (carattere jolly ?)|.+|`e.+e` trova "eede" in "feeder" ma non "ee".|
|Trovare la corrispondenza a zero o più occorrenze dell'espressione precedente (trovare quanti meno caratteri corrispondenti possibile)|*?|`e.*?e` trova "ee" in "feeder" ma non "eede".|
|Trovare la corrispondenza a una o più occorrenze dell'espressione precedente (trovare quanti meno caratteri corrispondenti possibile)|+?|`e.+?e` trova "ente" e "erprise" in "enterprise", ma non l'intera parola "enterprise".|
|Ancorare la stringa di corrispondenza all'inizio di una riga o stringa|^|`^car` trova la parola "car" solo quando viene visualizzata all'inizio di una riga.|
|Ancorare la stringa di corrispondenza alla fine di una riga o stringa|\r?$|`end\r?$` trova "end" solo quando è visualizzato alla fine di una riga.|
|Ancorare la stringa di corrispondenza alla fine del file|$|`end$` trova "end" solo quando è visualizzato alla fine del file.|
|Trovare la corrispondenza con qualsiasi carattere singolo in un set|[abc]|`b[abc]` trova "ba", "bb" e "bc".|
|Trovare la corrispondenza con qualsiasi carattere in un intervallo di caratteri|[a-f]|`be[n-t]` trova "bet" in "between", "ben" in "beneath" e "bes" in "beside", ma non "below".|
|Acquisire e numerare in modo implicito l'espressione racchiusa tra parentesi|()|`([a-z])X\1` trova "aXa" e "bXb", ma non "aXb". "\1" fa riferimento al primo gruppo di espressioni "[a-z]".|
|Invalidare una corrispondenza|(?!abc)|`real(?!ity)` trova "real" in "realty" e "really", ma non in "reality". Trova anche il secondo "real" (ma non il primo "real") in "realityreal".|
|Trovare la corrispondenza con qualsiasi carattere non presente in un determinato set di caratteri|[^abc]|`be[^n-t]` trova "bef" in "before", "beh" in "behind" e "bel" in "below", ma non "beneath".|
|Trovare la corrispondenza dell'espressione prima o dopo il simbolo.|&#124;|`(sponge\|mud) bath` trova "sponge bath" e "mud bath".|
|Includere il carattere che segue la barra rovesciata usando una sequenza di escape| \\ |`\^` trova il carattere ^.|
|Specificare il numero di occorrenze del gruppo o del carattere precedente|{x}, dove x è il numero di occorrenze|`x(ab){2}x` trova "xababx" e `x(ab){2,3}x` trova "xababx" e "xabababx" ma non "xababababx".|
|Trovare la corrispondenza con un testo in una classe di caratteri Unicode. Per altre informazioni sulle classi di caratteri Unicode, vedere<br /><br /> [Proprietà dei caratteri Unicode standard 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, dove "X" è il numero Unicode.|`\p{Lu}` trova "T" e "D" in "Thomas Doe".|
|Trovare la corrispondenza con un confine di parola|\b (all'esterno di una classe di caratteri `\b` specifica un confine di parola e all'interno di una classe di caratteri `\b` specifica un backspace).|`\bin` trova "in" in "inside" ma non "pinto".|
|Trovare la corrispondenza con un'interruzione di riga (ovvero un ritorno a capo seguito da una nuova riga).|\r?\n|`End\r?\nBegin` trova "End" e "Begin" solo quando "End" è l'ultima stringa in una riga e "Begin" è la prima stringa nella riga successiva.|
|Trovare la corrispondenza con qualsiasi carattere alfanumerico|\w|`a\wd` trova "add" e "a1d", ma non "a d".|
|Trovare la corrispondenza con qualsiasi spazio vuoto.|\s|`Public\sInterface` trova la frase "Public Interface".|
|Trovare la corrispondenza con qualsiasi carattere numerico|\d|`\d` trova "3" in "3456", "2" in 23" e "1" in "1".|
|Trovare la corrispondenza con un carattere Unicode|\uXXXX dove XXXX specifica il valore del carattere Unicode.|`\u0065` trova il carattere "e".|
|Trovare la corrispondenza con un identificatore|\b[\_\w-[0-9]][\_\w]*\b|Trova "type1" ma non "&type1" o "#define".|
|Trovare la corrispondenza con una stringa tra virgolette|((\\".+?\\")&#124;('.+?'))|Trova qualsiasi stringa racchiusa tra virgolette singole o doppie.|
|Trovare la corrispondenza con un numero esadecimale|\b0[xX]([0-9a-fA-F]+\)\b|Trova "0xc67f", ma non "0xc67g".|
|Trovare la corrispondenza con numeri interi e decimali|\b[0-9]*\\.\*[0-9]+\b|Trova "1.333".|

> [!TIP]
> Nei sistemi operativi Windows la maggior parte delle righe termina con "\r\n" (un ritorno a capo seguito da una nuova riga). Questi caratteri non sono visibili, ma sono presenti nell'editor e vengono passati al servizio delle espressioni regolari di .NET.

## <a name="see-also"></a>Vedere anche

- [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)
