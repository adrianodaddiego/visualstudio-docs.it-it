---
title: Protezione delle applicazioni ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a2610c1fef92bb77d150dad7972bb991b6ef4a4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686016"
---
# <a name="securing-clickonce-applications"></a>Protezione di applicazioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le applicazioni[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sono soggette ai vincoli di sicurezza dall'accesso di codice in .NET Framework che consentono di limitare l'accesso del codice alle risorse e alle operazioni protette. Per poter scrivere correttamente le applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , è quindi importante comprendere le implicazioni di questo tipo di sicurezza. Le applicazioni possono usare l'attendibilità totale o le aree parziali, ad esempio le aree Internet e Intranet, per limitare l'accesso.  
  
 Inoltre, ClickOnce usa i certificati per verificare l'autenticità dell'editore dell'applicazione e per firmare i manifesti dell'applicazione e della distribuzione al fine di dimostrare che i file non sono stati alterati. La firma è un passaggio facoltativo, che semplifica la modifica dei file dell'applicazione dopo la generazione dei manifesti. Senza manifesti firmati, è tuttavia difficile garantire che il programma di installazione dell'applicazione non venga manomesso in attacchi alla sicurezza di tipo man-in-the-middle. Per questo motivo, è consigliabile firmare i manifesti dell'applicazione e della distribuzione per proteggere le applicazioni.  
  
## <a name="zones"></a>Aree  
 Le applicazioni distribuite con la tecnologia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sono limitate a un set di autorizzazioni e azioni definite dall'area di sicurezza. Le aree di sicurezza vengono definite in Internet Explorer e si basano sul percorso dell'applicazione. Nella seguente tabella sono elencate le autorizzazioni predefinite in base al percorso di distribuzione:  
  
