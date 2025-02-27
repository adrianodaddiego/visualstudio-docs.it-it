---
title: Opzioni di formattazione dell'editor C#
ms.date: 08/14/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a11fa7913828ef557c87ec50184c9de35a9e5bc4
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65847437"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Finestra di dialogo Opzioni: Editor di testo \> C# \> Stile codice \> Formattazione

Usare la pagina di opzioni **Formattazione** e le relative pagine secondarie ([**Rientro**](#indentation-page), **Nuove righe**, **Spaziatura** e **Ritorno a capo**) per impostare le opzioni di formattazione del codice nell'editor del codice.

Per accedere a questa pagina di opzioni, scegliere **Strumenti** > **Opzioni** dalla barra dei menu. Nella finestra di dialogo **Opzioni** scegliere **Editor di testo** > **C#** > **Stile codice** > **Formattazione**.

> [!TIP]
> Ognuna delle pagine secondarie **Rientro**, **Nuove righe**, **Spaziatura** e **Ritorno a capo** visualizza una finestra di anteprima nella parte inferiore che mostra l'effetto dell'applicazione di ogni opzione. Per usare la finestra di anteprima, selezionare un'opzione di formattazione. La finestra di anteprima illustra un esempio dell'opzione selezionata. Quando si modifica un'impostazione selezionando un pulsante di opzione o una casella di controllo, la finestra di anteprima viene aggiornata per mostrare l'effetto della nuova impostazione.

## <a name="formatting-general-page"></a>Pagina Formattazione (Generale)

### <a name="general-settings"></a>Impostazioni generali

Queste impostazioni influenzano *il momento in cui* l'editor del codice applica le opzioni di formattazione al codice.

|Label|Description|
|-----------|-----------------|
|**Formatta automaticamente durante la digitazione**|Quando questa opzione è deselezionata, le opzioni **Formatta automaticamente istruzione dopo :** e **Formatta automaticamente blocco dopo }** sono disabilitate.|
|**Formatta automaticamente istruzione dopo ;**|Quando questa opzione è selezionata, le istruzioni vengono formattate al completamento in base alle opzioni di formattazione selezionate per l'editor.|
|**Formatta automaticamente blocco dopo }**|Quando questa opzione è selezionata, i blocchi di codice vengono formattati in base alle opzioni di formattazione selezionate per l'editor subito dopo il completamento del blocco di codice.|
|**Formatta automaticamente dopo INVIO**|Quando questa opzione è selezionata, il testo viene formattato dopo la pressione di **INVIO**, in base alle opzioni di formattazione selezionate per l'editor.|
|**Formatta automaticamente dopo operazione Incolla**|Quando questa opzione è selezionata, il testo incollato nell'editor viene formattato in base alle opzioni di formattazione selezionate per l'editor.|

::: moniker range="vs-2019"

Se si è già utilizzato il comando **Formatta documento** per applicare impostazioni di stile al codice per i file C# in Visual Studio 2017, ora tale funzionalità disponibile con il nome [**Pulizia del codice**](../code-styles-and-code-cleanup.md#apply-code-styles).

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Impostazioni di Formatta documento

