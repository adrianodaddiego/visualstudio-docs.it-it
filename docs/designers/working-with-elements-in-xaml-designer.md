---
title: Utilizzo di elementi in XAML Designer
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 1c3d0e7d30778580ac09bfd4476e44280c775a2c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844042"
---
# <a name="work-with-elements-in-xaml-designer"></a>Usare gli elementi nella finestra di progettazione XAML

Puoi aggiungere elementi come controlli, layout e forme alla tua app in XAML, nel codice o tramite la finestra di progettazione XAML. Questo argomento descrive come usare gli elementi nella finestra di progettazione XAML in Visual Studio o in Blend per Visual Studio.

## <a name="add-an-element-to-a-layout"></a>Aggiungere un elemento a un layout

Per *layout* si intende il processo di ridimensionamento e posizionamento degli elementi in un'interfaccia utente. Per posizionare gli elementi visivi, è necessario inserirli in una classe [Panel](/uwp/api/Windows.UI.Xaml.Controls.Panel) del layout. Una classe `Panel` contiene una proprietà figlio, ovvero una raccolta di tipi [FrameworkElement](/uwp/api/Windows.UI.Xaml.FrameworkElement). È possibile usare vari elementi figlio di `Panel`, ad esempio [Canvas](/uwp/api/Windows.UI.Xaml.Controls.Canvas), [StackPanel](/uwp/api/Windows.UI.Xaml.Controls.StackPanel) e [Grid](/uwp/api/Windows.UI.Xaml.Controls.Grid) come contenitori di layout e per posizionare e disporre gli elementi in una pagina.

Per impostazione predefinita, viene usato un pannello `Grid` come contenitore di layout di primo livello all'interno di una pagina o di un modulo. È possibile aggiungere pannelli di layout, controlli o altri elementi nel layout di pagina di primo livello.

Per aggiungere un elemento a un layout nella finestra di progettazione XAML, eseguire una delle operazioni seguenti:

- Fare doppio clic su un elemento nella **casella degli strumenti** oppure selezionare un elemento nella casella degli strumenti e premere **INVIO**.

- Trascinare un elemento dalla **casella degli strumenti** nella tavola da disegno.

- Nella **casella degli strumenti** fare clic su uno degli strumenti di disegno, ad esempio [Ellisse](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) o [Rettangolo](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) e disegnare un elemento nel pannello attivo.

## <a name="change-the-layering-order-of-elements"></a>Modificare l'ordine dei livelli degli elementi

In presenza di due elementi sulla tavola da disegno nella finestra di progettazione XAML, un elemento verrà visualizzato davanti all'altro nell'ordine di disposizione. Alla fine dell'elenco di elementi nella finestra Struttura documento si trova l'elemento in primo piano, eccetto quando è impostata la proprietà **ZIndex** per un elemento. Quando si inserisce un elemento in una pagina, un modulo o un contenitore di layout, l'elemento viene automaticamente posizionato davanti agli altri nell'elemento contenitore attivo. Per modificare l'ordine degli elementi, è possibile usare i comandi di **Ordina** o trascinare gli elementi nella struttura a oggetti nella finestra Struttura documento.

Per modificare l'ordine dei livelli, effettuare una delle operazioni seguenti:

- Nella finestra **Struttura documento** trascinare gli elementi verso l'alto o verso il basso per creare l'ordine dei livelli desiderato.

- Fare clic con il pulsante destro del mouse nella finestra Struttura documento o nella tavola da disegno per cui si vuole modificare l'ordine dei livelli, scegliere **Ordina** e fare clic su una delle opzioni seguenti:

   - **Porta in primo piano** per portare l'elemento davanti a tutti gli altri nell'ordine.

   - **Porta avanti** per portare l'elemento avanti di un livello nell'ordine.

   - **Porta indietro** per portare l'elemento indietro di un livello nell'ordine.

   - **Porta in secondo piano** per portare l'elemento dietro tutti gli altri nell'ordine.

   Modificare la proprietà **ZIndex** nella sezione **Layout** della finestra Proprietà. Per gli elementi che si sovrappongono, la proprietà **ZIndex** ha la precedenza sull'ordine degli elementi indicato nella finestra Struttura documento. Un elemento con un valore **ZIndex** maggiore viene visualizzato in primo piano quando gli elementi si sovrappongono.

## <a name="change-the-alignment-of-an-element"></a>Modificare l'allineamento di un elemento

È possibile allineare elementi nella tavola da disegno usando i comandi di menu o trascinando gli elementi sulle guide di allineamento.

Una *guida di allineamento* è un'indicazione visiva che agevola l'allineamento di un elemento in relazione ad altri elementi nell'app.

Per allineare due o più elementi tramite i comandi di menu:

1. Selezionare gli elementi da allineare. È possibile selezionare uno o più elementi tenendo premuto **CTRL** mentre li si selezionano.

2. Selezionare una delle proprietà seguenti in **HorizontalAlignment** nella sezione **Layout** della finestra Proprietà: **A sinistra**, **Al centro**, **A destra** o **Esteso**.

3. Selezionare una delle proprietà seguenti in **VerticalAlignment** nella sezione **Layout** della finestra Proprietà: **In alto**, **Al centro**, **In basso** o **Esteso**.

Per allineare due o più elementi usando le guide di allineamento, nella finestra di progettazione XAML trascinare o ridimensionare uno degli elementi in modo che il bordo sia allineato a un altro elemento.

