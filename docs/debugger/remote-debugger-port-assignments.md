---
title: Le assegnazioni di porta del Debugger remoto | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 672d54b29e6de9302e88b1b95b4117783b8a0113
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903044"
---
# <a name="remote-debugger-port-assignments"></a>Assegnazioni delle porte del debugger remoto
Visual Studio Remote Debugger può essere eseguito come applicazione o come servizio in background. Quando viene eseguito come applicazione, usa una porta assegnata per impostazione predefinita, come indicato di seguito:
::: moniker range=">=vs-2019"
- Visual Studio 2019: 4024
::: moniker-end
- Visual Studio 2017: 4022

- Visual Studio 2015: 4020

- Visual Studio 2013: 4018

- Visual Studio 2012: 4016

  In altre parole, il numero della porta assegnata al debugger remoto viene incrementato di 2 per ogni versione. È possibile impostare un numero di porta diverso. In una sezione successiva verrà illustrato come impostare i numeri di porta.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Porta del debugger remoto nei sistemi operativi a 32 bit

::: moniker range=">=vs-2019"
 TCP 4024 (in Visual Studio 2019) è la porta principale ed è necessaria per tutti gli scenari. Può essere configurata dalla riga di comando o nella finestra del debugger remoto.
::: moniker-end
::: moniker range="vs-2017"
 TCP 4022 (in Visual Studio 2017) è la porta principale ed è necessaria per tutti gli scenari. Può essere configurata dalla riga di comando o nella finestra del debugger remoto.
::: moniker-end

 Nella finestra del debugger remoto fare clic su **Strumenti > opzioni** e impostare il numero di porta TCP/IP.

 Nella riga di comando avviare il debugger remoto con l'opzione **/port**: **msvsmon /port \<numero porta>**.

 Tutte le opzioni della riga di comando del debugger remoto sono reperibili nella Guida al debug remoto (premere **F1** o fare clic su **Guida > Utilizzo** nella finestra del debugger remoto).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Porta del debugger remoto nei sistemi operativi a 64 bit
::: moniker range=">=vs-2019"
 Quando viene avviata la versione a 64 bit del debugger remoto, Usa principale porta (4024) per impostazione predefinita.  Se si esegue il debug di un processo a 32 bit, la versione a 64 bit del debugger remoto avvia una versione a 32 bit del debugger remoto sulla porta 4025 (il numero di porta principale incrementato di 1). Se si esegue il debugger remoto a 32 bit, viene usata la porta 4024 e non la porta 4025.
::: moniker-end
::: moniker range="vs-2017"
 Quando viene avviata la versione a 64 bit del debugger remoto, principale Usa la porta (4022) per impostazione predefinita.  Se si esegue il debug di un processo a 32 bit, la versione a 64 bit del debugger remoto avvia una versione a 32 bit del debugger remoto sulla porta 4023 (il numero di porta principale incrementato di 1). Se si esegue il debugger remoto a 32 bit, viene usata la porta 4022 e non la porta 4023.
:::moniker-end

 Questa porta è configurabile dalla riga di comando: **Msvsmon /wow64port \<numero porta >**.

## <a name="the-discovery-port"></a>Porta di individuazione
 La porta UDP 3702 viene usata per individuare le istanze in esecuzione del debugger remoto sulla rete, ad esempio la finestra di dialogo **Trova** nella finestra di dialogo **Connetti a processo** . Viene usata solo per l'individuazione di un computer che esegue il debugger remoto, pertanto è facoltativa se si ha altro un modo per conoscere il nome del computer o l'indirizzo IP del computer di destinazione. Si tratta di una porta standard per l'individuazione, quindi non è possibile configurare il numero di porta.

 Se non si desidera abilitare l'individuazione, è possibile avviare msvsmon dalla riga di comando con l'individuazione disabilitata:  **Msvsmon /nodiscovery**.

## <a name="remote-debugger-ports-on-azure"></a>Porte del debugger remoto in Azure
 Il debugger remoto in Azure usa le porte indicate di seguito. Le porte del servizio cloud sono mappate alle porte nelle singole macchine virtuali. Tutte le porte sono TCP.

|Connessione|Porta sul servizio cloud|Porta sulla macchina virtuale|
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarderx86|31401|31399|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|

## <a name="see-also"></a>Vedere anche
- [Remote Debugging](../debugger/remote-debugging.md)