---
title: Elenco eventi grafici | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 710cc8cae2b1974529be1eded6c5148eedd1211e
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805320"
---
# <a name="graphics-event-list"></a>Elenco eventi grafici
Usare l'Elenco eventi di grafica in Analizzatore grafica di Visual Studio per esplorare gli eventi Direct3D registrati durante il rendering di un frame del gioco o dell'app.

 Questo è l'elenco di eventi:

 ![Un elenco di eventi con "Vertice" nel nome. ](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Uso dell'elenco di eventi
 Quando si seleziona un evento nell'elenco, l'attività si riflette nelle informazioni visualizzate dagli altri strumenti di analisi grafica. Usando l'elenco di eventi insieme a questi altri strumenti è possibile esaminare in dettaglio un problema di rendering per determinarne la causa. Per altre informazioni su come risolvere i problemi di rendering usando l'elenco di eventi insieme agli altri strumenti di analisi grafica, vedere [Esempi](graphics-diagnostics-examples.md).

 Usare le funzionalità dell'elenco di eventi in modo efficace è importante per operare su frame complessi che possono contenere migliaia di eventi. Per usare l'elenco di eventi in modo efficace, scegliere la visualizzazione più adatta alla proprie esigenze, seguire i collegamenti per altre informazioni sugli oggetti Direct3D associati a un evento e usare le frecce per spostarsi rapidamente tra le chiamate di disegno.

### <a name="color-coded-events-in-direct3d-12"></a>Eventi contraddistinti dal colore in Direct3D 12
 Direct3D 12 espone più code che corrispondono a funzionalità hardware diverse. Per agevolare l'identificazione della coda associata a un particolare evento di grafica in Direct3D 12, quando si lavora su una cattura di un'app Direct3D 12, all'interno dell'elenco gli eventi sono contraddistinti da colori diversi in base alla coda.

|Coda Direct3D 12|Colore|
|-----------------------|-----------|
|Coda di rendering|Verde|
|Coda di calcolo|Giallo|
|Coda di copia|Arancione|

 Direct3D 11 non espone più code, dunque gli eventi non sono contraddistinti dal colore nell'elenco di eventi quando si lavora con una cattura di un'app Direct3D 11.

### <a name="event-list-views"></a>Visualizzazioni dell'elenco di eventi
 L'elenco di eventi supporta due diverse visualizzazioni che organizzano gli eventi grafici in modo diverso, per supportare il flusso di lavoro e le preferenze dell'utente. La prima è la *visualizzazione di lavoro GPU* che organizza gli eventi e lo stato associato in gerarchie. La seconda è la *visualizzazione cronologia* , che organizza gli eventi in ordine cronologico, in un elenco semplice.

 Il **operazioni della GPU** consente di visualizzare gli eventi acquisiti e il proprio stato in una gerarchia di visualizzazione. Il primo livello della gerarchia contiene eventi come chiamate di disegno, cancellazioni, presentazioni ed eventi associati alle visualizzazioni. Nell'elenco di eventi è possibile espandere le chiamate di disegno per visualizzare lo stato del dispositivo al momento della chiamata di disegno ed espandere ulteriormente ogni tipo di stato per visualizzare gli eventi che hanno impostato i valori. A questo livello è anche possibile vedere se un particolare stato è stato impostato in un frame precedente oppure se è stato impostato più volte dall'ultima chiamata di disegno.

 Il **della sequenza temporale** Vista sono riportati gli eventi acquisiti in ordine cronologico. Questo tipo di organizzazione dell'elenco di eventi è uguale a quello usato nelle versioni precedenti di Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>Per modificare la modalità di visualizzazione dell'elenco di eventi

- Nel **elenco eventi di grafica** finestra, sopra l'elenco degli eventi, individuare il **vista** elenco a discesa e scegliere il **sequenza temporale** visualizzazione o la **operazioni della GPU** visualizzazione.

### <a name="filtering-events"></a>Filtro degli eventi
 La casella Cerca, situata nell'angolo superiore destro della finestra **Elenco eventi grafici** consente di filtrare l'elenco di eventi in modo da includere solo gli eventi i cui nomi contengono determinate parole chiave. È possibile specificare singole parole chiave, ad esempio `Vertex`, come mostrato nella figura precedente, oppure un elenco di parole chiave separate da punti e virgola, come `Draw;Primitive`, per visualizzare solo gli eventi il cui nome contiene `Draw` o `Primitive` . Le ricerche sono sensibili agli spazi. Ad esempio, `VSSet` e `VS Set` sono differenti. Fare quindi attenzione a formulare le ricerche nel modo corretto.

### <a name="moving-between-draw-calls"></a>Spostamento tra chiamate di disegno
 Poiché esaminare le chiamate `Draw` è particolarmente importante, è possibile usare i pulsanti **Passa a chiamata di disegno successiva** e **Passa a chiamate di disegno precedente** situati nell'angolo superiore sinistro della finestra **Elenco eventi grafici** , per trovare rapidamente gli eventi e spostarsi da uno all'altro.

### <a name="links-to-graphics-objects"></a>Collegamenti a oggetti grafici
 Per comprendere gli eventi di grafica potrebbero essere necessarie informazioni aggiuntive sullo stato corrente di Direct3D o sugli oggetti Direct3D a cui viene fatto riferimento dall'evento. In molti eventi sono presenti i collegamenti alle informazioni, che è possibile seguire per accedere a ulteriori dettagli.

## <a name="kinds-of-events-and-event-markers"></a>Tipi di eventi e marcatori di eventi
 Gli eventi visualizzati nell'elenco di eventi sono organizzati in quattro categorie: eventi generali, eventi di disegno, gruppi di eventi definiti dall'utente e marcatori di eventi definiti dall'utente. Tutti gli eventi, ad eccezione degli eventi generali, sono visualizzati insieme a un'icona che indica la categoria di appartenenza.

|Icona|Descrizione evento|
|----------|-----------------------|
|(nessuna icona)|Evento generale<br /> Qualsiasi evento diverso da un evento definito dall'utente, un gruppo di eventi definito dall'utente o un evento di disegno.|
|![L'icona dell'evento di disegno](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Evento di disegno<br /> Contrassegna un evento di disegno che si è verificato durante il frame acquisito.|
|![L'utente&#45;icona marcatore di eventi definiti](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Gruppo di eventi definito dall'utente<br /> Raggruppa gli eventi correlati, in base a quanto definito dall'app.|
|![L'utente&#45;icona marcatore di eventi definiti](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Marcatore di eventi definito dall'utente<br /> Contrassegna una posizione specifica, in base a quanto definito dall'app.|

## <a name="marking-user-defined-events-in-your-app"></a>Contrassegno di eventi definiti dall'utente nell'app
 Gli eventi definiti dall'utente sono specifici dell'app. Possono essere usati per correlare gli eventi significativi che si verificano nell'app a quelli presenti nell'Elenco eventi grafici. Ad esempio, è possibile creare gruppi di eventi definiti dall'utente per organizzare in gruppi o gerarchie gli eventi correlati al rendering dell'interfaccia, in modo da poter sfogliare più facilmente l'elenco di eventi, oppure creare marcatori quando vengono disegnati determinati tipi di oggetti, in modo da trovare facilmente gli eventi grafici correlati nell'elenco di eventi.

 Per creare gruppi e marcatori nell'app si usano le stesse API fornite da Direct3D per altri strumenti di debug Direct3D. A volte queste API cambiano tra una versione e l'altra di Direct3D, ma le funzionalità di base sono le stesse.

### <a name="user-defined-events-in-direct3d-12"></a>Eventi definiti dall'utente in Direct3D 12
 Per creare gruppi e marcatori in Direct3D 12, usare le API descritte in questa sezione. La tabella di seguito contiene un riepilogo delle API che è possibile usare in base alla posizione in cui si contrassegnano gli eventi, ovvero in una coda di comandi o in un elenco di comandi.

|Descrizione API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Controllare la disponibilità di un evento definito dall'utente|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|Iniziare un gruppo di eventi|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Terminare un gruppo di eventi|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Creare un marcatore di eventi|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Eventi definiti dall'utente in Direct3D 11 e versioni precedenti
 Per creare gruppi e marcatori in Direct3D 11 o versione precedente, usare le API descritte in questa sezione. La tabella di seguito contiene un riepilogo delle API che è possibile usare per versioni diverse di Direct3D 11 e versioni precedenti di Direct3D.

|Descrizione API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](http://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11.1)|Famiglia D3DPerf_ API (Direct3D 11.0 e precedenti)|
|---------------------| - | - | - |
|Iniziare un gruppo di eventi|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Terminare un gruppo di eventi|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Creare un marcatore di eventi|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 È possibile usare qualsiasi API supportata dalla versione di Direct3D in uso. Ad esempio, se la destinazione è l'API Direct3D 11.1, per creare un marcatore di eventi si può usare `SetMarker` o `D3DPerf_SetMarker` , ma non `SetMarkerInt` perché quest'ultima è disponibile solo in Direct3D 11.2. È anche possibile combinare nella stessa app le API che supportano versioni diverse di Direct3D.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Cronologia risorse
Visual Studio 2017 e versioni successiva contengono il **cronologia risorse** finestra.  Selezionando l'icona di espressioni di controllo ![icona watch](media/gfx_watch.png) accanto a una voce nel **elenco eventi di** finestra verrà visualizzata la **cronologia risorse** finestra illustrata di seguito:

![Cronologia risorse](media/gfx_diag_resource_history.png)

In questa finestra consente di visualizzare la cronologia dell'elemento selezionato nell'elenco eventi.  L'elenco a discesa nella parte superiore è utilizzabile per selezionare altri elementi per visualizzare la cronologia di.  Nella metà superiore della finestra contiene il **eventi di configurazione fotogrammi**.  Questi sono gli eventi che rientrano i *Create* categoria di tipi e sono chiamate che in genere inizializzano e creare la risorsa.  Nella parte inferiore della metà della finestra contiene il **eventi della cornice** sezione.  Si tratta la normale operazione di lettura e scrittura di eventi che si verificano durante l'utilizzo della risorsa.

| Colonna | Descrizione |
|-----------| - |
| **Type** | Mostra il tipo di voce, in genere *Create*, *lettura* e *scrivere*. |
| **Visualizza** | Mostra un'anteprima della risorsa in quel momento nel tempo.  Fare doppio clic su Anteprima per aprire una visualizzazione dei dettagli della risorsa in quel momento. |
| **Event** | Illustra la chiamata al metodo che si sono verificati che ha generato l'evento.  Qualsiasi cronologia aggiuntiva per singoli elementi può essere visualizzata selezionando l'icona di guardare ![icona watch](media/gfx_watch.png) sulla riga appropriata.  Inoltre, qualsiasi elemento che viene disegnato il testo di colore blu, ad esempio `m_commandList` nella schermata precedente, è possibile selezionare per altri dettagli. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Oggetti mancanti a causa dello stato del dispositivo](walkthrough-missing-objects-due-to-device-state.md)