|Percorso di distribuzione|Area di sicurezza|  
|-------------------------|-------------------|  
|Esecuzione dal Web|Area Internet|  
|Installazione dal Web|Area Internet|  
|Installazione da una condivisione file in rete|Area Intranet locale|  
|Installazione da CD|Attendibilità totale|  
  
 Le autorizzazioni predefinite dipendono dal percorso di distribuzione della versione originale dell'applicazione. Gli eventuali aggiornamenti erediteranno tali autorizzazioni. Se l'applicazione è configurata in modo da controllare la disponibilità degli aggiornamenti in un percorso Web o di rete e viene rilevata la disponibilità di una versione più recente, è possibile che l'installazione originale riceva autorizzazioni per l'area Internet o Intranet anziché autorizzazioni di attendibilità totale. Per evitare che la richiesta venga visualizzata, l'amministratore di sistema può specificare criteri di distribuzione ClickOnce che definiscano uno specifico editore dell'applicazione come fonte attendibile. Per i computer in cui viene distribuito questi criteri, le autorizzazioni verranno concesse automaticamente senza alcun intervento da parte dell'utente. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Per configurare la distribuzione di applicazioni attendibili, è possibile installare il certificato nel computer o a livello aziendale. Per altre informazioni, vedere [Procedura: Aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Criteri di sicurezza per l'accesso al codice  
 Le autorizzazioni per un'applicazione sono determinate dalle impostazioni nell'elemento [\<trustInfo> Element](../deployment/trustinfo-element-clickonce-application.md) del manifesto dell'applicazione. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera automaticamente queste informazioni in base alle impostazioni presenti nella pagina delle proprietà **Sicurezza** del progetto. A un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vengono concesse solo le autorizzazioni specifiche richieste. Ad esempio, se per l'accesso ai file sono necessarie autorizzazioni di attendibilità totale, ma l'applicazione richiede solo l'autorizzazione di accesso ai file, verrà concessa solo questa autorizzazione e non quelle di attendibilità totale. Quando si sviluppa l'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , è necessario assicurarsi di richiedere solo le autorizzazioni specifiche necessarie per l'applicazione. Nella maggior parte dei casi è possibile usare le aree Internet o Intranet locale per limitare l'applicazione a un'attendibilità parziale. Per altre informazioni, vedere [Procedura: Set a Security Zone for a ClickOnce Application](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Se l'applicazione richiede autorizzazioni personalizzate, è possibile creare un'area personalizzata. Per altre informazioni, vedere [Procedura: Impostare autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Se si aggiunge un'autorizzazione non inclusa nel set di autorizzazioni predefinito per l'area da cui viene distribuita l'applicazione, all'utente finale verrà chiesto di concedere l'autorizzazione al momento dell'installazione o dell'aggiornamento. Per evitare che la richiesta venga visualizzata, l'amministratore di sistema può specificare criteri di distribuzione ClickOnce che definiscano uno specifico editore dell'applicazione come fonte attendibile. Sui computer in cui vengono distribuiti questi criteri, le autorizzazioni verranno concesse automaticamente senza alcun intervento da parte dell'utente.  
  
 Uno sviluppatore ha la responsabilità di assicurarsi che l'applicazione venga eseguita con le autorizzazioni appropriate. Se l'applicazione richiede autorizzazioni all'esterno di un'area durante il run-time, è possibile che venga visualizzata un'eccezione di sicurezza. In[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è possibile eseguire il debug dell'applicazione all'interno dell'area di sicurezza di destinazione e vengono inoltre fornite informazioni utili per lo sviluppo di applicazioni sicure. Per altre informazioni, vedere [Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Per altre informazioni sulla sicurezza per l'accesso al codice e su ClickOnce, vedere [Code Access Security for ClickOnce Applications](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certificati per la firma del codice  
 Per pubblicare un'applicazione tramite la tecnologia di distribuzione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , è possibile firmare il manifesto dell'applicazione e della distribuzione con una coppia di chiavi pubblica/privata. Gli strumenti per firmare un manifesto sono disponibili nella pagina **Firma** di **Progettazione progetti**. Per altre informazioni, vedere [Signing Page, Project Designer](../ide/reference/signing-page-project-designer.md). In alternativa, è possibile firmare i manifesti con un file di chiave durante il processo di pubblicazione, tramite la Pubblicazione guidata.  
  
 Durante l'installazione, dopo la firma dei manifesti, nella finestra di dialogo Autorizzazioni verranno visualizzate le informazioni sull'editore basate sulla firma Authenticode, per dimostrare all'utente che l'applicazione proviene da una fonte attendibile.  
  
 Per altre informazioni su ClickOnce e sui certificati, vedere [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Autenticazione basata su form ASP.NET  
 Per controllare le distribuzioni cui può accedere ciascun utente, è consigliabile non consentire l'accesso anonimo alle applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuite su un server Web. La soluzione migliore consiste nel concedere agli utenti l'accesso alle distribuzioni installate in base all'identità, usando l'autenticazione di Windows.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] non supporta l'autenticazione basata su form ASP.NET perché prevede l'uso di cookie permanenti. Questi comportano un rischio di sicurezza in quanto rimangono nella cache di Internet Explorer e sono quindi vulnerabili ad attacchi di pirateria. Se pertanto si distribuiscono applicazioni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , non è supportato alcuno scenario di autenticazione ad eccezione dell'autenticazione di Windows.  
  
## <a name="passing-arguments"></a>Passaggio di argomenti  
 Se è necessario passare argomenti a un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , è opportuno valutare altre implicazioni sulla sicurezza. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] consente agli sviluppatori di fornire una stringa di query alle applicazioni distribuite sul Web. La stringa di query è una serie di coppie nome/valore aggiunte alla fine dell'URL usato per avviare l'applicazione:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Gli argomenti delle stringhe di query sono disabilitati per impostazione predefinita. Per attivarli, nel manifesto di distribuzione dell'applicazione deve essere impostato l'attributo `trustUrlParameters` . Questo valore può essere impostato da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e da MageUI.exe. Per informazioni dettagliate su come abilitare il passaggio di stringhe di query, vedere [come: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Non passare mai argomenti recuperati tramite una stringa di query direttamente a un database o alla riga di comando senza verificare che gli argomenti siano sicuri. Sono considerati non sicuri gli argomenti che includono caratteri di escape di database o da riga di comando che possono consentire a un utente malintenzionato di modificare l'applicazione eseguendo comandi arbitrari.  
  
> [!NOTE]
> Gli argomenti delle stringhe di query sono l'unico modo per passare argomenti a un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] all'avvio. Non è possibile passare argomenti a un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dalla riga di comando.  
  
## <a name="deploying-obfuscated-assemblies"></a>Distribuzione di assembly offuscati  
 È possibile offuscare l'applicazione con Dotfuscator per impedire ad altri utenti di decodificare il codice. L'offuscamento degli assembly tuttavia non è integrato nel processo di distribuzione dell'IDE Visual Studio o ClickOnce. Sarà necessario pertanto eseguire l'offuscamento al di fuori del processo di distribuzione, eventualmente usando un passaggio di post-compilazione. Dopo aver compilato il progetto, eseguire manualmente i passaggi seguenti al di fuori di Visual Studio:  
  
1. Eseguire l'offuscamento usando Dotfuscator.  
  
2. Usare Mage.exe o MageUI.exe per generare i manifesti ClickOnce e firmarli. Per altre informazioni, vedere [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) e [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
3. Pubblicare manualmente (copiare) i file nel percorso di origine della distribuzione, ovvero nel server Web, nella condivisione UNC o su CD-ROM.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
