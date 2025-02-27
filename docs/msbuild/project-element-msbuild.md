---
title: Elemento Project (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c69d010f9a4e834f9435616747c2776786706445
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999333"
---
# <a name="project-element-msbuild"></a>Elemento Project (MSBuild)
Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .

## <a name="syntax"></a>Sintassi

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
    <Choose>... </Choose>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Target>... </Target>
    <UsingTask.../>
    <ProjectExtensions>... </ProjectExtensions>
    <Import... />
</Project>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

| Attributo | Description |
|------------------------| - |
| `DefaultTargets` | Attributo facoltativo.<br /><br /> Destinazione o destinazioni predefinite che saranno il punto di ingresso della compilazione se non è stata specificata alcuna destinazione. Per specificare più destinazioni, usare il punto e virgola (;) come delimitatore.<br /><br /> Se non viene specificata alcuna destinazione predefinita nell'attributo `DefaultTargets` né nella riga di comando di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] il motore esegue la prima destinazione nel file di progetto dopo che gli elementi [Import](../msbuild/import-element-msbuild.md) sono stati valutati. |
| `InitialTargets` | Attributo facoltativo.<br /><br /> Destinazione o destinazioni iniziali da eseguire prima delle destinazioni specificate nell'attributo `DefaultTargets` o nella riga di comando. Per specificare più destinazioni, usare il punto e virgola (`;`) come delimitatore. Se più file importati definiscono `InitialTargets`, tutte le destinazioni menzionate verranno eseguite nell'ordine in cui si rilevano le importazioni. |
| `Sdk` | Attributo facoltativo. <br /><br /> Nome e versione facoltativa dell'SDK da usare per creare istruzioni Import implicite che vengono aggiunte al file PROJ. Se non viene specificata alcuna versione, MSBuild tenterà di risolvere una versione predefinita.  Ad esempio, `<Project Sdk="Microsoft.NET.Sdk" />` o `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Attributo facoltativo.<br /><br /> Versione del set di strumenti usato da MSBuild per determinare i valori per $(MSBuildBinPath) e $(MSBuildToolsPath). |
| `TreatAsLocalProperty` | Attributo facoltativo.<br /><br /> Nomi di proprietà che non verranno considerati come globali. Questo attributo impedisce a proprietà della riga di comando specifiche di eseguire l'override dei valori delle proprietà impostati in un file di progetto o di destinazioni e di tutte le importazioni successive. Per specificare più proprietà, usare il punto e virgola (;) come delimitatore.<br /><br /> Le proprietà globali in genere eseguono l'override dei valori delle proprietà impostati nel file di progetto o di destinazioni. Se la proprietà è elencata nel valore `TreatAsLocalProperty`, il valore della proprietà globale non esegue l'override dei valori della proprietà impostati in tale file e delle importazioni successive. Per altre informazioni, vedere [Procedura: Compilare gli stessi file di origine con opzioni diverse](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Nota:**  Per impostare le proprietà globali al prompt dei comandi, usare l'opzione **-property** (o **-p** ). È anche possibile impostare o modificare le proprietà globali per i progetti figlio in una compilazione a più progetti usando l'attributo `Properties` dell'attività di MSBuild. Per altre informazioni, vedere [Attività MSBuild](../msbuild/msbuild-task.md). |
| `xmlns` | Attributo facoltativo.<br /><br /> Quando specificato, l'attributo `xmlns` deve avere il valore di `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Elementi figlio

| Elemento | Description |
| - | - |
| [Choose](../msbuild/choose-element-msbuild.md) | Elemento facoltativo.<br /><br /> Valuta gli elementi figlio per selezionare un set di elementi `ItemGroup` e/o di elementi `PropertyGroup` da valutare. |
| [Import](../msbuild/import-element-msbuild.md) | Elemento facoltativo.<br /><br /> Consente a un file di progetto importare un altro file di progetto. Possono esistere zero o più elementi `Import` in un progetto. |
| [ImportGroup](../msbuild/importgroup-element.md) | Elemento facoltativo.<br /><br /> Contiene una raccolta di elementi `Import` raggruppati in una condizione facoltativa. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Elemento facoltativo.<br /><br /> Elemento di raggruppamento per singoli elementi. Gli elementi vengono specificati usando l'elemento [Item](../msbuild/item-element-msbuild.md). Possono esistere zero o più elementi `ItemGroup` in un progetto. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Elemento facoltativo.<br /><br /> Consente di definire un set di definizioni di elementi, ovvero valori di metadati applicati a tutti gli elementi nel progetto per impostazione predefinita. ItemDefinitionGroup ovvia alla necessità di usare le attività`CreateItem` e `CreateProperty`. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | Elemento facoltativo.<br /><br /> Consente di rendere permanente informazioni non di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] in un file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Possono esistere zero o un elemento `ProjectExtensions` in un progetto. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Elemento facoltativo.<br /><br /> Elemento di raggruppamento per singole proprietà. Le proprietà vengono specificate usando l'elemento [Property](../msbuild/property-element-msbuild.md). Possono esistere zero o più elementi `PropertyGroup` in un progetto. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | Elemento facoltativo.<br /><br /> Fa riferimento a un SDK di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Questo elemento può essere usato come alternativa all'attributo Sdk. |
| [Destinazione](../msbuild/target-element-msbuild.md) | Elemento facoltativo.<br /><br /> Contiene un set di attività da eseguire in sequenza in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Le attività vengono specificate usando l'elemento [Task](../msbuild/task-element-msbuild.md). Possono esistere zero o più elementi `Target` in un progetto. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Elemento facoltativo.<br /><br /> Consente di registrare attività in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Possono esistere zero o più elementi `UsingTask` in un progetto. |

### <a name="parent-elements"></a>Elementi padre
 Nessuno.

## <a name="see-also"></a>Vedere anche
- [Procedura: Specificare quale destinazione compilare per prima](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)
- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
