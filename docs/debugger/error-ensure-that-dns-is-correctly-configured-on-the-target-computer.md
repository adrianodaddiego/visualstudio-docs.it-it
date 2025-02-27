---
title: 'Errore: Assicurarsi di che DNS sia configurato correttamente nel Computer di destinazione | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_dns_failed
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
ms.openlocfilehash: c538a2b4ff4a50cd89bd9571a8746ccb58aaed04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850886"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Errore: Accertarsi che DNS sia correttamente configurato nel computer di destinazione
Quando si tenta di eseguire il debug remoto, potrebbe essere visualizzato il seguente messaggio di errore:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.
```

 Questo errore si verifica quando il computer di destinazione non è in grado di risolvere il nome del computer host del debugger Visual Studio. Verificare le impostazioni DNS del computer di destinazione.

- Per informazioni sulla visualizzazione della configurazione del DNS in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 oppure Windows Server 2008 R2, fare clic sul pulsante **Start**, scegliere **Guida e supporto tecnico** e quindi cercare le **impostazioni di modifica TCP/IP**.

- Per ulteriori informazioni, visitare il [sito Web Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) e cercare le **impostazioni di modifica TCP/IP**.

  Se è possibile risolvere il problema DNS, è possibile provare a eseguire il debugger remoto con un account diverso. L'errore si verifica quando è in esecuzione il debugger remoto con l'account del sistema locale o l'account del servizio di rete. Se si esegue il debugger remoto con un altro account, è possibile usare l'autenticazione NTLM, che non richiede il DNS. . Per istruzioni, vedere [errore: Il servizio di Visual Studio Remote Debugger nel computer di destinazione non può connettersi al computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
