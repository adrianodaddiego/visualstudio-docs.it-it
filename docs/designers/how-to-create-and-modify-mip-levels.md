---
title: 'Procedura: Creare e modificare livelli MIP'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50543a1f0191847beb4f849d56517cd0f12a1f7c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408608"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Procedura: Creare e modificare livelli MIP
Questo documento illustra come usare **Editor di immagini** per generare e modificare i *livelli MIP* per il livello di dettaglio dell'area della trama.

## <a name="generating-mip-levels"></a>Generazione dei livelli MIP
 *Mipmap* è una tecnica usata per aumentare la velocità di rendering e ridurre gli artefatti di aliasing sugli oggetti con trama tramite il precalcolo e l'archiviazione di più copie di una trama in dimensioni diverse. Ogni copia, nota come livello MIP, è metà della larghezza e dell'altezza della copia precedente. Quando viene eseguito il rendering di una trama sulla superficie di un oggetto, viene automaticamente scelto il livello MIP che più corrisponde all'area della superficie sullo schermo. L'hardware grafico, quindi, non deve filtrare le trame sovradimensionate per mantenere una qualità visiva uniforme. Anche se per i livelli MIP è necessario circa il 33% di memoria in più rispetto alla sola trama originale, questa condizione viene ampiamente ripagata dai vantaggi in termini di prestazioni e di qualità di immagine.

#### <a name="to-generate-mip-levels"></a>Per generare i livelli MIP

1. Iniziare con una trama di base, come descritto in [Procedura: Creare una trama di base](../designers/how-to-create-a-basic-texture.md). Per risultati ottimali, specificare una trama con larghezza e altezza equivalenti a una potenza di due nella dimensione, ad esempio 256, 512, 1024 e così via.

2. Generare i livelli MIP. Sulla barra degli strumenti della **modalità dell'editor di immagini** scegliere **Avanzate** > **Strumenti** > **Genera MIP**.

     I pulsanti per **la visualizzazione del livello MIP precedente** o **successivo** sono ora visualizzati sulla barra degli strumenti della **modalità dell'editor di immagini** . Se è visualizzata la finestra **Proprietà**, si può anche notare che nelle proprietà dell'immagine sono ora incluse le proprietà di sola lettura **Livello MIP** e **Conteggio livelli MIP**.

## <a name="modifying-mip-levels"></a>Modifica dei livelli MIP
 Per ottenere effetti speciali o aumentare la qualità dell'immagine in specifici livelli di dettaglio, è possibile modificare singolarmente ogni livello MIP. È ad esempio possibile assegnare a un oggetto con trama un aspetto diverso a una certa distanza (una distanza maggiore corrisponde a livelli MIP più piccoli) oppure è possibile assicurarsi che le trame contenenti testo o simboli rimangano leggibili anche a livelli MIP più piccoli.

#### <a name="to-modify-an-individual-mip-level"></a>Per modificare un singolo livello MIP

1. Selezionare il livello MIP che si vuole modificare. Sulla barra degli strumenti della **modalità dell'editor di immagini** usare i pulsanti per **la visualizzazione del livello MIP precedente** o **successivo** per spostarsi da un livello MIP all'altro.

2. Dopo aver selezionato il livello MIP da modificare, è possibile usare gli strumenti di disegno per modificarlo lasciando invariato il contenuto degli altri livelli MIP. Gli strumenti di disegno sono disponibili sulla barra degli strumenti **Editor di immagini**. Dopo aver selezionato uno strumento, è possibile modificarne le proprietà nella finestra **Proprietà**. Per informazioni sugli strumenti di disegno e le relative proprietà, vedere [Editor di immagini](../designers/image-editor.md).

> [!NOTE]
> Se non è necessario modificare il contenuto di singoli livelli MIP (ad esempio, per ottenere effetti specifici), è consigliabile generare mipmap dalla trama di origine in fase di compilazione. Questa operazione garantisce infatti che i livelli MIP rimangano sincronizzati con la trama di origine, poiché le modifiche apportate a un livello MIP non vengono propagate automaticamente ad altri livelli. Per altre informazioni su come generare mipmap in fase di compilazione, vedere [Procedura: Esportare una trama che contiene mipmap](../designers/how-to-export-a-texture-that-contains-mipmaps.md).

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare una trama di base](../designers/how-to-create-a-basic-texture.md)