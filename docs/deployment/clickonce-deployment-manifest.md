---
title: Manifesto della distribuzione ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d2f3383731fcfa314c3b936cd42002186012439
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900479"
---
# <a name="clickonce-deployment-manifest"></a>Manifesto di distribuzione ClickOnce
Un manifesto della distribuzione è un file XML che descrive una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], inclusa l'identificazione della versione corrente dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] da distribuire.

 I manifesti della distribuzione dispongono degli elementi e degli attributi riportati di seguito.

| Elemento | Descrizione | Attributi |
| - | - | - |
| [\<assembly> Element](../deployment/assembly-element-clickonce-deployment.md) | Obbligatorio. Elemento di primo livello. | `manifestVersion` |
| [\<assemblyIdentity> Element](../deployment/assemblyidentity-element-clickonce-deployment.md) | Obbligatorio. Identifica il manifesto dell'applicazione per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture` |
| [\<description> Element](../deployment/description-element-clickonce-deployment.md) | Obbligatorio. Identifica le informazioni sull'applicazione usate per creare una shell e l'elemento **Installazione applicazioni** nel Pannello di controllo. | `publisher`<br /><br /> `product`<br /><br /> `supportUrl` |
| [\<deployment> Element](../deployment/deployment-element-clickonce-deployment.md) | Facoltativo. Identifica gli attributi usati per la distribuzione degli aggiornamenti e l'esposizione al sistema. | `install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters` |
| [\<compatibleFrameworks> Element](../deployment/compatibleframeworks-element-clickonce-deployment.md) | Obbligatorio. Identifica le versioni di .NET Framework in cui è possibile installare ed eseguire questa applicazione. | `SupportUrl` |
| [\<dependency> Element](../deployment/dependency-element-clickonce-deployment.md) | Obbligatorio. Identifica la versione dell'applicazione da installare per la distribuzione e il percorso del manifesto dell'applicazione. | `preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size` |
| [\<publisherIdentity> Element](../deployment/publisheridentity-element-clickonce-deployment.md) | Obbligatorio per i manifesti firmati. Contiene informazioni sull'editore che ha firmato questo manifesto della distribuzione. | `Name`<br /><br /> `issuerKeyHash` |
| [\<Signature> Element](../deployment/signature-element-clickonce-deployment.md) | Facoltativo. Contiene le informazioni necessarie per apporre una firma digitale al manifesto della distribuzione. | nessuno |
| [\<customErrorReporting> Element](../deployment/customerrorreporting-element-clickonce-deployment.md) | Facoltativo. Specifica un URI da visualizzare quando si verifica un errore. | URI |

## <a name="remarks"></a>Note
 Il file manifesto della distribuzione identifica una distribuzione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], incluse la versione corrente e altre impostazioni della distribuzione. Fa riferimento al manifesto dell'applicazione, che descrive la versione corrente dell'applicazione e tutti i file contenuti all'interno della distribuzione.

 Per altre informazioni, vedere [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Posizione file
 Il file manifesto della distribuzione fa riferimento al manifesto dell'applicazione corretto per la versione corrente dell'applicazione. Quando si rende disponibile una nuova versione di una distribuzione dell'applicazione, è necessario aggiornare il manifesto della distribuzione in modo che faccia riferimento al nuovo manifesto dell'applicazione.

 Il file manifesto della distribuzione deve avere un nome sicuro e può anche contenere certificati per la convalida dell'editore.

## <a name="file-name-syntax"></a>Sintassi del nome file
 Il nome di un file manifesto della distribuzione deve terminare con l'estensione *application*.

## <a name="examples"></a>Esempi
 L'esempio di codice seguente illustra un manifesto della distribuzione.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <assemblyIdentity
    name="My Application Deployment.app"
    version="1.0.0.0"
    publicKeyToken="43cb1e8e7a352766"
    language="neutral"
    processorArchitecture="x86"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <description
    asmv2:publisher="My Company Name"
    asmv2:product="My Application"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <deployment install="true">
    <subscription>
      <update>
        <expiration maximumAge="0" unit="days" />
      </update>
    </subscription>
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />
  </deployment>
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />
  </compatibleFrameworks>
  <dependency>
    <dependentAssembly
      dependencyType="install"
      codebase="1.0.0.0\My Application Deployment.exe.manifest"
      size="6756">
      <assemblyIdentity
        name="My Application Deployment.exe"
        version="1.0.0.0"
        publicKeyToken="43cb1e8e7a352766"
        language="neutral"
        processorArchitecture="x86"
        type="win32" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></asmv1:assembly>
```

## <a name="see-also"></a>Vedere anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)