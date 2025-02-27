---
title: Risoluzione dei problemi del Visualizzatore della Guida | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: troubleshooting
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77529ad9957694b1ea1853b3e8b1b1cc29c45e2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429730"
---
# <a name="troubleshooting-the-help-viewer"></a>Risoluzione dei problemi relativi al visualizzatore della Guida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento vengono illustrati i problemi che potrebbero verificarsi con il visualizzatore della Guida.  
  
## <a name="audio-doesnt-work"></a>L'audio non funziona.  
 Il visualizzatore della Guida non include un lettore audio. Se si scaricano contenuti che includono l'audio e non accade nulla quando si sceglie **Riproduci**, installare un lettore audio.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>La ricerca non funziona in Windows Server 2008, Windows Server 2008 con SP1 o Windows Server 2008 R2.  
 Le funzionalità di ricerca e filtro nel visualizzatore della Guida richiedono il servizio Windows Search. Per impostazione predefinita, questo servizio è disattivato in Windows Server 2008, Windows Server 2008 con Service Pack 1 (SP1) e Windows Server 2008 R2.  
  
#### <a name="to-activate-windows-search-service"></a>Per attivare il servizio Windows Search  
  
1. Avviare Server Manager.  
  
2. Nel riquadro di spostamento a sinistra scegliere **Ruoli**.  
  
3. Nel riquadro Riepilogo ruoli scegliere **Aggiungi ruolo**.  
  
4. Scegliere il ruolo Servizi file e il pulsante **Avanti**.  
  
5. Scegliere il servizio ruolo Windows Search.  
  
## <a name="additional-resources"></a>Risorse aggiuntive  
 È possibile ottenere altre informazioni e offrire commenti e suggerimenti sul visualizzatore della Guida mediante le risorse seguenti:  
  
- Per offrire commenti e suggerimenti, vedere [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) dal sito Microsoft o inviare un messaggio di posta elettronica a [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
- Per altre informazioni, vedere la [sistema di Guida e documentazione per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=232741) forum e [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743) blog.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida dell'amministratore di Help Viewer 2.1](http://go.microsoft.com/fwlink/?LinkId=243985)
