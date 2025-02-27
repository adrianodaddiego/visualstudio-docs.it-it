---
title: 'Errore: Il servizio di Visual Studio Remote Debugger nel computer di destinazione non può connettersi al computer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f598d765e45b1f97d6a3e95d1ad57c325ea38fe
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697351"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Errore: Il servizio Visual Studio Remote Debugger nel computer di destinazione non è in grado di riconnettersi a questo computer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il messaggio di errore viene visualizzato per segnalare che l'account utente utilizzato per l'esecuzione del servizio Debugger remoto di Visual Studio non è in grado di eseguire l'autenticazione per la connessione al computer dal quale viene eseguito il debug.  
  
 Nella tabella riportata di seguito sono indicati gli account in grado di accedere al computer:  
  
|||||  
|-|-|-|-|  
||Account LocalSystem|Account di dominio|Account locali con lo stesso nome utente e la stessa password in entrambi i computer|  
|Entrambi i computer nello stesso dominio|Yes|Yes|Yes|  
|Entrambi i computer in domini con trust bidirezionale|No|No|Yes|  
|Uno o entrambi i computer in un gruppo di lavoro|No|No|Yes|  
|Computer in domini diversi|No|No|Yes|  
  
 Inoltre:  
  
- L'account utilizzato per l'esecuzione del servizio Debugger remoto di Visual Studio deve essere un account amministrativo nel computer remoto in modo da poter eseguire il debug di qualsiasi processo.  
  
- È anche necessario assegnare a questo account il privilegio `Log on as a service` nel computer remoto che utilizza lo strumento di amministrazione **Criteri di sicurezza locali**.  
  
- Se si intende utilizzare un accesso al computer con account locale, è necessario eseguire il servizio Debugger remoto di Visual Studio con un account locale.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. Assicurarsi che il servizio Debugger remoto di Visual Studio sia configurato in modo corretto nel computer remoto. Per altre informazioni, vedere [Set Up the Remote Tools sul dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
2. Eseguire il servizio Debugger remoto utilizzando un account in grado di accedere al computer host del debugger, come indicato nella tabella precedente.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Per aggiungere un privilegio "Accesso come servizio"  
  
1. Nel menu **Start** scegliere **Pannello di controllo**.  
  
2. Se necessario, nel Pannello di controllo scegliere **Passa alla visualizzazione classica**.  
  
3. Fare doppio clic su **Strumenti di amministrazione**.  
  
4. Nella finestra Strumenti di amministrazione fare doppio clic su **Criteri di sicurezza locali**.  
  
5. Nella finestra **Impostazioni sicurezza locale** espandere la cartella **Criteri locali**.  
  
6. Scegliere **Assegnazione diritti utente**.  
  
7. Nella colonna **Criteri** fare doppio clic su **Accedi come servizio** per visualizzare le assegnazioni dei criteri di gruppo locali correnti nella finestra di dialogo **Accedi come servizio**.  
  
8. Per aggiungere nuovi utenti, fare clic sul pulsante **Aggiungi utente o gruppo**.  
  
9. Al termine, scegliere **OK**.  
  
### <a name="to-work-around-this-error"></a>Per risolvere il problema  
  
- Eseguire Remote Debugging Monitor come applicazione anziché come servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
