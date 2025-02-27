---
title: 'Procedura: Usare ClickOnce per distribuire applicazioni eseguibili in più versioni di .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 164fe64f360e41c06ef3f7bfd2d8091a6ebefecd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679941"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Procedura: Usare ClickOnce per distribuire applicazioni eseguibili in più versioni di .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile distribuire un'applicazione destinata a più versioni di .NET Framework tramite la tecnologia di distribuzione ClickOnce. Ciò richiede di generare e aggiornare i manifesti dell'applicazione e della distribuzione.  
  
> [!NOTE]
> Prima di modificare l'applicazione a più versioni di .NET Framework di destinazione, è necessario assicurarsi che l'applicazione viene eseguita con più versioni di .NET Framework. Versione common language runtime è diverso tra [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] rispetto a .NET Framework 2.0, .NET Framework 3.0 e .NET Framework 3.5.  
  
 Questo processo sono necessari i passaggi seguenti:  
  
1. Generare i manifesti dell'applicazione e distribuzione.  
  
2. Modificare il manifesto di distribuzione per visualizzare un elenco di più versioni di .NET Framework.  
  
3. Modificare il file app. config per elencare le versioni di runtime di .NET Framework compatibili.  
  
4. Modificare il manifesto dell'applicazione per contrassegnare gli assembly dipendenti degli assembly di .NET Framework.  
  
5. Firmare il manifesto dell'applicazione.  
  
6. Aggiornare e firmare il manifesto della distribuzione.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Per generare i manifesti dell'applicazione e distribuzione  
  
- Usare la procedura guidata di pubblicazione o la pagina di pubblicazione di creazione progetti per pubblicare l'applicazione e generare l'applicazione e i file manifesto di distribuzione. Per altre informazioni, vedere [Procedura: Pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) oppure [pubblicare Page, Project Designer](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Per modificare il manifesto di distribuzione per visualizzare un elenco di più versioni di .NET Framework  
  
1. Nella directory di pubblicazione, aprire il manifesto di distribuzione usando l'Editor XML in Visual Studio. Il manifesto di distribuzione ha l'estensione del nome file. Application.  
  
2. Sostituire il codice XML tra i `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` e `</compatibleFrameworks>` elementi con il codice XML che elenca le versioni di .NET Framework supportate per l'applicazione.  
  
     Nella tabella seguente vengono illustrate alcune delle versioni di .NET Framework disponibili e il codice XML corrispondente che è possibile aggiungere al manifesto della distribuzione.  
  
    |Versione di .NET Framework|XML|  
    |----------------------------|---------|  
    |4 Client|\<Framework targetVersion = "4.0" profile = supportedRuntime "Client" = "4.0.30319" / >|  
    |4 Completo|\<Framework targetVersion = "4.0" profile = supportedRuntime "Completo" = "4.0.30319" / >|  
    |3.5 Client|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|  
    |3.5 Completo|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|  
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Per modificare il file app. config per elencare le versioni di runtime di .NET Framework compatibili  
  
1. In Esplora soluzioni aprire il file app. config usando l'Editor XML in Visual Studio.  
  
2. Sostituire (o aggiungere) il codice XML tra i `<startup>` e `</startup>` elementi con il codice XML che elenca i runtime di .NET Framework supportati per l'applicazione.  
  
     Nella tabella seguente vengono illustrate alcune delle versioni di .NET Framework disponibili e il codice XML corrispondente che è possibile aggiungere al manifesto della distribuzione.  
  
    |Versione di runtime di .NET framework|XML|  
    |------------------------------------|---------|  
    |4 Client|\<versione supportedRuntime = sku "v4.0.30319" = ". NETFramework, versione = v4.0, profilo = Client "/ >|  
    |4 Completo|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|  
    |3.5 Completo|\<supportedRuntime version="v2.0.50727"/>|  
    |3.5 Client|\<supportedRuntime version="v2.0.50727" sku="Client"/>|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Per modificare il manifesto dell'applicazione per contrassegnare gli assembly dipendenti degli assembly di .NET Framework  
  
1. Nella directory di pubblicazione, aprire il manifesto dell'applicazione utilizzando l'Editor XML in Visual Studio. Il manifesto di distribuzione ha l'estensione manifest.  
  
2. Aggiungere `group="framework"` per il XML della dipendenza per gli assembly di sentinel (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, e `System.Data.Entity`). Ad esempio, il codice XML dovrebbe essere simile al seguente:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3. Aggiornare il numero di versione il `<assemblyIdentity>` elemento per Microsoft.Windows.CommonLanguageRuntime sul numero di versione di .NET Framework che è il minimo comune denominatore. Ad esempio, se l'applicazione è destinata a .NET Framework 3.5 e [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], utilizzare il 2.0.50727.0 numero di versione e il codice XML dovrebbe essere simile al seguente:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Per aggiornare e firmare nuovamente l'applicazione e distribuzione di manifesti  
  
- Aggiornare e firmare nuovamente i manifesti dell'applicazione e distribuzione. Per altre informazioni, vedere [Procedura: Firmare nuovamente i manifesti dell'applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dipendenza > elemento](../deployment/dependency-element-clickonce-application.md)   
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Schema dei file di configurazione](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)
