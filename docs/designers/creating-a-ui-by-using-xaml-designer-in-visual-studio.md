---
title: Creazione di un'interfaccia utente tramite la finestra di progettazione XAML
ms.date: 03/28/2019
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3cd26f35111fc2e79290b30e7ae488b268e558d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899427"
---
# <a name="create-a-ui-by-using-xaml-designer-in-visual-studio"></a>Creare un'interfaccia utente tramite la finestra di progettazione XAML in Visual Studio

La finestra di progettazione XAML in Visual Studio offre un'interfaccia visiva per semplificare la progettazione di app per Windows e per il Web. È possibile creare interfacce utente per le app trascinando i controlli dalla **Casella degli strumenti** e impostando le proprietà nella finestra **Proprietà** . È anche possibile modificare il codice XAML direttamente nella visualizzazione XAML.

Per attività di progettazione XAML avanzate quali animazioni e comportamenti, vedere [Creating a UI by using Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md). Per un confronto tra gli strumenti, vedere anche [Progettare XAML in Visual Studio e Blend per Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="xaml-designer-workspace"></a>Area di lavoro della finestra di progettazione XAML

L'area di lavoro della finestra di progettazione XAML è costituita da alcuni elementi dell'interfaccia visiva, ad esempio la **tavola da disegno**, l'**Editor XAML**, la finestra **Dispositivo**, la finestra **Struttura documento** e la finestra **Proprietà**. Per aprire la finestra di progettazione XAML, fare clic con il pulsante destro del mouse su un file XAML in **Esplora soluzioni** , quindi scegliere **Progettazione visualizzazioni**.

## <a name="authoring-views"></a>Visualizzazioni per la creazione

La finestra di progettazione XAML include una visualizzazione XAML e una visualizzazione Progettazione sincronizzata del markup XAML dell'app sottoposto a rendering. Con un file XAML aperto in Visual Studio, è possibile spostarsi tra la visualizzazione Progettazione e la visualizzazione XAML mediante le schede **Progettazione** e **XAML** . È possibile usare il pulsante **Scambia riquadri** per visualizzare in primo piano alternativamente la tavola da disegno o l'Editor XAML.

Nella visualizzazione Progettazione la finestra che include la *tavola da disegno* è la finestra attiva ed è possibile usarla come area di lavoro principale. Permette di progettare visivamente una pagina nell'app, aggiungendo o disegnando elementi e quindi modificandoli. Per altre informazioni, vedi [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md). Questa figura mostra la tavola da disegno nella visualizzazione Progettazione.

![Visualizzazione Progettazione della finestra di progettazione XAML](../designers/media/xaml_editor_design_view.png)

Nella tavola da disegno sono disponibili le funzionalità seguenti:

**Guide di allineamento**

Le guide di allineamento sono *limiti di allineamento* , visualizzati sotto forma di linee tratteggiate rosse, per indicare quando i bordi dei controlli sono allineati o quando le linee di base del testo sono allineate. I limiti di allineamento vengono visualizzati solo quando è abilitato l' **allineamento alle guide di allineamento** .

**Sbarre della griglia**

Le sbarre`Grid` consentono di gestire righe e colonne in un pannello [Grid](/uwp/api/Windows.UI.Xaml.Controls.Grid) . È possibile creare ed eliminare righe e colonne e modificare le rispettive larghezze e altezze. La sbarra verticale della griglia, visualizzata nel lato sinistro della tavola da disegno, viene usata per le righe, mentre la sbarra orizzontale, visualizzata in alto, viene usata per le colonne.

**Strumenti decorativi griglia**

Uno strumento decorativo griglia viene visualizzato sotto forma di triangolo a cui è collegata una linea verticale o orizzontale sulla barra di scorrimento della griglia. Quando si trascina uno strumento decorativo griglia, le larghezze o altezze delle colonne o righe adiacenti vengono aggiornate in base allo spostamento del mouse.

Gli strumenti decorativi griglia vengono usati per controllare la larghezza e l'altezza delle righe e delle colonne di una griglia. È possibile aggiungere una nuova colonna o riga facendo clic sulle barre di scorrimento della griglia. Quando si aggiunge una nuova linea di riga o colonna per un pannello Griglia che include due o più colonne o righe, una barra degli strumenti ridotta viene visualizzata all'esterno della barra di scorrimento e permette di impostare esplicitamente la larghezza e l'altezza. La barra degli strumenti ridotta permette di configurare le opzioni di ridimensionamento per le righe e le colonne della griglia.

**Quadratini di ridimensionamento**

I quadratini di ridimensionamento vengono visualizzati sui controlli selezionati e ne permettono il ridimensionamento. Quando si ridimensiona un controllo, vengono in genere visualizzati i valori relativi a larghezza e altezza per semplificare il ridimensionamento del controllo. Per altre informazioni sulla modifica dei controlli nella visualizzazione **Progettazione**, vedere [Utilizzo di elementi in XAML Designer](../designers/working-with-elements-in-xaml-designer.md).

**Margini**

I margini rappresentano la quantità di spazio fisso tra il bordo di un controllo e il bordo del rispettivo contenitore. È possibile impostare i margini di un controllo usando le proprietà [Margin](/uwp/api/windows.ui.xaml.frameworkelement.margin) in **Layout** nella finestra Proprietà.

**Strumenti decorativi del margine**

È possibile usare gli strumenti decorativi del margine per modificare i margini di un elemento in relazione al rispettivo contenitore di layout. Se uno strumento decorativo del margine è aperto, il margine non viene impostato e viene visualizzata una catena interrotta. Se il margine non è impostato, gli elementi restano al proprio posto quando il contenitore di layout viene ridimensionato in fase di esecuzione. Se uno strumento decorativo del margine viene chiuso, viene visualizzata una catena ininterrotta e gli elementi vengono spostati insieme al margine quando il contenitore di layout viene ridimensionato in fase di esecuzione (il margine resta fisso).

**Handle degli elementi**

È possibile modificare un elemento usando i rispettivi handle visualizzati sulla tavola da disegno quando si sposta il puntatore sugli angoli della casella blu che circonda l'elemento. Gli handle consentono di ruotare, ridimensionare, capovolgere, spostare o aggiungere un raggio dell'angolo all'elemento. Il simbolo per l'handle dell'elemento varia in base alla funzione e cambia a seconda della posizione esatta del puntatore. Se gli handle non sono visibili, verificare che l'elemento sia selezionato.

Nella visualizzazione **Progettazione** sono disponibili comandi aggiuntivi della tavola da disegno nell'area inferiore sinistra della schermata, come illustrato di seguito:

![Comandi della visualizzazione Progettazione](../designers/media/xaml_editor_design_controls.png)

Nella barra degli strumenti sono disponibili i comandi seguenti:

**Zoom**

Lo zoom consente di ridimensionare l'area di progettazione. È possibile ingrandire dal 12,5% all'800% o selezionare opzioni come **Larghezza pagina** e **Adatta tutto**.

**Mostra/Nascondi griglia di allineamento**

Visualizza o nasconde la griglia di allineamento che mostra le griglie. Le griglie vengono usate quando è abilitato lo **snapping sulle linee della griglia** o lo **snapping sulle guide di allineamento**.

**Attiva/Disattiva allineamento alla griglia**

Se è abilitato l'**allineamento alla griglia**, quando si trascina un elemento sulla tavola da disegno l'elemento tende ad allinearsi alle linee orizzontali e verticali più vicine.

**Attiva/Disattiva allineamento alle guide di allineamento**

Le guide di allineamento consentono di allineare i controlli l'uno rispetto all'altro. Se è abilitato l' **allineamento alle guide di allineamento** , quando si trascina un controllo in relazione ad altri controlli, vengono visualizzati i limiti di allineamento quando i bordi e il testo di alcuni controlli sono allineati orizzontalmente o verticalmente. Il limite di allineamento viene mostrato come una linea tratteggiata rossa.

Nella visualizzazione **XAML**, la finestra contenente l'editor XAML è la finestra attiva e l'editor XAML è lo strumento di creazione primario. Il linguaggio Extensible Application Markup Language (XAML) fornisce un vocabolario dichiarativo basato su XML per la specifica dell'interfaccia utente di un'applicazione. La visualizzazione XAML include IntelliSense, la formattazione automatica, l'evidenziazione della sintassi e la navigazione tra tag. La figura seguente mostra la visualizzazione XAML:

![Visualizzazione XAML](../designers/media/xaml_editor.png)

**Barra della visualizzazione suddivisa**

La barra della visualizzazione suddivisa compare nella parte superiore della visualizzazione XAML quando l'editor XAML si trova nella finestra inferiore. La barra della doppia visualizzazione consente di controllare le dimensioni relative delle visualizzazioni **Progettazione** e **XAML**. È anche possibile scambiare le posizioni delle visualizzazioni, usando il pulsante **Scambia riquadri** , specificare se le visualizzazioni sono disposte orizzontalmente o verticalmente e comprimere una visualizzazione.

**Zoom di markup**

Lo zoom di markup permette di ridimensionare la visualizzazione **XAML**. È possibile ingrandire dal 20% al 400%.

## <a name="document-outline-window"></a>Finestra Struttura documento

La finestra Struttura documento nella finestra di progettazione XAML è simile alla finestra **Oggetti e sequenza temporale** in Blend per Visual Studio. **Struttura documento** consente di eseguire le attività seguenti:

- Visualizzare la struttura gerarchica di tutti gli elementi sulla tavola da disegno.

- Selezionare gli elementi in modo da poterli modificare, ossia spostarli nella gerarchia, modificarli sulla tavola da disegno, impostarne le proprietà nella finestra Proprietà e così via. Per altre informazioni, vedere [Utilizzo di elementi in XAML Designer](../designers/working-with-elements-in-xaml-designer.md)

- Creare e modificare modelli per gli elementi che sono controlli.

- Usare il menu di scelta rapida per gli elementi selezionati. Lo stesso menu è disponibile anche per gli elementi selezionati nella tavola da disegno.

Per visualizzare la finestra **Struttura documento**, scegliere **Visualizza** > **Altre finestre** > **Struttura documento** sulla barra dei menu.

![Finestra Struttura documento in Visual Studio](../designers/media/document-outline-window.png)

Le opzioni della finestra **Struttura documento** sono le seguenti:

**Struttura documento**

La visualizzazione principale nella finestra **Struttura documento** mostra la gerarchia di un documento in una struttura ad albero. È possibile usare la natura gerarchica della struttura documento per esaminare il documento con diversi livelli di dettaglio e per bloccare e nascondere gli elementi singolarmente o in gruppo.

**Mostra/Nascondi**

Visualizza o nasconde gli elementi della tavola da disegno che corrispondono agli elementi nella struttura documento. Usare i pulsanti **Mostra/Nascondi** (identificati, quando gli elementi sono visualizzati, dal simbolo di un occhio) oppure premere **CTRL**+**H** per nascondere gli elementi e **MAIUSC**+**CTRL**+**H** per visualizzarli.

**Blocca/Sblocca**

Blocca o sblocca gli elementi della tavola da disegno che corrispondono agli elementi nella struttura documento. Gli elementi bloccati non possono essere modificati. Usare i pulsanti **Blocca/Sblocca** (identificati, quando è applicato il blocco, dal simbolo di un lucchetto) oppure premere **CTRL**+**L** per bloccare gli elementi e **MAIUSC**+**CTRL**+**L** per sbloccarli.

**Reimposta l'ambito pageRoot**

L'opzione nella parte superiore della finestra **Struttura documento**, che mostra un simbolo di freccia rivolta verso l'alto, reimposta l'ambito precedente per la struttura documento. Questa operazione può essere eseguita solo nell'ambito di uno stile o di un modello.

## <a name="properties-window"></a>Finestra Proprietà

La finestra **Proprietà** consente di impostare valori di proprietà sui controlli. e ha l'aspetto seguente:

![Finestra Proprietà](../designers/media/xaml-designer-properties-window.png)

Nella parte superiore della finestra **Proprietà** sono disponibili varie opzioni. È possibile modificare il nome dell'elemento selezionato usando la casella **Nome** . Nell'angolo superiore sinistro è presente un'icona che rappresenta l'elemento selezionato. Per disporre le proprietà per categoria o in ordine alfabetico, fare clic su **Categoria**, **Nome**oppure **Origine** nell'elenco **Disponi per** . Per visualizzare l'elenco di eventi per un controllo, fare clic sul pulsante **Eventi** , al quale è associato il simbolo di un fulmine.

Per cercare una proprietà, iniziare a digitare il nome corrispondente nella casella di ricerca. La finestra **Proprietà** mostra le proprietà corrispondenti alla ricerca durante la digitazione. In alcuni casi è possibile impostare proprietà avanzate selezionando un pulsante Freccia GIÙ.

Per altre informazioni sull'uso delle proprietà e sulla gestione degli eventi, vedere [Intro to controls and patterns](/windows/uwp/design/controls-and-patterns/controls-and-events-intro) (Introduzione a controlli e modelli)

A destra di ogni valore di proprietà è presente un *marcatore della proprietà* , visualizzato sotto forma di simbolo di casella. L'aspetto del marcatore della proprietà indica se è presente un data binding o una risorsa applicata alla proprietà. Ad esempio, una casella bianca indica un valore predefinito, una casella nera indica che è stata applicata una risorsa locale e una casella arancione indica che è stato applicato un data binding. Quando si fa clic su questo marcatore, è possibile passare alla definizione di uno stile, aprire il generatore di data binding oppure aprire il selettore risorse.

## <a name="see-also"></a>Vedere anche

- [Uso di elementi in XAML Designer](../designers/working-with-elements-in-xaml-designer.md)
- [Procedura per creare e applicare una risorsa](../designers/how-to-create-and-apply-a-resource.md)
- [Procedura dettagliata: Eseguire il binding ai dati nella finestra di progettazione XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)