---
title: 'Procedura: Compilare un progetto con risorse | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7b5357975ff893ca889de07bada83f4524a16c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423008"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Procedura: Compilare un progetto con risorse
Se si stanno compilando le versioni localizzate di un progetto, tutti gli elementi dell'interfaccia utente devono essere separati in file di risorse per le diverse lingue. Se il progetto usa solo stringhe, i file di risorse possono usare file di testo. In alternativa, è possibile usare i file con estensione *resx* come file di risorse.

## <a name="compile-resources-with-msbuild"></a>Compilare le risorse con MSBuild
La raccolta di attività comuni specificata con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] include un'attività `GenerateResource` che è possibile usare per compilare le risorse in file di testo o con estensione *resx*. Questa attività include il parametro `Sources` per specificare i file di risorse da compilare e il parametro `OutputResources` per specificare i nomi dei file di risorse di output. Per altre informazioni sull'attività `GenerateResource`, vedere [Attività GenerateResource](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Per compilare le risorse con MSBuild

1. Identificare i file di risorse del progetto e passarli all'attività `GenerateResource`, come elenchi di elementi o come nomi file.

2. Specificare il parametro `OutputResources` dell'attività `GenerateResource`, che consente di impostare i nomi dei file di risorse di output.

3. Usare l'elemento `Output` dell'attività per archiviare il valore del parametro `OutputResources` in un elemento.

4. Usare l'elemento creato dall'elemento `Output` come input per un'altra attività.

## <a name="example"></a>Esempio
L'esempio di codice seguente illustra come l'elemento `Output` specifica che l'attributo `OutputResources` dell'attività `GenerateResource` conterrà i file di risorse compilati *alpah.resources* e *beta.resources* e che questi due file verranno inseriti nell'elenco di elementi `Resources`. Identificando tali file con estensione *resources* come raccolta di elementi con lo stesso nome, è possibile usarli facilmente come input per un'altra attività, ad esempio l'attività [Csc](../msbuild/csc-task.md).

Questa attività equivale a usare l'opzione **/compile** per [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example"></a>Esempio
Il progetto di esempio seguente contiene due attività: l'attività `GenerateResource` per compilare le risorse e l'attività `Csc` per compilare sia i file di codice sorgente che i file di risorse compilati. I file di risorse compilati dall'attività `GenerateResource` vengono archiviati nell'elemento `Resources` e passati all'attività `Csc`.

```xml
<Project DefaultTargets = "Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <Target Name="Resources">
        <GenerateResource
            Sources="alpha.resx; beta.txt"
            OutputResources="alpha.resources; beta.resources">
            <Output TaskParameter="OutputResources"
                ItemName="Resources"/>
        </GenerateResource>
    </Target>

    <Target Name="Build" DependsOnTargets="Resources">
        <Csc Sources="hello.cs"
                Resources="@(Resources)"
                OutputAssembly="hello.exe"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche
- [MSBuild](../msbuild/msbuild.md)
- [Attività GenerateResource](../msbuild/generateresource-task.md)
- [Attività Csc](../msbuild/csc-task.md)
- [Resgen.exe (generatore di file di risorse)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
