---
title: Opzioni, Editor di testo, XAML, Formattazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8f820ac16667a9550db17bc252c547f16b81e70b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696015"
---
# <a name="options-text-editor-xaml-formatting"></a>Opzioni, Editor di testo, XAML, Formattazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usare la pagina delle proprietà **Formattazione** per specificare la formattazione di elementi e attributi nei documenti XAML. Per aprire la finestra di dialogo **Opzioni**, fare clic sul menu **Strumenti** e quindi su **Opzioni**. Per accedere alla finestra delle proprietà **Formattazione**, espandere **Editor di testo**, **XAML** e il nodo **Formattazione**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="auto-formatting-events"></a>Eventi di formattazione automatica
La formattazione automatica può verificarsi quando vengono rilevati gli eventi seguenti.

- Completamento di un tag di fine o un tag semplice.

- Completamento di un tag di inizio.

- Inserimento degli Appunti.

- Formattazione di comandi da tastiera.

  È possibile specificare gli eventi che causano la formattazione automatica.

|||
|-|-|
|**Al completamento del tag di fine o del tag semplice**|La formattazione automatica si verifica quando si finisce di digitare un tag di fine o un tag semplice. Un tag semplice non include attributi, ad esempio `<Button />`.|
|**Al completamento del tag di inizio**|La formattazione automatica si verifica quando si finisce di digitare un tag di inizio.|
|**All'inserimento degli Appunti**|La formattazione automatica si verifica quando si incolla XAML dagli Appunti nella visualizzazione XAML.|

## <a name="quotation-mark-style"></a>Stile virgolette
Questa impostazione indica se i valori di attributo sono racchiusi tra virgolette singole o doppie. Il formattatore automatico e il completamento automatico IntelliSense usano questa impostazione.

Dopo l'impostazione, questa opzione viene applicata solo agli attributi aggiunti successivamente usando la finestra di progettazione o manualmente nella visualizzazione XAML.

|||
|-|-|
|**Virgolette doppie (")**|I valori di attributo sono racchiusi tra virgolette doppie.<br /><br /> `<Button Name="button1">Hello</Button>`|
|**Virgolette singole (')**|I valori di attributo sono racchiusi tra virgolette singole.<br /><br /> `<Button Name='button1'>Hello</Button>`|

## <a name="tag-wrapping"></a>Ritorno a capo dei tag
È possibile specificare una lunghezza di riga per il ritorno a capo dei tag. Quando il ritorno a capo dei tag è abilitato, verrà applicato il ritorno a capo appropriato a qualsiasi XAML aggiunto successivamente usando la finestra di progettazione.

|||
|-|-|
|**Testo a capo per i tag che eccedono la lunghezza specificata**|Specifica se il ritorno a capo viene applicato alle righe alla lunghezza di riga specificata da **Lunghezza**.|
|**Lunghezza**|Il numero di caratteri che una riga può contenere. Se necessario, alcune righe XAML possono superare la lunghezza di riga specificata.|

## <a name="attribute-spacing"></a>Spaziatura attributi
Usare questa impostazione per controllare la disposizione degli attributi nel documento XAML

|||
|-|-|
|**Conserva i caratteri di fine riga e gli spazi tra gli attributi**|La formattazione automatica non viene applicata ai caratteri di fine riga e agli spazi tra gli attributi.<br /><br /> `<Button Height="23" Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Inserisci uno spazio singolo tra gli attributi**|Gli attributi occupano una riga, con uno spazio che separa gli attributi adiacenti. Vengono applicate le impostazioni di ritorno a capo dei tag.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|
|**Posiziona ogni attributo su una riga diversa**|Ogni attributo occupa una riga. Ciò è utile quando presenti molti attributi.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Posiziona il primo attributo sulla stessa riga del tag di inizio**|Se questa opzione è selezionata, il primo attributo viene visualizzato sulla stessa riga del tag di inizio dell'elemento.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|

## <a name="element-spacing"></a>Spaziatura elementi
Usare questa impostazione per controllare la disposizione degli elementi nel documento XAML

|                                                               |                                                                                                                                                                                       |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Conserva i caratteri di fine riga nel contenuto**                             | Le righe vuote nel contenuto dell'elemento non vengono rimosse.<br /><br /> `<Grid>`<br /><br /><br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>\`   |
| **Comprimi più righe vuote nel contenuto in una sola riga** | Le righe vuote nel contenuto dell'elemento vengono compresse in una singola riga.<br /><br /> `<Grid>`<br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>` |
| **Rimuovi le righe vuote nel contenuto**                             | Tutte le righe vuote nel contenuto dell'elemento vengono rimosse.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`                                        |

## <a name="auto-insert"></a>Inserimento automatico
Usare questa impostazione per controllare la generazione automatica di tag e virgolette.

|||
|-|-|
|**Tag di chiusura**|Specifica se il tag di chiusura di un elemento viene generato automaticamente quando si chiude il tag di apertura con il carattere maggiore di (>).|
|**Virgolette per gli attributi**|Specifica se vengono generate le virgolette quando un valore di attributo viene selezionato dall'elenco a discesa Completamento istruzioni.|
|**Parentesi graffe di chiusura per MarkupExtensions**|Specifica se una parentesi graffa di chiusura dell'estensione del markup (}) viene generata automaticamente quando si digita il carattere di parentesi graffa di apertura ({).|
|**Virgole per separare i parametri di MarkupExtension**|Specifica se vengono generate le virgole quando si digita più di un parametro in un'estensione di markup.|

## <a name="default-view"></a>Visualizzazione predefinita
Usare questa impostazione per verificare se la visualizzazione Progettazione appare quando vengono caricati documenti XAML.

|||
|-|-|
|**Documenti sempre aperti nella visualizzazione XAML completo**|Specifica se i documenti XAML vengono visualizzati solo nella visualizzazione XAML, senza la visualizzazione progettazione. È utile per il caricamento dei documenti di grandi dimensioni.|

## <a name="toolbox"></a>Casella degli strumenti
Usare questa impostazione per specificare se i controlli utente e controlli personalizzati vengono visualizzati nella casella degli strumenti.

|||
|-|-|
|**Inserisci automaticamente elementi della casella degli strumenti**|Specifica se i controlli utente e i controlli personalizzati della soluzione corrente vengono visualizzati automaticamente nella casella degli strumenti.|

## <a name="see-also"></a>Vedere anche
[XAML in WPF](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)  
[Procedura: Modificare le impostazioni visualizzazione XAML](https://msdn.microsoft.com/aee87c79-ca01-4f84-8fb7-a9e47048ee47)  
[Procedure dettagliate relative all'uso di XAML e del codice](https://msdn.microsoft.com/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
