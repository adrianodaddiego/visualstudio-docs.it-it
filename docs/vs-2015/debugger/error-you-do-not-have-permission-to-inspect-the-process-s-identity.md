---
title: 'Errore: Non hai le autorizzazioni per controllare il processo di&#39;identità s | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d66eacb1b7f5205ea430d7154f67d05bdd047a74
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080748"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Errore: Non hai le autorizzazioni per controllare il processo di&#39;identità s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Non si dispone dell'autorizzazione necessaria per controllare l'identità del processo. Probabilmente l'errore è causato dalla configurazione del sistema.  
  
 Il debugger non è stato in grado di controllare l'identità del processo, un'informazione necessaria per l'esecuzione del debug. Probabilmente Servizi terminal è disabilitato. Per impostazione predefinita, questo servizio è attivato. Per riattivarlo, eseguire la procedura seguente.  
  
### <a name="to-enable-terminal-services"></a>Per attivare Servizi terminal  
  
1. Fare clic su **Start**, quindi scegliere **Pannello di controllo**.  
  
2. Nel Pannello di controllo scegliere **Passa alla visualizzazione classica**, se necessario, quindi fare doppio clic su **Strumenti di amministrazione**.  
  
3. Nella finestra **Strumenti di amministrazione** fare doppio clic su **Gestione computer**.  
  
4. Nella finestra di Gestione computer espandere il nodo **Servizi e applicazioni**.  
  
5. In **Servizi e applicazioni** fare clic su **Servizi**.  
  
     Nel riquadro di destra verrà visualizzato un elenco di servizi.  
  
6. Nell'elenco **Servizi** fare clic con il pulsante destro del mouse su **Servizi terminal** e quindi scegliere **Proprietà**.  
  
7. Nel **proprietà servizi Terminal** finestra, passa al **generali** scheda e impostare **tipo di avvio** al **manuale**.  
  
8. Fare clic su **OK**.  
  
9. Riavviare il computer.  
  
     Con questa procedura non si attiva automaticamente Desktop remoto. Se si desidera attivare Desktop remoto nel computer in uso, eseguire la procedura aggiuntiva seguente.  
  
### <a name="to-enable-remote-desktop"></a>Per attivare Desktop remoto  
  
1. Fare clic su **Start** e quindi fare clic con il pulsante destro del mouse su **Risorse del computer**.  
  
2. Scegliere **Proprietà**.  
  
     Verrà visualizzata la finestra **Proprietà del sistema**.  
  
3. Fare clic su **Connessione remota**.  
  
4. In **Desktop remoto** selezionare **Consenti agli utenti di connettersi in remoto al computer**.  
  
5. Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
