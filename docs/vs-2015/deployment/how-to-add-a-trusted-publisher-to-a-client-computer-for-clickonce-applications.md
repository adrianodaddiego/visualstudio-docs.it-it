---
title: 'Procedura: Aggiungere un autore attendibile a un Computer Client per applicazioni ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7129d8de5e37b24304b7f1cbf862e4cd299cdf72
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442210"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Procedura: Aggiungere un autore attendibile a un Computer Client per applicazioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con la distribuzione di applicazioni attendibili, è possibile configurare i computer client in modo che le applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] siano eseguite con un livello di attendibilità superiore senza chiedere conferma all'utente. Le procedure seguenti illustrano come usare lo strumento da riga di comando CertMgr.exe per aggiungere un certificato dell'autore all'archivio editori attendibili in un computer client.  
  
 I comandi utilizzati variano leggermente a seconda che l'autorità di certificazione (CA) che ha emesso il certificato sia parte della radice attendibile del client. Se un computer client Windows fa parte di un dominio conterrà, in un elenco, le autorità di certificazione considerate attendibili. Questo elenco è in genere configurato dall'amministratore di sistema. Se il certificato è stato rilasciato da una di queste fonti attendibili o da un'autorità di certificazione legata a una di queste fonti attendibili, è possibile aggiungere il certificato all'archivio radice attendibile del client. Se invece il certificato non è stato rilasciato da una di queste fonti attendibili, è necessario aggiungere il certificato sia all'archivio radice attendibile del client sia all'archivio autori attendibili.  
  
> [!NOTE]
> È necessario aggiungere i certificati in questo modo su ogni computer client in cui si intende distribuire un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] che richiede autorizzazioni elevate. I certificati possono essere aggiunti manualmente o mediante un'applicazione distribuita nei client. È sufficiente configurare questi computer una volta, dopo di che è possibile distribuire un numero qualsiasi di applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] firmate con lo stesso certificato.  
  
 È anche possibile aggiungere un certificato a un archivio a livello di codice tramite la classe <xref:System.Security.Cryptography.X509Certificates.X509Store> .  
  
 Per una panoramica della distribuzione di applicazioni attendibili, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Per aggiungere un certificato nell'archivio autori attendibili sotto la radice attendibile  
  
1. Ottenere un certificato digitale da un'autorità di certificazione.  
  
2. Esportare il certificato nel formato Base64 X.509 (.cer). Per altre informazioni sui formati di certificato, vedere [Esportare un certificato](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3. Dal prompt dei comandi nei computer client eseguire il comando seguente:  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Per aggiungere un certificato nell'archivio autori attendibili sotto un'altra radice  
  
1. Ottenere un certificato digitale da un'autorità di certificazione.  
  
2. Esportare il certificato nel formato Base64 X.509 (.cer). Per altre informazioni sui formati di certificato, vedere [Esportare un certificato](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3. Dal prompt dei comandi nei computer client eseguire il comando seguente:  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [Procedura: Abilitare le impostazioni di sicurezza ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Procedura: Impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: Impostare autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: Aggiungere un autore attendibile a un Computer Client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Procedura: Firmare nuovamente i manifesti dell'applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Procedura: Configurare il comportamento di richiesta di attendibilità di ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
