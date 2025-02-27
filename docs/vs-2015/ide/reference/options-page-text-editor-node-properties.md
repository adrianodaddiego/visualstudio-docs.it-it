---
title: Pagina delle opzioni, Proprietà del nodo Editor di testo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d127aaa85cdd8da9e5daebe5c7841e0f6e85238d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674866"
---
# <a name="options-page-text-editor-node-properties"></a>Pagina delle opzioni, Proprietà del nodo Editor di testo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In questo documento vengono descritte alcune pagine, o raccolte di proprietà, associate alla categoria **Editor di testo**, `DTE.Properties("TextEditor", <Property Page>)`, della finestra di dialogo **Opzioni**. Il titolo di ogni sottosezione rappresenta la chiamata utilizzata per accedere alla raccolta `Properties` e nella tabella di ogni sottosezione sono elencate le proprietà della raccolta.  
  
 Le macro di Visual Basic in [Controllo delle impostazioni relative alle opzioni](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) spiegano come visualizzare le opzioni correnti e i relativi valori per ogni pagina della finestra di dialogo **Opzioni**.  
  
## <a name="general"></a>Generale  
 `DTE.Properties("TextEditor", "General")`  
  
|Nome degli elementi delle proprietà|Value|Description|  
|------------------------|-----------|-----------------|  
|GoToAnchorAfterEscape|Get/Set (Boolean)|Se `True`, premendo escape in presenza di una selezione si determina lo spostamento del punto di inserimento nella posizione in cui è iniziata l'azione che ha creato la selezione. `False` consente di spostare il punto di inserimento all'altra estremità della selezione.|  
|DragNDropTextEditing|Get/Set (Boolean)|Determina se è possibile trascinare un'area di testo selezionata da una posizione a un'altra nel documento tramite operazioni Copia o Taglia/Incolla.|  
|HorizontalScrollBar|Get/Set (Boolean)|Determina se esiste una barra di scorrimento orizzontale nelle finestre dell'editor.|  
|VerticalScrollBar|Get/Set (Boolean)|Determina se esiste una barra di scorrimento verticale nelle finestre dell'editor.|  
|SelectionMargin|Get/Set (Boolean)|Determina la presenza di spazio a sinistra del riquadro di testo per speciali operazioni di selezione, creazione di icone dei punti di interruzione e così via.|  
|MarginIndicatorBar|Get/Set (Boolean)|Determina se esiste una riga verticale che divide il margine sinistro del riquadro di testo dal corpo principale del riquadro di testo.|  
|UndoCaretActions|Get/Set (Boolean)|Se `True`. le operazioni di annullamento includono lo spostamento del punto di inserimento, i comandi di selezione e così via, oltre alle azioni di modifica del buffer.|  
|AutoDelimiterHighlighting|Get/Set (Boolean)|Determina se la digitazione di un delimitatore di chiusura causa la selezione del delimitatore di apertura da parte dell'editor. L'editor formatta sempre in grassetto il delimitatore di apertura indipendentemente dal valore di questa proprietà.|  
|EditorEmulation|Get/Set (Enum)||  
|DetectUTF8WithoutSignature|Get/Set (Boolean)|Determina se in un file viene utilizzata la codifica UTF-8 quando non è presente una firma di codifica.|  
|TrackChanges|Get/Set (Boolean)||  
  
## <a name="plain-text"></a>Testo normale  
 `DTE.Properties("TextEditor", "PlainText")`  
  
 Le opzioni dell'editor `PlainText` influiscono sulle impostazioni dell'editor al momento della modifica dei file di testo. Ogni linguaggio di programmazione e il pacchetto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usano impostazioni specifiche dell'**editor di testo**. Ad esempio, per visualizzare o modificare le impostazioni dell'editor di [!INCLUDE[csprcs](../../includes/csprcs-md.md)], utilizzare `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")`. Per le impostazioni dell'editor di **Script SQL** usare `DTE.Properties("TextEditor", "SQL ")`.  
  
|Nome degli elementi delle proprietà|Value|Description|  
|------------------------|-----------|-----------------|  
|AutoListMembers|Get/Set (Boolean)|Determina se l'elenco di membri disponibile viene visualizzato automaticamente quando viene digitato un punto dopo un riferimento a una variabile.|  
|AutoListParams|Get/Set (Boolean)|Determina se la descrizione di un elenco di argomenti viene visualizzata automaticamente quando viene digitata una parentesi "(" dopo il nome di una funzione.|  
|HideAdvancedMembers|Get/Set (Boolean)|Determina se nel completamento dell'istruzione vengono elencati tutti i membri o solo quelli comunemente utilizzati.|  
|VirtualSpace|Get/Set (Boolean)|Determina se gli spazi vengono visualizzati come grafica. Impostando questo valore su `true`, l'elemento della proprietà `WordWrap` presente in questo elenco verrà impostato su `false`.|  
|WordWrap|Get/Set (Boolean)|Determina se nella visualizzazione esiste un ritorno a capo delle righe lunghe alla fine delle parole. Impostando questo valore su `true`, l'elemento della proprietà `VirtualSpace` presente in questo elenco verrà impostato su `false`.|  
|WordWrapGlyphs|Get/Set (Boolean)|Consente di visualizzare un glifo alla fine di una riga, a indicare un ritorno a capo automatico nella riga successiva.|  
|EnableLeftClickForURLs|Get/Set (Boolean)|Determina se nell'editor vengono sottolineati gli URL e se è sufficiente fare clic sul pulsante sinistro del mouse per passare all'URL nel browser registrato del sistema.|  
|IndentStyle|Get/Set (<xref:EnvDTE.vsIndentStyle>) |Determina lo stile di rientro: Predefinito, Intelligenti o Nessuno.|  
|TabSize|Get/Set (Long)|Rappresenta il numero di spazi che equivale a una tabulazione. L'impostazione di un intero esterno all'intervallo compreso tra 1 e 60 (inclusi) ha esito negativo.|  
|InsertTabs|Get/Set (Boolean)|Se `True`, i caratteri di tabulazione vengono utilizzati per i rientri.|  
|IndentSize|Get/Set (Long)|Rappresenta il numero di spazi che equivale a un livello di rientro. L'impostazione di un valore integer esterno all'intervallo compreso tra 1 e 60 (inclusi) ha esito negativo.|  
|ShowLineNumbers|Get/Set (Boolean)|Determina se nella visualizzazione del documento principale dell'editor sono presenti i numeri delle righe lungo il margine sinistro.|  
|ShowNavigationBar|Get/Set (Boolean)|Determina se nella parte superiore delle finestre dell'editor vengono visualizzati gli elenchi a discesa e i pulsanti.|  
|CutCopyBlankLines|Get/Set (Boolean)|Consente di tagliare o copiare righe vuote quando queste vengono selezionate.|  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo delle impostazioni relative alle opzioni](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Determinazione dei nomi degli elementi delle proprietà nelle pagine delle opzioni](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Pagina delle opzioni, Proprietà del nodo Ambiente](../../ide/reference/options-page-environment-node-properties.md)   
 [Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
