---
title: Come è possibile eseguire il debug di funzioni API Windows? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c5fd73eb64c79ac9476c0036b9f2d709294d178
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704591"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Come è possibile eseguire il debug di funzioni API Windows?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per eseguire il debug di una funzione API Windows con NT Symbols caricato, effettuare le operazioni seguenti.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Per impostare un punto di interruzione su una funzione Windows API con NT Symbols caricato  
  
- Immettere il nome della funzione e il nome della DLL in cui risiede la funzione. Nel codice a 32 bit, utilizzare la forma decorata del nome della funzione. Ad esempio, per impostare un punto di interruzione su **MessageBeep**, è necessario immettere quanto segue.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Per ottenere il nome decorato, vedere [visualizzazione di nomi decorati](https://msdn.microsoft.com/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
