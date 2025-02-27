---
title: Attività ResourcesGenerator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ef54bdc3b3c692869b4883cf4f92293551a1958
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996771"
---
# <a name="resourcesgenerator-task"></a>Attività ResourcesGenerator
L'attività <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> incorpora una o più risorse (con estensione *jpg*, *ico*, *bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in formato binario e altri tipi di estensione) in un file con estensione *resources*.

## <a name="task-parameters"></a>Parametri dell'attività

|Parametro|Description|
|---------------|-----------------|
|`OutputPath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso della directory di output. Se il percorso non è assoluto, verrà trattato come percorso relativo alla directory di progetto radice.|
|`OutputResourcesFile`|Parametro di output **ITaskItem[]** obbligatorio.<br /><br /> Specifica il percorso e il nome del file con estensione *resources* generato. Se il percorso non è assoluto, il file  *resources* verrà generato come percorso relativo alla directory di progetto radice.|
|`ResourcesFiles`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica una o più risorse da incorporare nel file con estensione *resources* generato.|

## <a name="example"></a>Esempio
 L'esempio seguente illustra come generare un file con estensione *resources* con una sola risorsa con estensione *bmp*. La risorsa con estensione *bmp* viene generata in una directory relativa alla directory radice del progetto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Riferimenti delle attività MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)