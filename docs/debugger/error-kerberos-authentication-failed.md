---
title: "Errore: Impossibile eseguire l'autenticazione Kerberos | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76a62a821a9b110be2ffd8e25cbdf6721f12bc08
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850739"
---
# <a name="error-kerberos-authentication-failed"></a>Errore: Autenticazione Kerberos non riuscita
Quando si tenta di eseguire il debug remoto, è possibile che venga visualizzato il messaggio di errore seguente:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 L'errore si verifica quando Visual Studio Remote Debugging Monitor è in esecuzione con l'account di sistema locale o l'account del servizio di rete. Utilizzando uno di questi account, il debugger remoto deve stabilire una connessione di autenticazione Kerberos allo scopo di inviare comunicazioni al computer host del debugger Visual Studio.

 L'autenticazione Kerberos non è disponibile nei seguenti casi:

- Il computer di destinazione o il computer host del debugger si trova in un gruppo di lavoro anziché in un dominio.

   \- oppure -

- Kerberos è stato disabilitato sul controller di dominio.

  Se l'autenticazione Kerberos non è disponibile, modificare l'account utilizzato per l'esecuzione di Visual Studio Remote Debugging Monitor. Per istruzioni, vedere [errore: Il servizio di Visual Studio Remote Debugger nel computer di destinazione non può connettersi al computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

  Se il messaggio di errore viene visualizzato nonostante entrambi i computer siano connessi allo stesso dominio, verificare che il nome del computer host del debugger venga risolto correttamente dal DNS del computer di destinazione. Attenersi alla procedura indicata di seguito.

### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Per verificare la corretta risoluzione del nome del computer host del debugger da parte del DNS del computer di destinazione

1. Nel computer di destinazione, aprire il menu **Start**, scegliere **Accessori**, quindi fare clic su **Prompt dei comandi**.

2. Nella finestra del **prompt dei comandi** digitare:

    ```cmd
    ping <debugger_host_computer_name>
    ```

3. Nella prima riga della risposta `ping` viene indicato il nome completo del computer e l'indirizzo IP restituito dal DNS per il computer specificato.

4. Nel computer host del debugger, aprire la finestra del **prompt dei comandi** ed eseguire `ipconfig`.

5. Confrontare i valori degli indirizzi IP.

## <a name="see-also"></a>Vedere anche
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
