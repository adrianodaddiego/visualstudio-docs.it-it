---
title: Presentazione delle funzionalità di Blend per Visual Studio
titleSuffix: ''
ms.date: 07/17/2017
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a27799eb9c22ec633d5c8d8604fe58d6924cd623
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847325"
---
# <a name="blend-for-visual-studio-overview"></a>Panoramica di Blend per Visual Studio

Blend per Visual Studio consente di progettare applicazioni Windows e Web basate su XAML. Offre la stessa esperienza di progettazione XAML di base disponibile in Visual Studio e aggiunge finestre di progettazione visive per attività avanzate, quali animazioni e comportamenti. Per un confronto tra Blend e Visual Studio, vedere [Progettare XAML in Visual Studio e Blend per Visual Studio](../designers/designing-xaml-in-visual-studio.md).

Blend per Visual Studio è un componente di Visual Studio. Per installare Blend, nel **programma di installazione di Visual Studio** scegliere il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)** o **Sviluppo per desktop .NET**. Entrambi questi carichi di lavoro includono il componente Blend per Visual Studio.

![Componenti del carico di lavoro UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Componenti del carico di lavoro Sviluppo per desktop .NET](media/installer-dotnet-desktop.png)

Se non si ha familiarità con Blend per Visual Studio, dedicare alcuni minuti all'esame delle funzionalità specifiche dell'area di lavoro. In questo argomento è disponibile una breve panoramica.

