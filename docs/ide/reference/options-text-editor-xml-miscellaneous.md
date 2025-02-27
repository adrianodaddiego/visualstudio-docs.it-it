---
title: Opzioni, Editor di testo, XML, Varie
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3421580251a6a871adba311fd609e881e088ebd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969215"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opzioni, Editor di testo, XML, Varie

Usare la pagina delle opzioni **Varie** per modificare le impostazioni di completamento automatico e dello schema per l'editor XML. Per accedere alle opzioni XML, Varie, scegliere **Strumenti** > **Opzioni** > **Editor di testo** > **XML**, quindi scegliere **Varie**.

## <a name="auto-insert"></a>Inserimento automatico

**Tag di chiusura**

L'editor di testo aggiunge tag di chiusura durante la creazione di elementi XML. Se si seleziona il tag di inizio di un elemento, l'editor inserisce il tag di chiusura corrispondente, incluso un prefisso di spazio dei nomi corrispondente. Per impostazione predefinita, questa casella di controllo è selezionata.

**Virgolette per gli attributi**

Quando si creano attributi XML, l'editor inserisce i caratteri `="` e `"` e posiziona l'accento circonflesso (**^**) all'interno delle virgolette. Per impostazione predefinita, questa casella di controllo è selezionata.

**Dichiarazioni dello spazio dei nomi**

L'editor inserisce automaticamente le dichiarazioni dello spazio dei nomi ovunque siano necessarie. Per impostazione predefinita, questa casella di controllo è selezionata.

**Altri markup (commenti, CDATA)**

Commenti, CDATA, DOCTYPE, istruzioni di elaborazione e altri markup vengono completati automaticamente. Per impostazione predefinita, questa casella di controllo è selezionata.

## <a name="network"></a>Rete

**Scarica automaticamente le DTD e gli schemi**

Gli schemi e le DTD (Document Type Definitions) vengono scaricati automaticamente dalle posizioni HTTP. Questa funzionalità usa System.Net con il rilevamento automatico dei server proxy abilitato. Per impostazione predefinita, questa casella di controllo è selezionata.

## <a name="outlining"></a>struttura

**Attiva modalità struttura all'apertura del file**

Attiva la funzionalità struttura quando un file è aperto. Per impostazione predefinita, questa casella di controllo è selezionata.

## <a name="caching"></a>Memorizzazione nella cache

**Schemi**

Specifica il percorso della cache degli schemi. Il pulsante **Sfoglia** consente di aprire la posizione corrente della cache dello schema in una nuova finestra. Il percorso predefinito è *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Vedere anche

- [Opzioni XML - Formattazione](options-text-editor-xml-formatting.md)
- [Strumenti XML in Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)