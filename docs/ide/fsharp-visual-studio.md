---
title: Strumenti F#
description: Informazioni sulle funzionalità di Visual Studio supportate in F#.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: dc3a49c586b7a8f5a67d6c1a3a77d00772698389
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793407"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Sviluppare con F# in Visual Studio

Questo articolo offre informazioni sulle funzionalità di Visual Studio per lo sviluppo in F#.

## <a name="install-f-support"></a>Installare il supporto per F#

Per sviluppare con F# in Visual Studio, installare prima di tutto il carico di lavoro **Sviluppo per desktop .NET**, se non lo si è già fatto. Per installare carichi di lavoro di Visual Studio si usa il programma di installazione di Visual Studio, che è possibile aprire selezionando **Strumenti** > **Ottieni strumenti e funzionalità**.

![Carico di lavoro Sviluppo per desktop .NET in Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>Funzionalità per progetti F#

In Visual Studio sono disponibili vari modelli di progetto e di elemento. L'immagine seguente illustra alcuni modelli di progetto F# per .NET Core e .NET Standard:

![Modelli di progetto F# in Visual Studio](media/fsharp-project-templates.png)

L'immagine seguente illustra alcuni modelli di elemento F#:

![Modelli di elemento F# in Visual Studio](media/fsharp-item-templates.png)

Per altre informazioni sui modelli di elemento per l'accesso ai dati, vedere [Provider di tipi F#](/dotnet/fsharp/tutorials/type-providers/index).

La tabella seguente riepiloga le funzionalità delle proprietà del progetto per F#:

|Impostazione progetto|Supporto in F#|Note|
|---------------|----------------|-----|
|File di risorse|Sì||
|Impostazioni di compilazione, debug e riferimento|Sì||
|Multitargeting|Sì||
|Icona e manifesto|No|Disponibili attraverso le opzioni della riga di comando del compilatore.|
|Servizi client ASP.NET|No||
|ClickOnce|No|Usare un progetto client in un altro linguaggio .NET Framework, se applicabile.|
|Denominazione sicura|No|Disponibili attraverso le opzioni della riga di comando del compilatore.|
|Pubblicazione e controllo delle versioni degli assembly|No||
|Analisi codice|No|Gli strumenti di analisi codice possono essere eseguiti manualmente o nell'ambito di un comando post-compilazione.|
|Sicurezza (modifica dei livelli di attendibilità)|No||

## <a name="project-designer"></a>Progettazione progetti

**Creazione progetti** è costituito da diverse pagine delle proprietà di progetto raggruppate per funzionalità correlate. Le pagine disponibili per i progetti F#, per la maggior parte un subset dei progetti disponibili per altri linguaggi, sono descritte nella tabella seguente. Sono presenti collegamenti alla pagina **Creazione progetti** C# corrispondente.

|Pagina Creazione progetti|Collegamenti correlati|Description|
| - |-------------|-----------|
|Applicazione|[Pagina Applicazione, Creazione progetti](reference/application-page-project-designer-csharp.md)|Consente di specificare le impostazioni e le proprietà a livello di applicazione, ad esempio se si sta creando una libreria o un file eseguibile, nonché la versione di .NET Framework a cui è destinata l'applicazione e informazioni sulla posizione di archiviazione dei file di risorse usati dall'applicazione stessa.|
|Compilazione|[Pagina Compilazione, Progettazione progetti](reference/build-page-project-designer-csharp.md)|Consente di controllare la modalità di compilazione del codice.|
|Eventi di compilazione|[Pagina Eventi di compilazione, Creazione progetti](reference/build-events-page-project-designer-csharp.md)|Consente di specificare i comandi da eseguire prima o dopo una compilazione.|
|Debug|[Pagina Debug, Creazione progetti](reference/debug-page-project-designer.md)|Consente di controllare la modalità di esecuzione dell'applicazione durante il debug, ad esempio i comandi da usare e la directory iniziale dell'applicazione, ed eventuali modalità di debug speciali da abilitare, ad esempio codice nativo e SQL.|
|Pacchetto (solo .NET SDK)|N/D|Consente di definire i metadati del pacchetto NuGet durante la pubblicazione come pacchetto NuGet.|
|Percorsi riferimento|[Gestire i riferimenti in un progetto](managing-references-in-a-project.md)|Consente di specificare la posizione in cui cercare gli assembly da cui dipende il codice.|
|Risorse (solo .NET SDK)|N/D|Consente di generare e gestire un file di risorse predefinito.|

### <a name="f-specific-settings"></a>Impostazioni specifiche di F#

La tabella seguente riepiloga le impostazioni specifiche di F#:

|Pagina Creazione progetti|Impostazione|Description|
| - |-------|-----------|
|Compilazione|Genera chiamate tail|Se selezionata, abilita l'uso delle istruzioni tail MSIL (Microsoft Intermediate Language). In questo modo lo stack frame viene riutilizzato per le funzioni tail ricorsive. Equivalente all'opzione del compilatore `--tailcalls`.|
|Compilazione|Altri flag|Consente di specificare opzioni da riga di comando del compilatore aggiuntive.|

## <a name="code-and-text-editor-features"></a>Funzionalità degli editor di codice e di testo

F# supporta le funzionalità seguenti degli editor di codice e di testo di Visual Studio:

|Funzionalità|Description|Supporto in F#|
|-------|-----------|----------------|
|Commento automatico|Consente di impostare o rimuovere commenti da sezioni di codice.|Sì|
|Formattazione automatica|Riformatta il codice con rientri e stile standard.|No|
|Segnalibri|Consente di salvare posizioni specifiche nell'editor.|Sì|
|Modifica del rientro|Consente di impostare o annullare un rientro per le righe selezionate.|Sì|
|Rientro automatico|Applica e annulla il rientro del cursore in base alle regole di ambito F#.|Sì|
|[Ricerca e sostituzione di testo](finding-and-replacing-text.md)|Consente di eseguire la ricerca in un file, in un progetto o in una soluzione, con la possibilità di modificare il testo.|Sì|
|Passaggio alla definizione per l'API di .NET Framework|Quando il cursore è posizionato su un'API di .NET Framework, visualizza il codice generato dai metadati di .NET Framework.|No|
|Passaggio alla definizione per un'API definita dall'utente|Quando il cursore è posizionato su un'entità di programma definita dall'utente, sposta il cursore nella posizione all'interno del codice in cui l'entità è definita.|Sì|
|Vai alla riga|Consente di passare a una riga specifica in un file, in base al numero di riga.|Sì|
|Barre di spostamento nella parte superiore del file|Consente di passare a posizioni specifiche all'interno del codice, ad esempio a un nome di funzione.|Sì|
|Linee guida per strutture a blocchi|Mostra linee guida che indicano ambiti F# che visualizzano un'anteprima se si sposta il puntatore del mouse su di essi.|Sì|
|[Struttura](outlining.md)|Consente di comprimere le sezioni del codice per creare una visualizzazione più compatta.|Sì|
|Inserimento di tabulazioni|Converte gli spazi in tabulazioni.|Sì|
|Colorazione dei tipi|Visualizza i nomi dei tipi definiti con un colore particolare.|Sì|
|Ricerca veloce. Vedere Ricerca veloce, finestra Trova e sostituisci.|Consente di eseguire ricerche all'interno di un file o di un progetto.|Sì|
|**Ctrl**+**clic** per passare a una definizione|Consente di richiamare Vai a definizione tenendo premuto **Ctrl** e facendo clic su un simbolo F#.|Sì|
|Vai a definizione da Informazioni rapide|Simboli selezionabili all'interno delle descrizioni comando che richiamano Vai a definizione.|Sì|
|Vai a tutti|Consente lo spostamento per corrispondenze fuzzy globale per tutti i costrutti F# tramite **Ctrl**+**T**.|Sì|
|Ridenominazione inline|Consente di rinominare tutte le occorrenze di un simbolo inline.|Sì|
|Trova tutti i riferimenti|Trova tutte le occorrenze di un simbolo in una codebase.|Sì|
|Correzione del codice Semplifica nome|Rimuove i qualificatori non necessari per i simboli F#.|Sì|
|Correzione del codice Rimuovi istruzioni `open` non usate|Rimuove tutte le istruzioni `open` non necessarie presenti in un documento.|Sì|
|Correzione del codice valore non usato|Suggerisce di rinominare un identificatore non usato in un carattere di sottolineatura.|Sì|

Per informazioni generali sulla modifica di codice in Visual Studio e sulle funzionalità dell'editor di testo, vedere [Scrivere codice nell'editor](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>IntelliSense, funzionalità

La tabella seguente riepiloga le funzionalità di IntelliSense supportate e non supportate in F#:

|Funzionalità|Description|Supporto in F#|
|-------|-----------|----------------|
|Implementazione automatica di interfacce|Genera stub di codice per metodi di interfaccia.|Sì|
|Frammenti di codice|Inserisce codice da una libreria di costrutti di codifica comuni in argomenti.|No|
|Completa parola|Salva il testo digitato completando le parole e i nomi durante la digitazione.|Sì|
|Completamento automatico|Se abilitata, questa funzionalità fa in modo che il completamento delle parole selezioni la prima corrispondenza durante la digitazione, anziché attendere la selezione di una parola o la pressione di **Ctrl**+**Spazio** da parte dell'utente.|Sì|
|Offerta di completamento dei simboli all'interno di spazi dei nomi non aperti|Con il completamento automatico, viene suggerito un simbolo corrispondente presente in uno spazio dei nomi non aperto, consentendo il completamento con l'istruzione `open` corrispondente, se selezionato.|Sì|
|Generazione di elementi di codice|Consente di generare codice di stub per un'ampia gamma di costrutti.|No|
|Elenca membri|Quando si digita l'operatore di accesso ai membri (.), visualizza i membri di un tipo.|Sì|
|Organizzazione di using/open|Organizza gli spazi dei nomi a cui fanno riferimento istruzioni **using** in C# o direttive **open** in F#.|No|
|Informazioni sul parametro|Visualizza informazioni utili sui parametri durante la digitazione di una chiamata di funzione.|Sì|
|Informazioni rapide|Visualizza la dichiarazione completa per ogni identificatore incluso nel codice.|Sì|
|Completamento parentesi graffa automatico|Completa automaticamente i costrutti di sintassi con parentesi graffe di F# in modo transazionale.|Sì|

Per informazioni generali su IntelliSense, vedere [Usare IntelliSense](using-intellisense.md).

## <a name="debugging-features"></a>Funzionalità di debug

La tabella seguente riepiloga le funzionalità disponibili quando si esegue il debug di codice F#:

|Funzionalità|Description|Supporto in F#|
|-------|-----------|----------------|
|Auto (finestra)|Visualizza le variabili automatiche o temporanee.|No|
|Punti di interruzione|Consente di sospendere l'esecuzione del codice in corrispondenza di punti specifici durante il debug.|Sì|
|Punti di interruzione condizionali|Consente l'uso di punti di interruzione che eseguono il test di una condizione che determina se l'esecuzione deve essere sospesa.|Sì|
|Modifica e continuazione|Consente la modifica e la compilazione del codice durante il debug di un programma in esecuzione senza interrompere e riavviare il debugger.|No|
|Analizzatore di espressioni|Valuta ed esegue codice in fase di runtime.|No, ma è possibile usare l'analizzatore di espressioni C#, anche se è necessario usare la sintassi C#.|
|Debug cronologico|Consente di eseguire un'istruzione di codice eseguito in precedenza.|Sì|
|Finestra Variabili locali|Visualizza valori e variabili definiti localmente.|Sì|
|Esecuzione fino al cursore|Consente di eseguire il codice fino al raggiungimento della riga che contiene il cursore.|Sì|
|Esegui istruzione|Consente di anticipare l'esecuzione passando a una qualsiasi chiamata di funzione.|Sì|
|Esegui istruzione/routine|Consente di anticipare l'esecuzione nello stack frame corrente superando qualsiasi chiamata di funzione.|Sì|

Per informazioni generali sul debugger di Visual Studio, vedere [Debug in Visual Studio](../debugger/index.md).

## <a name="additional-tools"></a>Strumenti aggiuntivi

La tabella seguente riepiloga il supporto per F# di Strumenti di Visual Studio.

|Strumento|Description|Supporto in F#|
|----|-----------|----------------|
|Gerarchia delle chiamate|Visualizza la struttura annidata delle chiamate di funzione nel codice.|No|
|Metrica del codice|Raccoglie informazioni sul codice, ad esempio il numero di righe.|No|
|Visualizzazione classi|Rende disponibile una visualizzazione del codice di un progetto basata sui tipi.|No|
|[Finestra Elenco errori](reference/error-list-window.md)|Visualizza l'elenco degli errori nel codice.|Sì|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Consente di digitare (o copiare e incollare) codice F# ed eseguirlo immediatamente, indipendentemente dalla compilazione del progetto. La finestra F# Interactive è una finestra REPL (Read-Eval-Print).|Sì|
|Visualizzatore oggetti|Consente di visualizzare i tipi presenti in un assembly.|I tipi F# visualizzati negli assembly compilati non appaiono esattamente come vengono creati. È possibile esplorare la rappresentazione compilata dei tipi F#, ma non è possibile visualizzare i tipi così come appaiono da F#.|
|[Finestra Output](reference/output-window.md)|Visualizza l'output della compilazione.|Sì|
|Analisi delle prestazioni|Rende disponibili strumenti per la misurazione delle prestazioni del codice.|Sì|
|Finestra Proprietà|Visualizza le proprietà dell'oggetto con stato attivo nell'ambiente di sviluppo e consente la modifica di tali proprietà.|Sì|
|Esplora server|Offre alcuni metodi per l'interazione con un'ampia gamma di risorse del server.|Sì|
|Esplora soluzioni|Consente di visualizzare e gestire progetti e file.|Sì|
|Elenco attività|Consente di gestire gli elementi di lavoro relativi al codice.|No|
|Progetti di test|Offre funzionalità per l'esecuzione del test del codice.|No|
|Casella degli strumenti|Visualizza schede che contengono oggetti trascinabili quali controlli e sezioni di testo o codice.|Sì|

## <a name="see-also"></a>Vedere anche

- [Guida a F# (.NET Framework)](/dotnet/fsharp/)
- [Introduzione a F# in Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)