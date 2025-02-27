---
title: Opzioni, Editor di testo, XAML, Formattazione
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3ed364d9c8995a93acb0de8002bafefd603c2d71
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969254"
---
# <a name="options-text-editor-xaml-formatting"></a>Opzioni, Editor di testo, XAML, Formattazione

Usare la pagina delle proprietà **Formattazione** per specificare la formattazione di elementi e attributi nei documenti XAML. Per aprire la finestra di dialogo **Opzioni**, fare clic sul menu **Strumenti** e quindi su **Opzioni**. Per accedere alla finestra delle proprietà **Formattazione**, espandere **Editor di testo** > **XAML** > nodo **Formattazione**.

## <a name="auto-formatting-events"></a>Eventi di formattazione automatica

La formattazione automatica può verificarsi quando vengono rilevati gli eventi seguenti.

- Completamento di un tag di fine o un tag semplice.

- Completamento di un tag di inizio.

- Inserimento degli Appunti.

- Formattazione di comandi da tastiera.

È possibile specificare gli eventi che causano la formattazione automatica.

**Al completamento del tag di fine o del tag semplice**

La formattazione automatica si verifica quando si finisce di digitare un tag di fine o un tag semplice. Un tag semplice non include attributi, ad esempio `<Button />`.

**Al completamento del tag di inizio**

La formattazione automatica si verifica quando si finisce di digitare un tag di inizio.

**All'inserimento degli Appunti**

La formattazione automatica si verifica quando si incolla XAML dagli Appunti nella visualizzazione XAML.

## <a name="quotation-mark-style"></a>Stile virgolette

Questa impostazione indica se i valori di attributo sono racchiusi tra virgolette singole o doppie. Il formattatore automatico e il completamento automatico IntelliSense usano questa impostazione.

Dopo l'impostazione, questa opzione viene applicata solo agli attributi aggiunti successivamente usando la finestra di progettazione o manualmente nella visualizzazione XAML.

**Virgolette doppie (")**

I valori di attributo sono racchiusi tra virgolette doppie.
`<Button Name="button1">Hello</Button>`

**Virgolette singole (')**

I valori di attributo sono racchiusi tra virgolette singole.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Ritorno a capo dei tag

È possibile specificare una lunghezza di riga per il ritorno a capo dei tag. Quando il ritorno a capo dei tag è abilitato, verrà applicato il ritorno a capo appropriato a qualsiasi XAML aggiunto successivamente usando la finestra di progettazione.

**Testo a capo per i tag che eccedono la lunghezza specificata**

Specifica se il ritorno a capo viene applicato alle righe alla lunghezza di riga specificata da **Lunghezza**.

**Lunghezza**

Il numero di caratteri che una riga può contenere. Se necessario, alcune righe XAML possono superare la lunghezza di riga specificata.

## <a name="attribute-spacing"></a>Spaziatura attributi

Usare questa impostazione per controllare la disposizione degli attributi nel documento XAML

**Conserva i caratteri di fine riga e gli spazi tra gli attributi**

La formattazione automatica non viene applicata ai caratteri di fine riga e agli spazi tra gli attributi.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Inserisci uno spazio singolo tra gli attributi**

Gli attributi occupano una riga, con uno spazio che separa gli attributi adiacenti. Vengono applicate le impostazioni di ritorno a capo dei tag.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Posiziona ogni attributo su una riga diversa**

Ogni attributo occupa una riga. Questo risulta utile quando sono presenti molti attributi.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Posiziona il primo attributo sulla stessa riga del tag di inizio**

Se questa opzione è selezionata, il primo attributo viene visualizzato sulla stessa riga del tag di inizio dell'elemento.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Spaziatura elementi

Usare questa impostazione per controllare la disposizione degli elementi nel documento XAML.

**Conserva i caratteri di fine riga nel contenuto**

Le righe vuote nel contenuto dell'elemento non vengono rimosse.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Comprimi più righe vuote nel contenuto in una sola riga**

Le righe vuote nel contenuto dell'elemento vengono compresse in una singola riga.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Rimuovi le righe vuote nel contenuto**

Tutte le righe vuote nel contenuto dell'elemento vengono rimosse.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Vedere anche

- [XAML in WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)