---
title: 'Introduzione a PTVS: Compilazione di un sito Web in Azure | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 61f8748a3874f32db9c235d03b6b7464bc5cecf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62551000"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Introduzione a PTVS: Compilazione di un sito Web in Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile iniziare a creare rapidamente un sito Web Python in Azure.  
  
 È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
 Iniziare con la finestra di dialogo Nuovo progetto e tra i progetti Python scegliere il progetto Web Bottle.  Questo modello [Bottle](http://bottlepy.org/docs/dev/index.html) è un sito di partenza basato sul [framework Bootstrap](http://getbootstrap.com/).  Quando si crea il progetto, Visual Studio richiede di installare le dipendenze (Bottle in questo caso) in un ambiente virtuale.  Poiché si sta eseguendo la distribuzione in un sito Web di Azure, è necessario aggiungere le dipendenze in un ambiente virtuale per distribuire i bit necessari per il funzionamento del sito.  È anche necessario basare l'ambiente su Python 2.7 o 3.4 a 32 bit.  Dopo aver creato il progetto, premere F5 per avviare l'esecuzione del sito in locale.  
  
 È facile provare il sito in Azure.  Se non si ha una sottoscrizione di Azure, è possibile usare [try.azurewebsites.net](https://trywebsites.azurewebsites.net/).  Questo sito offre un modo semplice per provare i siti Web di Azure per un'ora alla volta solo con un account di accesso social.  Non è necessaria una carta di credito.  Scegliere il modello di sito vuoto nell'elenco a discesa Change Language e scegliere Create.  In "Work with your web application" scegliere Download Publishing Profile e salvare il file da usare con Visual Studio.  È anche possibile eseguire la distribuzione usando GIT da qualsiasi sistema operativo.  
  
 Tornare a Visual Studio e al progetto creato.  Selezionare il nodo del progetto in Esplora soluzioni, scegliere il pulsante destro del puntatore, quindi scegliere Pubblica.  Se si dispone di una sottoscrizione di Azure, è possibile fare clic su Siti Web di Microsoft Azure nella finestra di dialogo per gestire i siti da qui.  Per questa procedura dettagliata scegliere Importa per importare il profilo di pubblicazione appena scaricato.  Poiché il profilo di pubblicazione contiene tutte le informazioni necessarie, è possibile scegliere Pubblica.  Entro pochi secondi verrà aperta una nuova finestra del browser e il sito verrà ospitato in tempo reale nel cloud di Azure.  
  
 I siti Web semplici sono intuitivi; per informazioni su applicazioni Web più complesse in Azure, vedere il [video di approfondimento](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) e gli altri video di questo canale (tramite il collegamento in alto a destra della pagina del video di introduzione o approfondimento oppure il collegamento riportato di seguito).  
  
 È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
## <a name="see-also"></a>Vedere anche  
 [Documentazione wiki](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [Video introduttivi e dettagliati su PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