> [!NOTE]
> Per una panoramica delle funzionalità di progettazione, ad esempio la tavola da disegno, la finestra **Struttura documento** e la finestra **Dispositivo**, vedere [Creazione di un'interfaccia utente tramite la finestra di progettazione XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="tools-panel"></a>Pannello Strumenti

È possibile usare il pannello **Strumenti** in Blend per Visual Studio per creare e modificare oggetti nell'applicazione. Il pannello **Strumenti** è visualizzato sul lato sinistro della finestra di progettazione XAML quando è aperto un file *XAML*.

Per creare oggetti, si seleziona lo strumento e si disegna sulla tavola da disegno con il mouse.

![Pannello Strumenti in Blend per Visual Studio](../designers/media/blend5toolspanel.png)

> [!TIP]
> Alcuni degli strumenti nel pannello **Strumenti** presentano varianti (contrassegnate con le lettere da A a F nella figura). Per accedere a queste varianti, fare clic con il pulsante destro del mouse o fare clic e tenere premuto sullo strumento.
>
> ![Varianti dello strumento Forma in Blend per Visual Studio](media/rectangle-shape-tool-blend.png)

|||||
|-|-|-|-|
|![Strumenti di selezione](../designers/media/b1_1.png)|**Strumenti di selezione** Selezionare oggetti e percorsi.<br /><br /> Usare lo strumento **Selezione diretta** per selezionare gli oggetti annidati e i segmenti di percorso.|![Callout A](../designers/media/b5_label_a.png)|**Strumenti Sfumatura e tratto**|
|![Strumenti di visualizzazione](../designers/media/b1_2.png)|**Strumenti di visualizzazione** Consente di modificare la visualizzazione della tavola da disegno, ad esempio per la panoramica e lo zoom.|![Callout B](../designers/media/b5_label_b.png)|**Strumenti per i tracciati**|
|![Strumento per i pennelli](../designers/media/b1_3.png)|**Strumenti per i pennelli** Consente di usare gli attributi visivi di un oggetto, ad esempio cambiare un pennello, disegnare un oggetto o selezionare gli attributi di un oggetto da applicare a un altro oggetto.|![Callout C](../designers/media/b5_label_c.png)|**Strumenti per le forme**|
|![Strumenti per gli oggetti](../designers/media/b1_4.png)|**Strumenti per gli oggetti** Consente di disegnare gli oggetti più comuni sulla tavola da disegno, ad esempio tracciati, forme, pannelli di layout, testo e controlli.|![Callout D](../designers/media/b5_label_d.png)|**Pannelli di layout**|
|![Strumenti per gli asset](../designers/media/b1_5.png)|**Strumenti per gli asset** Consente di accedere al pannello **Assets** e visualizzare l'ultimo asset usato nella libreria.|![Callout E](../designers/media/b5_label_e.png)|**Controlli testo**|
|||![Callout F](../designers/media/b5_label_f.png)|**Controlli comuni**|

## <a name="assets-window"></a>Finestra Asset

La finestra **Asset** contiene tutti i controlli disponibili ed è simile alla **casella degli strumenti** di Visual Studio. Oltre ai controlli, nella finestra **Asset** è disponibile tutto ciò che può essere aggiunto alla tavola da disegno, inclusi gli stili, gli elementi multimediali, i comportamenti e gli effetti. Per aprire la finestra **Asset**, scegliere **Visualizza** > **Finestra Asset** oppure premere **CTRL**+**ALT**+**X**.

![Finestra Asset in Blend per Visual Studio](../designers/media/blend5_assets_panel.png)

|||
|-|-|
|![](../designers/media/b1_1.png)|**Casella di ricerca** Digitare testo nella casella **Cerca** per filtrare l'elenco di asset.|
|![Modalità griglia e modalità elenco](../designers/media/b1_2.png)|**Modalità griglia e Modalità elenco** Consente di passare dalla visualizzazione **Modalità griglia** alla visualizzazione **Modalità elenco** e viceversa.|
|![Categorie di asset](../designers/media/b1_3.png)|**Categorie di asset** Fare clic su una categoria o sottocategoria per visualizzare l'elenco di asset corrispondente.|
|![Stili](../designers/media/b1_4.png)|**Stili** Consente di visualizzare tutti gli stili disponibili nel dizionario risorse.|
|![Description](../designers/media/b1_5.png)|**Descrizione** Consente di visualizzare una descrizione della categoria o sottocategoria di asset selezionata.|

## <a name="objects-and-timeline-window"></a>Finestra Oggetti e sequenza temporale

Usare questa finestra per organizzare gli oggetti nella tavola da disegno e, se si vuole, per animarli. Per aprire la finestra **Oggetti e sequenza temporale**, scegliere **Visualizza** > **Oggetti e sequenza temporale** oppure premere **CTRL**+**W**, **U**.

![Finestra Oggetti e sequenza temporale in modalità animazione](../designers/media/b5_object_timeline_animation.png)

|||
|-|-|
|![Visualizzazione oggetti](../designers/media/b1_1.png)|**Visualizzazione Oggetti** Consente di visualizzare una struttura ad albero visuale di un documento. È possibile accedere a diversi livelli di dettaglio. È anche possibile aggiungere livelli per organizzare ulteriormente gli oggetti nella tavola da disegno. In questo modo è possibile bloccarli e nasconderli come gruppi.|
|![Indicatore della modalità di registrazione](../designers/media/b1_2.png)|**Indicatore della modalità di registrazione** Consente di verificare se è in corso la registrazione delle modifiche delle proprietà in una sequenza temporale.|
|![Selezione storyboard](../designers/media/b1_3.png)|**Selezione storyboard** Consente di visualizzare un elenco degli storyboard creati.|
|![Chiudi storyboard](../designers/media/b1_4.png)|**Chiudere lo storyboard** Consente di chiudere lo storyboard corrente.|
|![Opzioni di storyboard](../designers/media/b1_5.png)|**Opzioni di storyboard** Consente di creare, duplicare, invertire, eliminare, rinominare o chiudere uno storyboard.|
|![Controlli di riproduzione](../designers/media/b1_6.png)|**Controlli di riproduzione** Consente di esplorare la sequenza temporale. Per spostarsi nella sequenza temporale, o *eseguire lo scrubbing*, è anche possibile trascinare l'indicatore di riproduzione.|
|![Reimposta l'ambito](../designers/media/b1_7.png)|**Reimposta l'ambito** Consente di reimpostare l'ambito della visualizzazione oggetti sull'oggetto radice o ambito precedente. È possibile solo quando si modifica uno stile o modello.|
|![Registra fotogramma chiave](../designers/media/b1_8.png)|**Registra fotogramma chiave** Consente di registrare uno snapshot delle proprietà dell'oggetto selezionato nell'istante corrente.|
|![Opzioni snapping](../designers/media/b1_9.png)|**Opzioni snapping** Consente di impostare l'allineamento della sequenza temporale, la risoluzione di snap e disattivare l'allineamento della sequenza temporale.|
|![Mostra/Nascondi Blocca/Sblocca](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Mostra/Nascondi**, **Blocca/Sblocca** Consente di visualizzare o nascondere le opzioni di visibilità e blocco della visualizzazione degli oggetti.|
|![Posizione indicatore di riproduzione nella sequenza temporale](../designers/media/b1_11.png)|**Posizione indicatore di riproduzione nella sequenza temporale** Consente di visualizzare il tempo corrente in millisecondi. In questo campo è possibile immettere direttamente un valore di tempo per passare a un istante specifico. La precisione dipende dalla risoluzione di snap impostata in **Opzioni snapping**.|
|![Indicatore di riproduzione](../designers/media/b1_12.png)|**Indicatore di riproduzione** Consente di determinare il punto temporizzato in cui si trova l'animazione. L'indicatore di riproduzione può essere trascinato lungo la sequenza temporale per visualizzare l'animazione in anteprima.|
|![Fotogrammi chiave impostati su sequenze temporali](../designers/media/b1_13.png)|**Fotogrammi chiave impostati su sequenze temporali** Consente di modificare un valore di proprietà in un istante specifico.|
|![Modifica dell'ordine degli oggetti](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Modifica dell'ordine degli oggetti** Consente di impostare l'ordine di visualizzazione degli oggetti. Fare clic su questo pulsante per disporre gli oggetti nella visualizzazione struttura secondo l'ordine Z (da primo a ultimo) o in base all'ordine di markup, ovvero l'ordine in cui compaiono nella visualizzazione **XAML**.|
|![Zoom sequenza temporale](../designers/media/b1_15.png)|**Zoom sequenza temporale** Consente di impostare la risoluzione di zoom della sequenza temporale. Lo zoom avanti permette di modificare un'animazione a un maggior livello di dettaglio, mentre lo zoom indietro permette di ottenere una panoramica del comportamento di un'animazione su periodi di tempo più lunghi. Se si applica lo zoom avanti, ma non è possibile impostare un fotogramma chiave nella posizione corrispondente all'istante desiderato, verificare che la risoluzione di snap sia sufficientemente elevata.|
|![Callout 16](../designers/media/b5_label_16.png)|**Area di composizione della sequenza temporale** Consente di visualizzare la sequenza temporale e spostare i fotogrammi chiave trascinandoli o usando i relativi menu di scelta rapida.|

## <a name="properties-window"></a>Finestra Proprietà

Usare questa finestra per visualizzare e modificare le proprietà di un oggetto. È anche possibile impostarle direttamente sulla tavola da disegno. In questo caso, le modifiche alle proprietà si riflettono nella finestra **Proprietà**. Per aprire la finestra **Proprietà**, scegliere **Visualizza** > **Finestra Proprietà** o premere **CTRL**+**W**, **P**.

![Finestra Proprietà in Blend per Visual Studio](../designers/media/blend5_properties_panel.png)

**Categorie** Consente di espandere e comprimere le categorie delle proprietà. Fare clic su **Espandi** ![Espandi](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png) e **Comprimi** ![Comprimi](../designers/media/b5_collapse_button.png) per visualizzare o nascondere i dettagli della categoria.

|||
|-|-|
|![Nome e tipo](../designers/media/b1_1.png)|**Nome e tipo** Consente di visualizzare l'icona, il nome e il tipo dell'oggetto selezionato.|
|![Disponi per](../designers/media/b1_2.png)|**Disponi per** Consente di ordinare alfabeticamente le proprietà per nome, database di origine o categoria.|
|![Proprietà dei pennelli](../designers/media/b1_3.png)|**Proprietà dei pennelli** Consente di configurare le proprietà visive dei pennelli, ad esempio riempimento, tratto e primo piano.|
|![Editor dei colori](../designers/media/b1_4.png)|**Editor dei colori** Consente di usare pennelli a tinta unita e con sfumatura.|
|![Selezione colori](../designers/media/b1_5.png)|**Selezione colori** Consente di selezionare un colore.|
|![Caselle del colore](../designers/media/b1_6.png)|**Caselle del colore** Consente di visualizzare il colore iniziale, il colore corrente e l'ultimo colore|
|![Contagocce](../designers/media/b1_7.png)|**Contagocce** Consente di usare il colore di qualsiasi elemento sullo schermo. Il **Contagocce colore** è disponibile quando è selezionato il **pennello tinta unita**. Il **Contagocce sfumatura** è disponibile quando è selezionato il **pennello sfumatura**.|
|![Proprietà ed eventi](../designers/media/b1_8.png)|**Proprietà ed eventi** Consente di impostare le proprietà o scegliere gli eventi per un elemento selezionato.|
|![Casella di ricerca](../designers/media/b1_9.png)|**Casella di ricerca** Consente di cercare le proprietà. Filtrare le proprietà visualizzate digitando nella casella **Cerca**.|
|![Schede Editor del pennello](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Schede Editor del pennello**. Consente di selezionare un editor del pennello. È possibile scegliere **Nessun pennello**, **Pennello tinta unita**, **Pennello sfumato**, **Pennello tessera** o **Risorsa pennello**.|
|![Risorse colore](../designers/media/b1_11.png)|**Risorse colore** Consente di applicare lo stesso colore a proprietà diverse. La scheda **Risorse colore** include **Risorse locali** e **Risorse di sistema**.|
|![Spazio colori RGB](../designers/media/b1_12.png)|**Spazio colori RGB** Consente di modificare il colore cambiando i valori per gli editor di numero **R**, **G** o **B** (rosso, verde, blu).|
|![Canale alfa](../designers/media/b1_13.png)|**Canale alfa** Consente di modificare il valore alfa usando l'editor di numero accanto ad **A**.|
|![Converti colore in risorsa](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Converti colore in risorsa** Consente di convertire il colore selezionato in una risorsa di colore. Le risorse di colore sono disponibili quando si fa clic sulla scheda Risorse colore.|
|![](../designers/media/b1_15.png)|**Valore hex** Consente di visualizzare il valore esadecimale del colore visualizzato.|
|![Callout 16](../designers/media/b5_label_16.png)|**Cursore sfumatura** Viene visualizzato solo se è selezionato un pennello sfumato.|
|![Mostra proprietà avanzate](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png)|**Mostra proprietà avanzate** Consente di visualizzare le categorie di proprietà che vengono usate meno.|

## <a name="see-also"></a>Vedere anche

- [Inserire i controlli e modificarne il comportamento](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [Animare oggetti](../designers/animate-objects-in-xaml-designer.md)
- [Disegnare forme e tracciati](../designers/draw-shapes-and-paths.md)
- [Progettazione di XAML in Visual Studio e Blend per Visual Studio](../designers/designing-xaml-in-visual-studio.md)