Queste impostazioni configurano il comando **Formatta documento** per eseguire una pulizia del codice aggiuntiva in un file. Per altre informazioni su come applicare queste impostazioni, vedere [Format Document command](../code-styles-and-code-cleanup.md#apply-code-styles) (Comando Formatta documento).

|Label|Description|Regole di EditorConfig e Strumenti > Opzioni corrispondenti|
|-----------|-----------------|-----------------|-----------------|
|**Applica tutte le regole di formattazione di C# (rientro, ritorno a capo, spaziatura)**|Il comando **Formatta documento** corregge sempre i problemi di formattazione. Questa impostazione non può essere modificata.| [Opzioni di base di EditorConfig](../../ide/create-portable-custom-editor-options.md)<br/>[Opzioni di formattazione di EditorConfig .NET](../../ide/editorconfig-code-style-settings-reference.md#formatting-conventions)<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Formattazione**  > [**Rientro** oppure **Nuove righe** oppure **Spaziatura** oppure **Ritorno a capo**]|
|**Esegui la pulizia aggiuntiva del codice durante la formattazione**|Se selezionata, applica le correzioni alle regole specificate di seguito nel comando **Edit.FormatDocument**.| N/D |
|**Rimuovi using non necessari**|Se selezionata, consente di rimuovere le direttive `using` inutili quando **Edit.FormatDocument** viene attivato.| N/D |
|**Ordina using**|Se selezionata, consente di ordinare le direttive `using` quando **Edit.FormatDocument** viene attivato.| dotnet_sort_system_directives_first<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Avanzate**  > **Inserisci prima le direttive 'System' durante l'ordinamento delle direttive using** |
|**Aggiungi/rimuovi le parentesi graffe per le istruzioni di controllo a riga singola**|Se selezionata, aggiunge o rimuove le parentesi graffe da istruzioni di controllo a riga singola quando **Edit.FormatDocument** viene attivato.| csharp_prefer_braces<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Stile codice**  > **Preferenze per blocchi di codice** > **Preferisci parentesi graffe** |
|**Aggiungi i modificatori di accessibilità**|Se selezionata, aggiunge i modificatori di accessibilità mancanti quando **Edit.FormatDocument** viene attivato.| dotnet_style_require_accessibility_modifiers |
|**Ordina i modificatori di accessibilità**|Se selezionata, ordina i modificatori di accessibilità quando **Edit.FormatDocument** viene attivato.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Applica le preferenze relative al corpo di espressioni/blocchi**|Se selezionata, converte i membri con corpo di espressione per bloccare i corpi, o viceversa, quando **Edit.FormatDocument** viene attivato.| [Opzioni di EditorConfig per il membro con corpo di espressione](../../ide/editorconfig-code-style-settings-reference.md#expression_bodied_members)<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Stile codice**  > **Preferenze per espressioni** > **Use expression body for methods, constructors, etc.** (Usa il corpo dell'espressione per metodi, costruttori e così via) |
|**Applica le preferenze relative al tipo implicito/esplicito**|Se selezionata, consente di convertire `var` al tipo esplicito, o viceversa, quando **Edit.FormatDocument** viene attivato.| [Opzioni di base di EditorConfig per il tipo esplicito](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types)<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Stile codice** > **Preferenze per 'var'** |
|**Applica le preferenze relative alle variabili 'out' inline**|Se selezionata, ordina inline le variabili `out` dove possibile quando **Edit.FormatDocument** viene attivato.| csharp_style_inlined_variable_declaration<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Stile codice** > **Preferenze per variabili** > **Preferisci dichiarazione di variabile inline** |
|**Applica le preferenze relative al tipo di linguaggio/framework**|Se selezionata, consente di convertire i tipi di linguaggio ai tipi framework, o viceversa, quando **Edit.FormatDocument** viene attivato.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Stile codice** > **preferenze per tipi predefiniti** |
|**Applica le preferenze di inizializzazione di oggetti/raccolte**|Se selezionata, usa inizializzatori di insieme e oggetto laddove possibile quando **Edit.FormatDocument** viene attivato.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Stile codice** > **Preferenze per espressioni** > **Preferisci inizializzatore di oggetto** o **Preferisci inizializzatore di insieme** |
|**Applica le preferenze relative alla qualificazione 'this.'**|Se selezionata, consente di applicare le preferenze `this.` quando **Edit.FormatDocument** viene attivato.| [Opzioni di EditorConfig per la qualificazione this.](../../ide/editorconfig-code-style-settings-reference.md#this_and_me)<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Stile codice** > **Preferenze per 'this.'** |
|**Imposta i campi privati come di sola lettura quando possibile**|Se selezionata, rende privati i campi `readonly` dove possibile quando **Edit.FormatDocument** viene attivato.| dotnet_style_readonly_field<br/><br/>**Strumenti** > **Opzioni** > **Editor di testo** > **C#** > **Stile codice**  > **Preferenze campi** > **Preferisci readonly** |
|**Rimuovi cast non necessari**|Se selezionata, consente di rimuovere i cast inutili quando **Edit.FormatDocument** viene attivato.| N/D |
|**Rimuovi variabili non usate**|Se selezionata, consente di rimuovere le variabili non usate quando **Edit.FormatDocument** viene attivato.| N/D |

![Impostazioni di pulizia del codice per C# in Visual Studio](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Pagina Rientro

Le opzioni di rientro di questa pagina sono applicate quando il codice viene formattato automaticamente. Un esempio di formattazione automatica del codice è quando si incolla codice nel file con l'opzione **Formatta automaticamente dopo operazione Incolla** selezionata. (L'opzione **Formatta automaticamente dopo operazione Incolla** si trova in **Formattazione** > **Generale**.)

![Opzioni di rientro dell'editor di testo C# in Visual Studio](media/csharp-indentation-options.png)

> [!TIP]
> Sono disponibili impostazioni di rientro anche nella pagina di opzioni **Editor di testo** > **C#** > **Tabulazioni**. Le opzioni determinano solo il punto in cui l'editor del codice posiziona il cursore quando si preme **INVIO** alla fine di una riga.
>
> ![Opzioni di tabulazione dell'editor di testo C# in Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Vedere anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)