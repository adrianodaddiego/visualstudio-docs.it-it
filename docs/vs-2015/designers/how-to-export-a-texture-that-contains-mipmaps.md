---
title: 'Procedura: Esportare una trama che contiene mipmap | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f525f4b31a3535f6ea7b89d0443402240365cc7d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088652"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Procedura: Esportare una trama che contiene mipmap
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La pipeline di contenuti immagine può generare mipmap da un'immagine di origine come parte della fase di compilazione del progetto. Se non è necessario specificare manualmente il contenuto dell'immagine di ogni livello MIP, operazione che è possibile eseguire per ottenere alcuni effetti, la creazione di mipmap in fase di compilazione garantisce che il contenuto mipmap sia sempre sincronizzato e consente di eliminare i costi di prestazione per generare mipmap in fase di esecuzione.  
  
 Questo documento illustra le attività seguenti:  
  
- Configurazione dell'immagine di origine che deve essere elaborata dalla pipeline di contenuti immagine.  
  
- Configurazione di pipeline di contenuti immagine per generare mipmap.  
  
## <a name="exporting-mipmaps"></a>Esportazione di mipmap  
 La creazione di mipmap offre un livello di dettaglio automatico sullo spazio della schermata per aree con trame in giochi 3D o in app. Migliora le prestazioni di rendering di un gioco o di un'app pre-elaborando versioni a campionamento ridotto di una trama in modo che l'intera trama non debba essere elaborata ogni volta che viene campionata.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>Per esportare una trama che contiene mipmap  
  
1. Iniziare con una trama di base. Caricare un file d'immagine esistente oppure crearne uno nuovo, come illustrato in [Procedura: Creare una trama di base](../designers/how-to-create-a-basic-texture.md). Per supportare le mipmap, specificare una trama la cui larghezza e altezza corrispondano a un valore esponenziale con base due, ad esempio, 64 x 64, 256 x 256 o 512 x 512.  
  
2. Configurare il file di trama appena creato in modo che venga elaborato dalla pipeline di contenuti immagine. In **Esplora soluzioni** aprire il menu di scelta rapida per il file di trama appena creato e quindi scegliere **Proprietà**. Nella pagina **Proprietà di configurazione**, **Generale**, impostare la proprietà **Tipo di elemento** su **Image Content Pipeline** (Pipeline di contenuti immagine). Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e che l'opzione **Exclude From Build** (Escludi da compilazione) sia impostata su **No**, quindi scegliere il pulsante **Applica**. Viene visualizzata la pagina delle proprietà di configurazione **Image Content Pipeline** (Pipeline di contenuti immagine).  
  
3. Configurare la pipeline di contenuti immagine per generare mipmap. Nella pagina **Proprietà di configurazione**, **Image Content Pipeline** (Pipeline di contenuti immagine), **Generale**, impostare la proprietà **Genera MIP** su **Sì (/generatemips)**.  
  
4. Fare clic sul pulsante **OK** .  
  
   Quando si compila il progetto, la pipeline di contenuti immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato, includendo i livelli MIP. Il risultato viene copiato nella directory di output del progetto.
