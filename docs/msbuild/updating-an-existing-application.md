---
title: Aggiornamento di un'applicazione esistente per MSBuild 15 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf1c226fceff6ea17a7f83d750a93d6406a31c7d
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263727"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Aggiornamento di un'applicazione esistente per MSBuild 15

Nelle versioni di MSBuild precedenti a 15.0, MSBuild viene caricato dalla Global Assembly Cache (GAC) e le estensioni di MSBuild vengono installate nel Registro di sistema. In questo modo tutte le applicazioni usano la stessa versione di MSBuild e accedono allo stesso set di strumenti, ma impediscono le installazioni side-by-side di versioni diverse di Visual Studio.

Per supportare installazioni più rapide, ridotte e side-by-side, Visual Studio 2017 e versioni successive non caricano più MSBuild nella Global Assembly Cache, né modificano il Registro di sistema. Purtroppo questo significa che le applicazioni che intendo usare l'API di MSBuild per valutare o compilare i progetti non possono basarsi in modo implicito sull'installazione di Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Uso di MSBuild da Visual Studio

Per garantire che le compilazioni a livello di programmazione dell'applicazione corrispondano a quelle eseguite all'interno di Visual Studio o *MSBuild.exe*, caricare gli assembly di MSBuild da Visual Studio e usare l'SDK disponibile all'interno di Visual Studio. Il pacchetto NuGet Microsoft.Build.Locator semplifica questo processo.

## <a name="use-microsoftbuildlocator"></a>Uso di Microsoft.Build.Locator

Se si ridistribuisce *Microsoft.Build.Locator.dll* con l'applicazione, non è necessario distribuire altri assembly di MSBuild.

L'aggiornamento di un progetto per usare MSBuild 15 e l'API del localizzatore richiede alcune modifiche nel progetto, descritte di seguito. Per un esempio delle modifiche necessarie per aggiornare un progetto, vedere la sezione relativa ai [commit eseguiti in un progetto di esempio nel repository MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Modificare i riferimenti di MSBuild

Per accertarsi che MSBuild venga caricato da una posizione centrale, non distribuire gli assembly con l'applicazione.

Il meccanismo per modificare il progetto al fine di evitare il caricamento di MSBuild da una posizione centrale varia a seconda del modo in cui si fa riferimento a MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Uso di pacchetti NuGet (opzione consigliata)

Queste istruzioni presuppongono che si usino [riferimenti NuGet in stile ](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files).

Modificare i file di progetto per fare riferimento agli assembly di MSBuild dai pacchetti NuGet. Specificare `ExcludeAssets=runtime` per indicare a NuGet che gli assembly sono necessari solo in fase di compilazione e non devono essere copiati nella directory di output.

La versione principale e secondaria dei pacchetti di MSBuild deve essere precedente o uguale alla versione minima di Visual Studio che si intende supportare. Ad esempio, se si desidera supportare Visual Studio 2017 e versioni successive, fare riferimento alla versione del pacchetto `15.1.548`.

È ad esempio possibile usare questo codice XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Uso di assembly di estensione

Se non è possibile usare pacchetti NuGet, è possibile fare riferimento agli assembly di MSBuild distribuiti con Visual Studio. Se si fa direttamente riferimento a MSBuild, verificare che non venga copiato nella directory di output impostando `Copy Local` su `False`. Nel file di progetto, apparirà come segue:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Reindirizzamenti di binding

Facendo automaticamente riferimento al pacchetto Microsoft.Build.Locator, è possibile garantire che l'applicazione usi i reindirizzamenti di associazione richiesti di tutte le versioni degli assembly di MSBuild alla versione `15.1.0.0`.

### <a name="ensure-output-is-clean"></a>Garantire l'eliminazione dell'output

Compilare il progetto ed esaminare la directory di output per verificare che non contenga alcun assembly *Microsoft.Build.\*.dll* diverso da *Microsoft.Build.Locator.dll*, aggiunto al passaggio successivo.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Aggiungere un riferimento al pacchetto per Microsoft.Build.Locator

Aggiungere un riferimento al pacchetto NuGet per [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Non specificare `ExcludeAssets=runtime` per il pacchetto Microsoft.Build.Locator.

### <a name="register-instance-before-calling-msbuild"></a>Registrare l'istanza prima di chiamare MSBuild

Aggiungere una chiamata all'API del localizzatore prima di chiamare qualsiasi metodo che usi MSBuild.

Il modo più semplice per aggiungere la chiamata all'API del localizzatore consiste nell'aggiungere una chiamata a

```csharp
MSBuildLocator.RegisterDefaults();
```

nel codice di avvio dell'applicazione.

Per un controllo più capillare sul caricamento di MSBuild, è possibile selezionare un risultato di `MSBuildLocator.QueryVisualStudioInstances()` da passare manualmente a `MSBuildLocator.RegisterInstance()`, ma in genere questa operazione non è necessaria.
