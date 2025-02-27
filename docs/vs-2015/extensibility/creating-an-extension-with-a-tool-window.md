---
title: Creazione di un'estensione con una finestra degli strumenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431849"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Creazione di un'estensione con una finestra degli strumenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura descrive come usare il modello di progetto VSIX e il **finestra degli strumenti personalizzata** modello di elemento per creare un'estensione con una finestra degli strumenti.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Creazione di una finestra degli strumenti  
  
1. Creare un progetto VSIX denominato **FirstWindow**. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2. Quando si apre il progetto, aggiungere un modello di elemento di finestra degli strumenti denominato **FirstWindow**. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Aggiungi / nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual c# / Extensibility** e selezionare **finestra degli strumenti personalizzata**. Nel **Name** campo nella parte inferiore della finestra, modificare il nome file della finestra degli strumenti per **FirstWindow.cs**.  
  
3. Compilare il progetto e avviare il debug.  
  
     Viene visualizzata l'istanza sperimentale di Visual Studio. Per altre informazioni sull'istanza sperimentale, vedere [il processo dell'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4. Nell'istanza sperimentale, passare a **Vista / Windows altri**.  
  
     Una voce di menu per dovrebbe **FirstWindow**. Fare clic.  
  
     Si dovrebbe essere una finestra degli strumenti con il titolo **FirstWindow** che indica che un pulsante e **Click Me!.**
