---
title: Installare agenti di test e test controller
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6597c47fd272beec2c82f7d4c2644291b168b5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965415"
---
# <a name="install-test-agents-and-test-controllers"></a>Installare agenti di test e test controller

Per gli scenari di test che usano Visual Studio e Azure Test Plans o Team Foundation Server (TFS), non occorre un test controller. Gli agenti per Visual Studio gestiscono l'orchestrazione mediante la comunicazione con Azure Test Plans o TFS. Uno scenario potrebbe essere l'esecuzione continuativa di test per i flussi di lavoro di compilazione e versione in Azure Test Plans o TFS.

Potrebbe anche essere utile valutare se è preferibile usare la [gestione di compilazione e versione](use-build-or-rm-instead-of-lab-management.md) anziché Lab Management.

## <a name="system-requirements"></a>Requisiti di sistema

La tabella seguente illustra i requisiti di sistema per l'installazione dell'agente di test o del test controller per Visual Studio:

| Elemento | Requisiti |
| ---- | ------------ |
| **Agente** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard e Datacenter<br />Windows Server 2012 R2 |
| **Controller** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard e Datacenter<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Installare il test controller e gli agenti di test

È possibile scaricare gli agenti per Visual Studio da [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Cercare *Agents per Visual Studio 2019*, selezionare *Agente* o *Controller* e quindi scegliere *Download*. Eseguire il file eseguibile scaricato per installare l'agente di test o il test controller.

È possibile scaricare gli agenti per Visual Studio 2017, Visual Studio 2015 e Visual Studio 2013 dalla pagina dei [download precedenti](https://visualstudio.microsoft.com/vs/older-downloads/).

Questi programmi di installazione sono disponibili come file ISO per facilitarne l'installazione nelle macchine virtuali.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Versioni compatibili di TFS, Microsoft Test Manager, test controller e agente di test

È possibile combinare diverse versioni di TFS, Microsoft Test Manager, test controller e agente di test come indicato nella tabella seguente:

| TFS | Microsoft Test Manager con Lab Center | Controller | Agente |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: aggiornamento dalla versione 2015 o nuova installazione | 2017 | 2017 | 2017 |
| 2017: aggiornamento dalla versione 2015 o nuova installazione | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017: aggiornamento dalla versione 2015 o nuova installazione | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015: aggiornamento da 2013 | 2013 | 2013 |2013 |
| 2015: nuova installazione | 2013 | 2013 | 2013 |
| 2015: aggiornamento da 2013 o nuova installazione | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

> [!NOTE]
> Gli scenari di gestione lab in Team Foundation Server 2018 e Azure DevOps Services sono deprecati. Per altre informazioni, vedere le [note sulla versione di TFS 2018](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Eseguire l'aggiornamento da agenti di test di Visual Studio 2013

È consigliabile usare gli agenti per Visual Studio in tutti i nuovi scenari di test automatizzato. Per scaricare e installare gli agenti di test nel computer, è possibile usare l'attività *Deploy Test Agents* (Distribuisci agenti di test) in una pipeline di compilazione.

La tabella seguente visualizza gli scenari supportati da Agents per Visual Studio 2013 e le alternative per Team Foundation Server (TFS) 2015 e Azure Test Plans:

| Scenari supportati da Agents per Visual Studio 2013 | Alternativa in TFS e Azure Test Plans |
| - | - |
| Flusso di lavoro compilazione, distribuzione e test in Visual Studio | Gli utenti possono usare una [pipeline di compilazione](/azure/devops/pipelines/index?view=vsts) (non una compilazione XAML) per gli scenari di compilazione, distribuzione e test in TFS. |
| Test di carico (test delle prestazioni) usando computer remoti in posizioni locali | Per eseguire i test di carico in locale, usare Test Controller e Test Agents 2013 Update 5. |
| Esecuzione remota di test automatizzati da Microsoft Test Manager usando un ambiente lab | Attualmente non è disponibile nessuna alternativa per questo scenario. È consigliabile usare l'attività Esegui test funzionali nelle definizioni di compilazione e di versione (non in una compilazione XAML) per eseguire i test in modalità remota. |
| Sviluppatori che eseguono test remoti in Visual Studio | Non è più supportato. |