Quando i bordi sono allineati, viene visualizzato un *limite di allineamento* per indicare l'allineamento. come linea tratteggiata rossa. I limiti di allineamento vengono visualizzati solo quando è abilitato l' **allineamento alle guide di allineamento** . Per un'illustrazione della tavola da disegno con un limite di allineamento, vedere [Creazione di un'interfaccia utente tramite la finestra di progettazione XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="change-an-elements-margins"></a>Modificare i margini di un elemento

I margini nella finestra di progettazione XAML determinano la quantità di spazio vuoto intorno a un elemento sulla tavola da disegno. I margini specificano, ad esempio, la quantità di spazio tra i bordi esterni di un elemento e i limiti di un pannello `Grid` che lo contiene. oppure la quantità di spazio tra gli elementi contenuti in `StackPanel`.

Per modificare i margini di un elemento nella finestra Proprietà:

1. Seleziona l'elemento di cui vuoi modificare i margini.

2. In **Layout** nella finestra Proprietà modificare il valore (in pixel o in unità di misura indipendenti dal dispositivo, che corrispondono all'incirca a 0,26 mm) di ogni proprietà **Margine** (**Superiore**, **Sinistro**, **Destro** o **Inferiore**).

Nella tavola da disegno, per modificare i margini di un elemento rispetto al contenitore di layout dell'elemento, fare clic sugli *Adorner dei margini* visualizzati attorno all'elemento quando l'elemento è selezionato e si trova all'interno di un contenitore di layout. Per un'illustrazione degli adorner dei margini, vedere [Creazione di un'interfaccia utente tramite la finestra di progettazione XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

Se uno strumento decorativo di un margine è aperto, verticalmente oppure orizzontalmente, il margine in questione non è impostato. Se invece è chiuso, il margine è impostato.

Quando si apre l'Adorner di un margine e il margine opposto non è impostato, questo viene impostato sul valore corretto in base alla posizione dell'elemento nella tavola da disegno. Per i margini opposti, come **Sinistro** e **Destro**, è sempre impostata almeno una proprietà.

> [!IMPORTANT]
> Gli elementi inseriti in alcuni contenitori di layout, ad esempio <xref:Windows.UI.Xaml.Controls.Canvas>, non dispongono di strumenti decorativi del margine. Gli elementi inseriti in un oggetto <xref:Windows.UI.Xaml.Controls.StackPanel> dispongono di strumenti decorativi del margine per i margini sinistro e destro oppure per quelli superiore e inferiore, in base all'orientamento di `StackPanel`.

## <a name="group-and-ungroup-elements"></a>Raggruppare e separare gli elementi

Se si raggruppano due o più elementi nella finestra di progettazione XAML, viene creato un nuovo contenitore di layout in cui vengono inseriti gli elementi raggruppati. Il posizionamento di due o più elementi nello stesso contenitore di layout semplifica le operazioni di selezione, spostamento e trasformazione del gruppo, in quanto gli elementi al suo interno possono essere gestiti come se fossero un solo elemento. Il raggruppamento è utile anche per identificare gli elementi in qualche modo correlati, ad esempio i pulsanti che compongono un elemento di navigazione. Quando si separano gli elementi, si elimina semplicemente il contenitore di layout nel quale erano posizionati.

Per raggruppare gli elementi in un nuovo contenitore di layout:

1. Selezionare gli elementi da raggruppare. Per selezionare più elementi, fare clic su ognuno tenendo premuto **CTRL**.

2. Fare clic con il pulsante destro del mouse sugli elementi selezionati, scegliere **Raggruppa** e fare clic sul tipo di contenitore di layout in cui si vuole inserire il gruppo.

    > [!TIP]
    > Se si seleziona <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer> per raggruppare gli elementi, questi vengono inseriti in un nuovo pannello <xref:Windows.UI.Xaml.Controls.Grid> all'interno di <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer>. Se separi gli elementi in uno di questi contenitori di layout, viene eliminato solo <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer>, non il pannello <xref:Windows.UI.Xaml.Controls.Grid>. Per eliminare il pannello `Grid`, separa nuovamente gli elementi.

Per separare gli elementi ed eliminare il layout, fare clic con il pulsante destro del mouse sul gruppo che si vuole separare e fare clic su **Separa**. È anche possibile raggruppare o separare elementi facendo clic con il pulsante destro del mouse sugli elementi selezionati nella finestra Struttura documento e scegliendo **Raggruppa** o **Separa**.

## <a name="reset-the-element-layout"></a>Reimpostare il layout dell'elemento

È possibile ripristinare i valori predefiniti per le proprietà di layout specifiche di un elemento usando i comandi di reimpostazione del layout. Questo comando consente di reimpostare il margine, l'allineamento, la larghezza, l'altezza e la dimensione di un elemento, separatamente o contemporaneamente.

Per reimpostare il layout dell'elemento, fare clic con il pulsante destro del mouse sull'elemento nella finestra Struttura documento o nella tavola da disegno e quindi scegliere **Layout** > **Reimposta** *NomeProprietà*, dove *NomeProprietà* è la proprietà che si vuole reimpostare (oppure scegliere **Layout** > **Reimposta tutto** per reimpostare tutte le proprietà di layout dell'elemento).

## <a name="see-also"></a>Vedere anche

- [Creare un'interfaccia utente tramite la finestra di progettazione XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
