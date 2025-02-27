---
title: 'Procedura: Usare la stessa destinazione in più file di progetto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8674f0c8ed833ac8db80f30f616aa8b0dbf4cf9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977184"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Procedura: Usare la stessa destinazione in più file di progetto
Se sono stati creati più file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], è possibile che sia stato necessario usare le stesse attività e destinazioni in file di progetto diversi. Anziché includere in ogni file di progetto la descrizione completa di tali attività o destinazioni, è possibile salvare una destinazione in un file di progetto separato e importarlo in qualsiasi altro progetto in cui si intende usare la destinazione.

## <a name="use-the-import-element"></a>Usare l'elemento Import
 L'elemento `Import` consente di inserire un file di progetto in un altro file di progetto. Il file di progetto importato deve essere un file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] valido e deve contenere codice XML in formato corretto. L'attributo `Project` specifica il percorso del file di progetto importato. Per altre informazioni sull'elemento `Import`, vedere [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Per importare un progetto

1. Nel file di progetto di importazione definire tutte le proprietà e gli elementi usati come parametri per le proprietà e gli elementi del progetto importato.

2. Usare l'elemento `Import` per importare il progetto. Ad esempio:

     `<Import Project="MyCommon.targets"/>`

3. Dopo l'elemento `Import`, definire tutte le proprietà e gli elementi che devono eseguire l'override delle definizioni predefinite delle proprietà e degli elementi presenti nel progetto importato.

## <a name="order-of-evaluation"></a>Ordine di valutazione
 Quando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] raggiunge un elemento `Import`, il progetto importato viene correttamente inserito nel progetto di importazione nella stessa posizione dell'elemento `Import`. La posizione dell'elemento `Import` può quindi influire sui valori delle proprietà e degli elementi ed è importante conoscere sia le proprietà e gli elementi impostati dal progetto importato, sia le proprietà e gli elementi usati dal progetto.

 Quando si compila il progetto, vengono valutate prima tutte le proprietà e dopo gli elementi. Il codice XML seguente, ad esempio, definisce il file di progetto importato *MyCommon.targets*:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 Il codice XML seguente definisce *MyApp.proj*, che esegue l'importazione di *MyCommon.targets*:

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 Quando si compila il progetto, viene visualizzato il messaggio seguente:

 `Name="MyCommon"`

 Poiché il progetto viene importato dopo che è stata definita la proprietà `Name` in *MyApp.proj*, la definizione di `Name` in *MyCommon.targets* esegue l'override della definizione presente in *MyApp.proj*. Se il progetto venisse importato prima di definire la proprietà Name, durante la compilazione verrebbe visualizzato il messaggio seguente:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Usare l'approccio seguente durante l'importazione dei progetti

1. Nel file di progetto definire tutte le proprietà e gli elementi usati come parametri per le proprietà e gli elementi del progetto importato.

2. Importare il progetto.

3. Nel file di progetto definire tutte le proprietà e gli elementi che devono eseguire l'override delle definizioni predefinite delle proprietà e degli elementi presenti nel progetto importato.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato il file *MyCommon.targets* importato dal secondo esempio di codice. Il file con estensione *targets* valuta le proprietà ottenute dal progetto di importazione per configurare la compilazione.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene importato il file *MyCommon.targets*.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>Vedere anche
- [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Destinazioni](../msbuild/msbuild-targets.md)