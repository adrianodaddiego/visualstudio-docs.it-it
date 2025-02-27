---
title: Finestre del debugger XSLT
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b25c47e6db79fe4b860b6e7c209f0fc8403d0fcd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838493"
---
# <a name="debugger-user-interface-xslt"></a>Interfaccia utente del debugger (XSLT)

Questo articolo descrive le finestre del debugger e finestre di dialogo. Vengono illustrati solo elementi dell'interfaccia utente che presentano un comportamento di debug specifiche XSLT.

Per altre informazioni, vedere la [riferimento all'interfaccia utente di debug](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>Finestra Variabili locali

Nella finestra Variabili locali vengono visualizzate le informazioni sulle variabili definite nel foglio di stile. La finestra Variabili locali contiene tre colonne di informazioni:

**Name**

Questa colonna contiene i nomi di tutte le variabili locali nell'ambito corrente. Set di nodi dispongono di un controllo albero che è possibile eseguire il drill down per visualizzare le sottocartelle.

**Valore**

In questa colonna è visualizzato il valore contenuto da ciascuna variabile. Nei nodi Attribute, processing instruction, comment, text e CData viene visualizzato il valore di testo del nodo. Nei nodi Namespace viene visualizzato l'URI dello spazio dei nomi.

**Type**

Questa colonna identifica il tipo di dati di ciascuna variabile elencata nel **nome** colonna.

Nella finestra Variabili locali vengono inoltre visualizzate le variabili di contesto predefinite che tengono traccia del contesto della trasformazione XSLT. Nella tabella seguente vengono descritte le variabili di contesto predefinite usate dal debugger XSLT.

|Nome|Descrizione|
|-|-----------------|
|`last()`|La dimensione del contesto.|
|`position()`|Posizione, ossia il numero di indice, del nodo di contesto, in base alla dimensione del contesto.|
|`self::node()`|Il valore del nodo di contesto.|

## <a name="output-window"></a>Output (finestra)

Nella finestra di output vengono visualizzati eventuali messaggi di errore o eccezioni di sicurezza che si verificano durante il debug. Viene inoltre illustrato l'output del debugger.

## <a name="task-list"></a>Elenco attività

Il **elenco attività** sono elencati tutti gli errori di compilazione nel foglio di stile. Se si fa doppio clic sull'errore il cursore si sposta sulla riga contenente l'errore.

Il **elenco attività** includa gli errori che si verificano nei blocchi di script nel file XSLT.

> [!NOTE]
> Il debugger XSLT non dispone di avvisi, in modo che vengano visualizzati nel **elenco attività**.

## <a name="breakpoints-window"></a>finestra Punti di interruzione

Nella finestra Punti di interruzione vengono visualizzati tutti i punti di interruzione impostati nel progetto corrente. Se si aggiunge un punto di interruzione mentre la finestra è visualizzata, la finestra viene aggiornata automaticamente per mostrare il nuovo punto di interruzione.

La finestra Punto di interruzione dovrebbe comportarsi allo stesso modo degli altri debugger di Visual Studio.

## <a name="watch-window"></a>Finestra Espressioni di controllo

La finestra Espressioni di controllo viene usata per valutare le variabili. È anche possibile modificare i valori delle variabili.

Le variabili visualizzate nella finestra Espressioni di controllo sono relative al contesto corrente (l'elemento in primo piano nello stack di chiamate). Se si modifica il contesto, la finestra viene aggiornata e vengono visualizzate le variabili impostate per quel determinato contesto.

## <a name="call-stack-window"></a>Finestra Stack di chiamate

Il **Stack di chiamate** finestra viene utilizzata per visualizzare i nomi delle funzioni in di stack di chiamate, i tipi di parametro e i valori dei parametri. Le informazioni relative allo stack di chiamate sono visualizzate solo quando il programma in fase di debug si trova in modalità interruzione.

Lo stack di chiamate rappresenta i vari contesti in cui si verifica l'esecuzione XSLT. Ad esempio, se viene eseguita una chiamata dal modello "a" al modello "b", modello "a" e modello "b" vengono visualizzati nei **Stack di chiamate** finestra con il contesto corrente nella parte superiore dell'elenco. L'utente è in grado di visualizzare la query attualmente in esecuzione.

Se i modelli non dispongono di un nome nel file XSLT, vengono usati i nomi generati dal processore XSLT.

Se si fa clic su un elemento diverso da quello presente all'inizio dell'elenco, viene indicato al visualizzatore dove si è verificata la creazione di un ramo dell'esecuzione XSLT usando l'evidenziazione verde standard e le frecce verdi.

## <a name="quickwatch-dialog-box"></a>Controllo immediato (finestra di dialogo)

Il **controllo immediato** nella finestra di dialogo viene utilizzata per valutare le espressioni XPath 1.0. Il nodo di contesto (il nodo `self::node()` proveniente dalla finestra Variabili locali) fornisce il contesto per l'esecuzione dell'espressione XPath. Il risultato dell'esecuzione dell'espressione XPath viene visualizzato nella finestra Espressioni di controllo.

L'elenco seguente descrive le restrizioni nella valutazione dell'espressione XPath:

- Sono consentite solo le funzioni XPath incorporate.

- Ad esempio le funzioni di XSLT incorporate `document()` e `key()` non sono consentiti.

- Non sono consentite funzioni definite dall'utente.

Per altre informazioni, vedere [Procedura: Valutare un'espressione XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Disassembly (finestra)

Nella finestra Disassembly viene visualizzato il codice di assembly generato dal compilatore XSLT. Questa finestra può essere usata nello stesso modo in cui si usano tutte le altre finestre Disassembly di Visual Studio.

Per altre informazioni, [come: Utilizzare la finestra disassembly](../debugger/how-to-use-the-disassembly-window.md).

## <a name="see-also"></a>Vedere anche

- [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Esaminare le variabili nelle finestre Auto e variabili locali in Visual Studio](../debugger/autos-and-locals-windows.md)