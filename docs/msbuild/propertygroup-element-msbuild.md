---
title: Elemento PropertyGroup (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 607c5f2c3cda64e7407203b0c45287a58342b807
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974683"
---
# <a name="propertygroup-element-msbuild"></a>Elemento PropertyGroup (MSBuild)
Contiene un set di elementi [Property](../msbuild/property-element-msbuild.md) definiti dall'utente. Ogni elemento `Property` usato in un progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve essere figlio di un elemento `PropertyGroup`.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Sintassi

```xml
<PropertyGroup Condition="'String A' == 'String B'">
    <Property1>...</Property1>
    <Property2>...</Property2>
</PropertyGroup>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Description|
|---------------|-----------------|
|Condizione|Attributo facoltativo.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Property](../msbuild/property-element-msbuild.md)|Elemento facoltativo.<br /><br /> Nome proprietà definito dall'utente, che contiene il valore della proprietà. Possono esistere zero o più elementi *Property* in un elemento `PropertyGroup`.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Description |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra come impostare le proprietà in base a una condizione. In questo esempio, se il valore della proprietà `CompileConfig` è `DEBUG`, vengono impostate le proprietà `Optimization`, `Obfuscate` e `OutputPath` nell'elemento `PropertyGroup`.

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [Proprietà di MSBuild](../msbuild/msbuild-properties.md)
