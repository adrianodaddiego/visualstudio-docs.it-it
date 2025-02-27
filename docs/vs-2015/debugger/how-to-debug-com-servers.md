---
title: 'Procedura: Eseguire il debug di server COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- COM, debugging
- debugging [C++], COM servers
- single document interface (SDI), debugging
- COM servers, debugging
- debugging [C++], ADI applications
- container information
ms.assetid: 9f013c2b-0306-4b34-ba7f-d4445a874da1
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3552ff1ffb5d6b3e3789aebd3a8903bf82a66b16
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088314"
---
# <a name="how-to-debug-com-servers"></a>Procedura: Eseguire il debug di server COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debug delle applicazioni server COM pone alcuni problemi che non sono sempre di facile soluzione.  
  
 Quando le informazioni di debug relative all'applicazione contenitore non vengono utilizzate o non sono disponibili, l'avvio del debug di un'applicazione server si suddivide in tre passaggi.  
  
### <a name="to-debug-a-server-application-without-container-information"></a>Per eseguire il debug di un'applicazione server senza informazioni sul contenitore  
  
1. Avviare il debug del server come applicazione normale.  
  
2. Impostare i punti di interruzione nel modo desiderato.  
  
3. Avviare l'applicazione contenitore.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Procedura: Eseguire il debug di client e server COM usando il debug RPC](../debugger/how-to-debug-com-clients-and-servers-using-rpc-debugging.md)   
 [Debug dei server e dei contenitori COM](../debugger/com-server-and-container-debugging.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)
