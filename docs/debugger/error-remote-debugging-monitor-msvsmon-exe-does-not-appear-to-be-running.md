---
title: 'Errore: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) non sembra essere in esecuzione sul computer remoto.'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.server_machine_no_default
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
ms.openlocfilehash: 5dcd45cb64656b926b9c59efd7b6af14d2ec4c53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850657"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Errore: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) non sembra essere in esecuzione sul computer remoto.
Questo messaggio di errore indica che Visual Studio non ha trovato l'istanza corretta di Visual Studio Remote Debugging Monitor nel computer remoto. Per il funzionamento del debug remoto, è necessario che Visual Studio Remote Debugging Monitor sia installato. Per informazioni sul download e la configurazione del debugger remoto, vedere [debug remoto](../debugger/remote-debugging.md).

> [!IMPORTANT]
> Se si ritiene di aver ricevuto questo messaggio a causa di un bug del prodotto, please [segnalare il problema a Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md). Per ottenere ulteriore assistenza, vedere [Talk to Us](../ide/talk-to-us.md) per le modalità di contatto di Microsoft.

## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Il messaggio è stato visualizzato durante il debug in Visual Studio 2010 o versioni precedenti
 Se la versione di Visual Studio in uso è Visual Studio 2010 o versioni precedenti, l'errore potrebbe essere visualizzato perché non è abilitata la condivisione di file e stampanti. Per altre informazioni su questo problema, consultare la versione di Visual Studio 2010 di questa documentazione: [Errore: Il Microsoft Visual Studio Remote Debugging Monitor (MSVSMON. Con estensione EXE) non sembra essere in esecuzione nel computer remoto. -Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100))

## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Il messaggio è stato visualizzato durante un debug locale
 Se si riceve questo messaggio durante un debug locale, il problema potrebbe essere causato dal software antivirus o da un firewall di terze parti. Visual Studio è un'applicazione a 32 bit, quindi usa la versione a 64 bit del debugger remoto per eseguire il debug delle applicazioni a 64 bit. I due processi comunicano usando la rete locale nel computer locale. Il traffico resta all'interno del computer, ma è possibile che un software per la sicurezza di terze parti blocchi la comunicazione.

 Le sezioni seguenti elencano altri motivi per cui potrebbe essere visualizzato questo messaggio e le soluzioni disponibili.

## <a name="the-remote-machine-is-not-reachable"></a>Il computer remoto non è raggiungibile
 Provare a eseguire il [ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) del computer remoto. Se non risponde al ping, neanche gli strumenti remoti potranno connettersi. Provare a riavviare il computer remoto, altrimenti assicurarsi che sia configurato correttamente sulla rete.

## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La versione del debugger remoto non corrisponde alla versione di Visual Studio
 La versione di Visual Studio in esecuzione in locale deve corrispondere alla versione di Remote Debugging Monitor in esecuzione nel computer remoto. Per risolvere questo problema, scaricare e installare la versione corrispondente di Remote Debugging Monitor. Andare nell' [Area download](http://www.microsoft.com/en-us/download) per trovare la versione corretta per il debugger remoto.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Il computer locale e quello remoto hanno modalità di autenticazione diverse
 Il computer locale e quello remoto devono usare la stessa modalità di autenticazione. Per risolvere questo problema, assicurarsi che entrambi i computer usino la stessa modalità di autenticazione. Per altre informazioni sulle modalità di autenticazione, vedere [Panoramica di Autenticazione di Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Il debugger remoto è in esecuzione con un altro account utente
 Per risolvere il problema, usare uno dei metodi seguenti:

- Arrestare il debugger remoto e riavviarlo con l'account in uso nel computer locale.

- Avviare il debugger remoto dalla riga di comando con il parametro **/allow \<nomeutente>**: `msvsmon /allow <username@computer>`

- È possibile aggiungere l'utente alle autorizzazioni del debugger remoto, nella finestra del debugger remoto, **Strumenti > Autorizzazioni**.

- Se i metodi descritti in precedenza non sono applicabili, è possibile consentire a tutti gli utenti di eseguire il debug remoto. Nella finestra del debugger remoto passare alla finestra di dialogo **Strumenti > Opzioni**. Se si seleziona   **Nessuna autenticazione**, è possibile selezionare **Consenti debug da parte di qualsiasi utente**. Tuttavia, questa opzione va usata solo se non sono disponibili le altre o se ci si trova in una rete privata.

## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Il firewall nel computer remoto non consente le connessioni in ingresso nel debugger remoto
 Il firewall nel computer Visual Studio e il firewall nel computer remoto devono essere configurati per consentire la comunicazione tra Visual Studio e il debugger remoto. Per informazioni sulle porte usate dal debugger remoto, vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Per informazioni sulla configurazione del firewall di Windows, vedere [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="anti-virus-software-is-blocking-the-connections"></a>Il software antivirus sta bloccando le connessioni
 Il software antivirus di Windows consente le connessioni del debugger remoto, mentre altri software antivirus di terze parti potrebbero bloccarle. Controllare la documentazione del software antivirus per scoprire come consentire queste connessioni.

## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>I criteri di sicurezza di rete bloccano la comunicazione tra il computer remoto e Visual Studio
 Esaminare la sicurezza della rete per assicurarsi che non blocchi la comunicazione. Per altre informazioni sui criteri di sicurezza di rete di Windows, vedere [impostazioni di criteri di sicurezza](/windows/device-security/security-policy-settings/security-policy-settings).

## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>La rete è troppo occupata per supportare il debug remoto
 Provare a eseguire il debug remoto in un altro momento oppure pianificare il lavoro sulla rete per un altro orario.

## <a name="more-help"></a>Altre informazioni
 Per ottenere assistenza sul debugger più remoti, inclusi opzioni della riga di comando, fare clic su **aiutare > utilizzo** nella finestra del debugger remoto. Se non è aperto, è possibile vedere la pagina web copiando la riga seguente a un **Esplora File** finestra. (È necessario sostituire \<directory di installazione di Visual Studio > con il percorso di installazione di Visual Studio.)

 res: / /*\<directory di installazione di Visual Studio >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm

## <a name="see-also"></a>Vedere anche
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
