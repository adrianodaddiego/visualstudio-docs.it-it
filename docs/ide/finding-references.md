---
title: Ricerca di riferimenti nel codice
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df3eb6577c72aa421f2a22d93b3109f63548cc96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793503"
---
# <a name="find-references-in-your-code"></a>Cercare riferimenti nel codice

Per trovare i riferimenti a particolari elementi di codice presenti nella codebase è possibile usare il comando **Trova tutti i riferimenti**. Il comando **Trova tutti i riferimenti** è disponibile nel menu di scelta rapida (clic con il pulsante destro del mouse) dell'elemento per il quale si vuole trovare i riferimenti. In alternativa, se si preferisce usare la tastiera, premere **MAIUSC+F12**.

I risultati vengono visualizzati in una finestra degli strumenti denominata **\<elemento> riferimenti**, dove *elemento* è il nome dell'elemento cercato. Una barra degli strumenti nella finestra dei **riferimenti** consente di:
- Modificare l'ambito della ricerca in un elenco a discesa. È possibile scegliere di eseguire la ricerca solo nei documenti modificati o nell'intera soluzione.
- Copiare l'elemento di riferimento selezionato scegliendo il pulsante **Copia**.
- Scegliere i pulsanti per passare alla posizione precedente o successiva nell'elenco oppure premere **F8** e **MAIUSC+F8** per eseguire questa operazione.
- Rimuovere tutti i filtri applicati ai risultati restituiti scegliendo il pulsante **Cancella tutti i filtri**.
- Modificare il raggruppamento degli elementi restituiti scegliendo un'impostazione nell'elenco a discesa **Raggruppa per**.
- Mantenere la finestra dei risultati della ricerca corrente scegliendo il pulsante **Mantieni risultati**. Quando si sceglie questo pulsante, i risultati della ricerca corrente rimangono in questa finestra e i nuovi risultati vengono visualizzati in una nuova finestra degli strumenti.
- Cercare stringhe nei risultati della ricerca immettendo il testo nella casella di testo **Cerca in Trova tutti i riferimenti**.

È anche possibile passare con il puntatore del mouse su un risultato della ricerca per visualizzare un'anteprima del riferimento.

![Finestra degli strumenti Trova tutti i riferimenti](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Passare ai riferimenti
Per passare ai riferimenti nella finestra dei **riferimenti** è possibile usare i metodi seguenti:

- Premere **F8** per passare al riferimento successivo oppure **MAIUSC+F8** per passare al riferimento precedente.
- Premere **INVIO** su un riferimento oppure fare doppio clic su di esso per passare al riferimento nel codice.
- Nel menu di scelta rapida di un riferimento scegliere i comandi **Vai alla posizione precedente** o **Vai alla posizione successiva**.
- Premere i tasti **freccia SU** e **freccia GIÙ**, se sono abilitati nella finestra di dialogo **Opzioni**. Per abilitare questa funzionalità, nella barra dei menu scegliere **Strumenti** > **Opzioni** > **Ambiente** > **Schede e finestre** > **Scheda anteprima** e quindi selezionare le caselle **Consenti apertura nuovi file nella scheda anteprima** e **Anteprima file selezionati in Risultati ricerca**.

## <a name="change-reference-groupings"></a>Modificare i raggruppamenti di riferimenti
Per impostazione predefinita, i riferimenti sono raggruppati prima in base al progetto e quindi in base alla definizione. È però possibile modificare questo ordine di raggruppamento modificando l'impostazione nell'elenco a discesa**Raggruppa per** sulla barra degli strumenti. Ad esempio, è possibile modificare l'impostazione predefinita **Progetto, quindi definizione** in **Definizione, quindi progetto** o in altre impostazioni.

I due raggruppamenti predefiniti usati sono **Definizione** e **Progetto**, ma è possibile aggiungerne altri scegliendo il comando **Raggruppamento** dal menu di scelta rapida dell'elemento selezionato. L'aggiunta di più raggruppamenti può essere utile se la soluzione contiene molti file e percorsi.

## <a name="filter-by-reference-type-in-net"></a>Filtrare per tipo di riferimento in .NET
In C# o Visual Basic la finestra Trova riferimenti include una colonna Tipo in cui sono elencati i tipi di riferimenti trovati. È possibile usare questa colonna per applicare un filtro in base al tipo di riferimento facendo clic sull'icona del filtro visualizzata al passaggio del mouse sull'intestazione della colonna. I riferimenti possono essere filtrati in base a Lettura, Scrittura, Riferimento e Solo nome.

![Colonna Tipo della finestra Trova riferimenti ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Vedere anche

- [Esplorazione del codice](../ide/navigating-code.md)
