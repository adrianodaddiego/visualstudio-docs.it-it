---
title: 'Debug ASP.NET: Requisiti di sistema | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 63a94f9ae6c35ef304af334737a8f206da911afd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402710"
---
# <a name="aspnet-debugging-system-requirements"></a>Debug ASP.NET: Requisiti di sistema
In questo argomento vengono descritti i requisiti software e di sicurezza per gli scenari di debug di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] :

- Debug locale in cui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e l'applicazione Web vengono eseguiti nello stesso computer. Questo scenario presenta due varianti:

  - Il codice [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] risiede nel file system.

  - Il codice [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] risiede in un sito Web IIS.

- Il debug remoto in cui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è in esecuzione in un computer client ed esegue il debug di un'applicazione Web in esecuzione in un computer server remoto.

## <a name="security-requirements"></a>Requisiti di sicurezza
 Per il debug remoto, i computer locale e remoto devono appartenere a una configurazione di dominio o di gruppo di lavoro.

 Per eseguire il debug di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo di lavoro (ospitato da un Pool di applicazioni), è necessario disporre dell'autorizzazione per il debug di tale processo. Per impostazione predefinita [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] runas applicazioni prima di IIS 6.0 il **ASPNET** utente. In IIS 6.0 e IIS 7.0, il **servizio di rete** account è il valore predefinito. Se il processo di lavoro è in esecuzione come **ASPNET**o come **SERVIZIO DI RETE**, per eseguirne il debug è necessario disporre dei privilegi di amministratore.

 > [!IMPORTANT]
 > A partire da Windows Server 2008 R2, è consigliabile usare la [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) come identità per ogni pool di applicazioni.

 Il nome del processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varia in base allo scenario di debug e alla versione di IIS. Per altre informazioni, vedere [Procedura: Trovare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).

 È possibile modificare l'account utente con cui il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] viene eseguito modificando il file machine.config nel server su cui è in esecuzione IIS. Il modo migliore per eseguire questa operazione è usare **Gestione Internet Information Services (IIS)**. Per altre informazioni, vedere [Procedura: Eseguire il processo di lavoro con un account utente](../debugger/how-to-run-the-worker-process-under-a-user-account.md).

 Se si modifica il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] affinché venga eseguito con il proprio account utente, non è necessario essere un amministratore nel server che esegue IIS.

> [!CAUTION]
> Prima di modificare il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in modo che venga eseguito con un account diverso, considerare le possibili conseguenze di un eventuale attacco al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mentre viene eseguito con tale account. Gli account utente ASPNET e SERVIZIO DI RETE vengono eseguiti con autorizzazioni minime, riducendo il più possibile i danni in caso di attacchi al processo. Se è necessario modificare il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in modo che venga eseguito con un account con autorizzazioni più elevate, il danno potenziale è maggiore.

## <a name="see-also"></a>Vedere anche

- [Eseguire il debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Procedura: Eseguire il processo di lavoro con un account utente](../debugger/how-to-run-the-worker-process-under-a-user-account.md)