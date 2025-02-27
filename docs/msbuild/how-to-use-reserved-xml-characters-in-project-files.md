---
title: 'Procedura: Usare caratteri XML riservati nei file di progetto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c79dfa33af5e0e80db682f272c5673856dbbcd8d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840382"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Procedura: Usare caratteri XML riservati nei file di progetto
Quando si creano file di progetto, potrebbe essere necessario usare caratteri XML riservati, ad esempio, nei valori della proprietà o nei valori del parametro di un'attività. Alcuni caratteri riservati tuttavia devono essere sostituiti da un'entità denominata in modo che il file di progetto possa essere analizzato.

## <a name="use-reserved-characters"></a>Usare caratteri riservati
 La tabella seguente descrive i caratteri XML riservati che devono essere sostituiti dall'entità denominata corrispondente in modo che il file di progetto possa essere analizzato.

|Carattere riservato|Entità denominata|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Per usare le virgolette doppie in un file di progetto

- Sostituire le virgolette doppie con l'entità denominata corrispondente, &amp;quot;. Ad esempio, per racchiudere tra virgolette doppie l'elenco di elementi `EXEFile`, digitare:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente le virgolette doppie vengono usate per evidenziare il nome file nel messaggio restituito dal file di progetto.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>"HelloWorldCS"</appname>
    </PropertyGroup>
    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs" />
    </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input
        files of type CSFile -->
        <Csc Sources = "@(CSFile)">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile"/>
        </Csc>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
