---
title: Elemento Otherwise (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fee2dd064b556596f27ae2130697cdd9435d8185
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963741"
---
# <a name="otherwise-element-msbuild"></a>Elemento Otherwise (MSBuild)
Specifica il blocco di codice da eseguire se e solo se le condizioni di tutti gli elementi `When` restituiscono `false`.

 \<Project> \<Choose> \<When> \<Choose> ... \<Otherwise> \<Choose> ...

## <a name="syntax"></a>Sintassi

```xml
<Otherwise>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</Otherwise>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Choose](../msbuild/choose-element-msbuild.md)|Elemento facoltativo.<br /><br /> Valuta gli elementi figlio per selezionare una sezione del codice da eseguire. Possono esistere zero o più elementi `Choose` in un elemento `Otherwise`.|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento facoltativo.<br /><br /> Contiene un set di elementi [Item](../msbuild/item-element-msbuild.md) definiti dall'utente. Possono esistere zero o più elementi `ItemGroup` in un elemento `Otherwise`.|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento facoltativo.<br /><br /> Contiene un set di elementi [Property](../msbuild/property-element-msbuild.md) definiti dall'utente. Possono esistere zero o più elementi `PropertyGroup` in un elemento `Otherwise`.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[Choose](../msbuild/choose-element-msbuild.md)|Valuta gli elementi figlio per selezionare una sezione del codice da eseguire.|

## <a name="remarks"></a>Osservazioni
 In un elemento `Choose` può esistere un solo un elemento `Otherwise` ed è necessario che sia l'ultimo.

 Gli elementi `Choose`, `When` e `Otherwise` vengono usati insieme per consentire di selezionare una sezione di codice da eseguire tra diverse alternative. Per altre informazioni, vedere [Costrutti condizionali di MSBuild](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Esempio
 Nel progetto riportato di seguito l'elemento `Choose` viene usato per selezionare il set di valori delle proprietà da impostare negli elementi `When`. Se gli attributi `Condition` di entrambi gli elementi `When` restituiscono `false`, vengono impostati i valori delle proprietà dell'elemento `Otherwise`.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
        </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>Vedere anche
- [Costrutti condizionali](../msbuild/msbuild-conditional-constructs.md)
- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
