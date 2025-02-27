---
title: Opzioni, editor di testo, di base (Visual Basic), avanzato
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa331fea595c2143dd3ab47aa562fbd61277f81f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817788"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Opzioni, editor di testo, di base (Visual Basic), avanzato
La pagina delle proprietà **Specifiche di VB** nella cartella **Base** della cartella **Editor di testo** della finestra di dialogo **Opzioni** (menu **Strumenti**) include le proprietà seguenti:

## <a name="analysis"></a>Analisi

- Abilita analisi della soluzione completa

   Abilita l'analisi del codice per tutti i file nella soluzione e non solo per i file di codice aperti. Per altre informazioni, vedere [Analisi della soluzione completa](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Direttive using

- Inserisci prima le direttive 'System' durante l'ordinamento delle direttive using

   Se selezionato, il comando **Rimuovi e ordina using** nel menu di scelta rapida ordina le direttive `using` e posiziona gli spazi dei nomi "System" all'inizio dell'elenco.

- Separa gruppi di direttive using

   Se selezionata, il comando **Rimuovi e ordina using** nel menu di scelta rapida separa le direttive `using` inserendo una riga vuota tra gruppi di direttive che hanno lo stesso spazio dei nomi radice.

- Suggerisci le direttive using per i tipi in assembly di riferimento
- Suggerisci le direttive using per i tipi in pacchetti NuGet

   Se queste opzioni sono selezionate, è disponibile un'[azione rapida](../quick-actions.md) per installare un pacchetto NuGet e aggiungere una direttiva `using` per i tipi senza riferimenti.

   ![Azione rapida per installare il pacchetto NuGet in Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Evidenziazione

 **Abilita evidenziazione di riferimenti e parole chiave**

L'editor di testo può evidenziare tutte le istanze di un simbolo o tutte le parole chiave in una clausola, ad esempio `If..Then`, `While...End While` o `Try...Catch...Finally`. È possibile spostarsi tra le parole chiave o i riferimenti evidenziati premendo **CTRL** + **MAIUSC** + **freccia GIÙ** o **CTRL** + **MAIUSC** + **freccia SU**.

## <a name="outlining"></a>struttura

**Abilita modalità struttura**

Quando si apre un file nell'editor del codice, è possibile visualizzare il documento in modalità struttura. Per altre informazioni, vedere [Struttura](../../ide/outlining.md). Quando questa opzione è selezionata, la funzionalità di struttura viene attivata all'apertura di un file.

**Mostra separatori di riga routine**

L'editor di testo indica l'ambito visivo delle routine. Viene tracciata una linea nei file di origine con estensione *vb* del progetto nelle posizioni indicate nella tabella seguente:

|Posizione nel file di origine vb|Esempio di posizione della linea|
|---------------------------------|------------------------------|
|Dopo la chiusura di un costrutto di dichiarazione di blocco|- Alla fine di una classe, struttura, modulo, interfaccia o enumerazione<br />- Dopo una proprietà, funzione o sub<br />- Non tra le clausole get e set in una proprietà|
|Dopo un set di costrutti a riga singola|- Dopo le istruzioni di importazione, prima di una definizione di tipo in un file di classe<br />- Dopo le variabili dichiarate in una classe, prima di qualsiasi routine|
|Dopo le dichiarazioni a riga singola (dichiarazioni non block-level)|- Dopo le istruzioni di importazione, le istruzioni inherits, le dichiarazioni di variabili, le dichiarazioni di eventi, le dichiarazioni di delegati e le istruzioni di dichiarazione di DLL|

## <a name="block-structure-guides"></a>Guide per strutture a blocchi

Se selezionata, nell'editor vengono visualizzate linee verticali allineate ai blocchi di codice strutturato, che consentono di identificare facilmente i singoli blocchi di codice. Ad esempio, verrà visualizzata una riga tra `Sub` e `EndSub` in un'istruzione `Sub`.

## <a name="editor-help"></a>Guida Editor

**Riformatta il listato di codice** Nell'editor di testo viene riformattato il codice nel modo appropriato. Quando questa opzione è selezionata, l'editor del codice:

- Allinea il codice nella posizione di tabulazione corretta

- Imposta la combinazione di maiuscole/minuscole corretta per parole chiave, variabili e oggetti

- Aggiunge un'istruzione `Then` mancante per un'istruzione `If...Then`

- Aggiunge le parentesi alle chiamate di funzione

- Aggiunge le virgolette finali mancanti nelle stringhe

- Riformatta la notazione esponenziale

- Riformatta le date

**Inserimento automatico di costrutti End**

Quando si digita, ad esempio, la prima riga di una dichiarazione di routine, `Sub Main`, e si preme **INVIO**, l'editor di testo aggiunge una riga `End Sub` corrispondente. Analogamente, se si aggiunge un ciclo [For](/dotnet/visual-basic/language-reference/statements/for-next-statement), l'editor di testo aggiunge un'istruzione `Next` corrispondente. Quando questa opzione è selezionata, l'editor del codice aggiunge automaticamente il costrutto end.

**Inserimento automatico di membri Interface e MustOverride**

Quando si esegue il commit di un'istruzione `Implements` o di un'istruzione `Inherits` per una classe, l'editor di testo inserisce prototipi per i membri che devono essere rispettivamente implementati o sottoposti a override.

**Abilita suggerimenti per la correzione di errore**

L'editor di testo può suggerire soluzioni agli errori comuni e consentire la sezione della correzione appropriata, che viene quindi applicata al codice.

## <a name="see-also"></a>Vedere anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
- [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../../ide/reference/options-text-editor-all-languages-tabs.md)
