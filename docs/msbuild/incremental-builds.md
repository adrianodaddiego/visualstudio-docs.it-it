---
title: Compilazioni incrementali | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 820d8b4837e2b7ae3f93a742ca8abe5962cd1893
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007029"
---
# <a name="incremental-builds"></a>Compilazioni incrementali

Le compilazioni incrementali sono compilazioni ottimizzate in modo da non eseguire le destinazioni con file di output aggiornati rispetto ai file di input corrispondenti. Un elemento di destinazione può avere sia un attributo `Inputs`, che indica quali elementi la destinazione accetta come input, sia un attributo `Outputs`, che indica quali elementi vengono generati come output. MSBuild tenta di trovare un mapping uno a uno tra i valori di questi attributi. Se esiste un mapping uno a uno, MSBuild confronta il timestamp di ogni elemento di input con il timestamp dell'elemento di output corrispondente. I file di output per cui non esiste un mapping uno a uno vengono confrontati con tutti i file di input. Un elemento viene considerato aggiornato se il relativo file di output è stato creato nello stesso momento dei relativi file di input o è più recente.

Se tutti gli elementi di output sono aggiornati, MSBuild ignora la destinazione. Questa *compilazione incrementale* della destinazione può migliorare significativamente la velocità di compilazione. Se solo alcuni file sono aggiornati, MSBuild esegue la destinazione, ma ignora gli elementi aggiornati e in questo modo tutti gli elementi vengono aggiornati. Questo processo è noto come *compilazione incrementale parziale*.

I mapping uno a uno in genere vengono prodotti dalle trasformazioni degli elementi. Per altre informazioni, vedere [Trasformazioni](../msbuild/msbuild-transforms.md).

 Considerare la destinazione seguente.

```xml
<Target Name="Backup" Inputs="@(Compile)"
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">
    <Copy SourceFiles="@(Compile)" DestinationFiles=
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />
</Target>
```

Il set di file rappresentato dal tipo dell'elemento `Compile` viene copiato in una directory di backup. I file di backup hanno estensione *bak*. Se i file rappresentati dal tipo dell'elemento `Compile` o i file di backup corrispondenti non vengono eliminati o modificati dopo l'esecuzione della destinazione di backup, la destinazione di backup viene ignorata nelle compilazioni successive.

## <a name="output-inference"></a>Inferenza di output

MSBuild confronta li attributi `Inputs` e `Outputs` di una destinazione per determinare se la destinazione deve essere eseguita. In teoria, il set di file che esiste dopo il completamento di una compilazione incrementale deve rimanere invariato a prescindere dall'esecuzione delle destinazioni associate. Poiché le proprietà e gli elementi che vengono creati o modificati dalle attività possono influire sulla compilazione, MSBuild deve dedurne i valori anche se la destinazione che influisce su di essi viene ignorata. Questo processo è noto come *inferenza di output*.

Esistono tre casi:

- La destinazione ha un attributo `Condition` che restituisce `false`. In questo caso, la destinazione non viene eseguita e non ha alcun effetto sulla compilazione.

- La destinazione ha output non aggiornati e viene eseguita per consentirne l'aggiornamento.

- La destinazione non ha output non aggiornati e viene ignorata. MSBuild valuta la destinazione e apporta modifiche a elementi e proprietà come se la destinazione fosse stata eseguita.

Per supportare la compilazione incrementale, le attività devono garantire che il valore dell'attributo `TaskParameter` di qualsiasi elemento `Output` sia uguale a un parametro di input dell'attività. Ecco alcuni esempi:

```xml
<CreateProperty Value="123">
    <Output PropertyName="Easy" TaskParameter="Value" />
</CreateProperty>
```

Questo codice crea la proprietà Easy, il cui valore è "123", indipendentemente dal fatto che la destinazione venga eseguita o ignorata.

A partire da MSBuild 3.5, l'inferenza di output viene eseguita automaticamente sui gruppi di proprietà ed elementi in una destinazione. Le attività `CreateItem` non sono richieste in una destinazione e devono essere evitate. Le attività `CreateProperty` devono inoltre essere usate in una destinazione solo per determinare se la destinazione è stata eseguita.

Prima di MSBuild 3.5 è possibile usare l'attività [CreateItem](../msbuild/createitem-task.md).

## <a name="determine-whether-a-target-has-been-run"></a>Determinare se una destinazione è stata eseguita

A causa dell'inferenza di output, è necessario aggiungere un'attività `CreateProperty` a una destinazione per esaminare le proprietà e gli elementi in modo da poter determinare se la destinazione è stata eseguita. Aggiungere l'attività `CreateProperty` alla destinazione e assegnare alla stessa un elemento `Output` il cui `TaskParameter` è "ValueSetByTask".

```xml
<CreateProperty Value="true">
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />
</CreateProperty>
```

Questo codice crea la proprietà CompileRan a cui viene assegnato il valore `true`, ma solo se la destinazione viene eseguita. Se la destinazione viene ignorata, la proprietà CompileRan non viene creata.

## <a name="see-also"></a>Vedere anche
- [Destinazioni](../msbuild/msbuild-targets.md)