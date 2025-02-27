---
title: Opzioni, Editor di testo, Base (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 461af4c3c8e811c989bc296b6f8f55f398bc5bd5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674504"
---
# <a name="options-text-editor-basic-visual-basic"></a>Opzioni, Editor di testo, Base (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La pagina delle proprietà **Specifiche di VB** nella cartella **Base** della cartella **Editor di testo** della finestra di dialogo **Opzioni** (menu **Strumenti**) contiene le proprietà seguenti:  
  
 **Inserimento automatico di costrutti End**  
 Quando si digita, ad esempio, la prima riga di una dichiarazione di routine, `Sub Main—`, e si preme INVIO, l'editor di testo aggiunge una riga `End Sub` corrispondente. Analogamente, se si aggiunge un ciclo [For](https://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9), l'editor di testo aggiunge un'istruzione `Next` corrispondente. Quando questa opzione è selezionata, l'editor del codice aggiunge automaticamente il costrutto end.  
  
 **Riformatta il listato di codice**  
 L'editor di testo riformatta il codice come appropriato. Quando questa opzione è selezionata, l'editor del codice:  
  
- Allinea il codice nella posizione di tabulazione corretta  
  
- Imposta la combinazione di maiuscole/minuscole corretta per parole chiave, variabili e oggetti  
  
- Aggiunge un'istruzione `Then` mancante per un'istruzione `If...Then`  
  
- Aggiunge le parentesi alle chiamate di funzione  
  
- Aggiunge le virgolette finali mancanti nelle stringhe  
  
- Riformatta la notazione esponenziale  
  
- Riformatta le date  
  
  **Abilita modalità struttura**  
  Quando si apre un file nell'editor del codice, è possibile visualizzare il documento in modalità struttura. Per altre informazioni, vedere [Struttura](../../ide/outlining.md). Quando questa opzione è selezionata, la funzionalità di struttura viene attivata all'apertura di un file.  
  
  **Inserimento automatico di membri Interface e MustOverride**  
  Quando si esegue il commit di un'istruzione `Implements` o di un'istruzione `Inherits` per una classe, l'editor di testo inserisce prototipi per i membri che devono essere rispettivamente implementati o sottoposti a override.  
  
  **Mostra separatori di riga routine**  
  L'editor di testo indica l'ambito visivo delle routine. Viene tracciata una linea nei file di origine con estensione vb del progetto nelle posizioni indicate nella tabella seguente:  
  
|Posizione nel file di origine vb|Esempio di posizione della linea|  
|---------------------------------|------------------------------|  
|Dopo la chiusura di un costrutto di dichiarazione di blocco|- Alla fine di una classe, struttura, modulo, interfaccia o enumerazione<br />- Dopo una proprietà, funzione o sub<br />- Non tra le clausole get e set in una proprietà|  
|Dopo un set di costrutti a riga singola|- Dopo le istruzioni di importazione, prima di una definizione di tipo in un file di classe<br />- Dopo le variabili dichiarate in una classe, prima di qualsiasi routine|  
|Dopo le dichiarazioni a riga singola (dichiarazioni non block-level)|- Dopo le istruzioni di importazione, le istruzioni inherits, le dichiarazioni di variabili, le dichiarazioni di eventi, le dichiarazioni di delegati e le istruzioni di dichiarazione di DLL|  
  
 **Abilita suggerimenti per la correzione di errore**  
 L'editor di testo può suggerire soluzioni agli errori comuni e consentire la sezione della correzione appropriata, che viene quindi applicata al codice.  
  
 **Abilita evidenziazione di riferimenti e parole chiave**  
 L'editor di testo può evidenziare tutte le istanze di un simbolo o tutte le parole chiave in una clausola, ad esempio `If..Then`, `While...End While` o `Try...Catch...Finally`. È possibile spostarsi tra le parole chiave o i riferimenti evidenziati premendo CTRL+MAIUSC+freccia GIÙ o CTRL+MAIUSC+freccia SU.  
  
## <a name="see-also"></a>Vedere anche  
 [General, Environment, Options Dialog Box](../../ide/reference/general-environment-options-dialog-box.md)  (Generale, Ambiente, finestra di dialogo Opzioni)  
 [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../../ide/reference/options-text-editor-all-languages-tabs.md)
