---
title: Libreria di controlli (codice gestito) Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031f894eb2e117a213f4f9fbbf08ac57a1512d61
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688169"
---
# <a name="web-control-library-managed-code"></a>Libreria di controlli Web (Codice gestito)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il modello di progetto Libreria di controlli Web consente di creare una DLL. Poiché la libreria di classi è una DLL, non è possibile eseguirla direttamente. È necessario creare una pagina di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in cui sia incorporato il controllo. Per altre informazioni, vedere [modello libreria di controlli Web](https://msdn.microsoft.com/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Per eseguire il debug di una libreria di controlli Web (procedura 1)  
  
1. Aprire un progetto Libreria di controlli Web esistente o crearne uno nuovo.  
  
2. Creare una pagina di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in cui sia incorporato il controllo.  
  
3. Nel sito Web che ospita il test harness di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] creare una sottodirectory denominata `/Code`.  
  
4. Copiare il codice sorgente del controllo nella sottodirectory `/Code`.  
  
5. Aprire il codice sorgente nella sottodirectory `/Code` e impostare i punti di interruzione.  
  
6. Aprire una finestra del browser con un URL che punta al test harness. Quando verrà raggiunto un punto di interruzione nel controllo sarà possibile iniziare il debug.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Eseguire il debug di una libreria di controlli Web (il metodo 2)  
  
1. Creare il progetto dell'applicazione host e il progetto del controllo Web nella stessa soluzione.  
  
2. Nelle **Esplora soluzioni**, fare doppio clic su applicazione host e scegliere **Aggiungi riferimento**.  
  
3. Aggiungere un riferimento al progetto del controllo Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni Web ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)
