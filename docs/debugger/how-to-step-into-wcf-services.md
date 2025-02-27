---
title: 'Procedura: Istruzioni nei servizi WCF | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fe025ed3050f25ec53175c543adfaf7cb48c506
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906478"
---
# <a name="how-to-step-into-wcf-services"></a>Procedura: Eseguire istruzioni nei servizi WCF
In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], è possibile eseguire istruzioni in un servizio WCF. Se il servizio WCF si trova nella stessa soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] del client, è possibile raggiungere punti di interruzione nel servizio WCF.

 Per consentire il funzionamento, è necessario avere attivato il debug nel file app.config o web.config. Per informazioni su come abilitare il debug e per le limitazioni sull'esecuzione dei servizi WCF, vedere [limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Per eseguire istruzioni in un servizio WCF

1. Creare una soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contenente entrambi i progetti client WCF e servizio WCF.

2. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto Client WCF e scegliere **Imposta come progetto di avvio**.

3. Attivare il debug nel file app.config o web.config. Per altre informazioni, vedere [limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md).

4. Impostare un punto di interruzione nel percorso all'interno del progetto client in cui si desidera iniziare a eseguire le istruzioni. In genere, si troverà poco prima della chiamata del servizio WCF.

5. Eseguire il debug nel punto d'interruzione, quindi iniziare a eseguire le istruzioni. Il debugger eseguirà automaticamente le istruzioni nel servizio.

## <a name="see-also"></a>Vedere anche
- [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)
- [Limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md)
- [Procedura: Eseguire il debug di un servizio WCF self-hosted](../debugger/how-to-debug-a-self-hosted-wcf-service.md)