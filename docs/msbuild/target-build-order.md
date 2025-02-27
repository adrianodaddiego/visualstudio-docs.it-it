---
title: Ordine di compilazione delle destinazioni | Microsoft Docs
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 502cc7d5f1124ef815455193f00c3f30e77c59a8
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225950"
---
# <a name="target-build-order"></a>Ordine di compilazione delle destinazioni

Le destinazioni devono venire ordinate se l'input per una destinazione dipende dall'output di un'altra destinazione. È possibile usare questi attributi per specificare l'ordine in cui vengono eseguite le destinazioni:

- `InitialTargets`. Questo attributo `Project` specifica le destinazioni che verranno eseguite per prime, anche se vengono specificate destinazioni nella riga di comando o nell'attributo `DefaultTargets`.

- `DefaultTargets`. Questo attributo `Project` specifica le destinazioni che vengono eseguite se non viene specificata una destinazione in modo esplicito nella riga di comando.

- `DependsOnTargets`. Questo attributo `Target` specifica le destinazioni che devono essere eseguite prima di poter eseguire questa destinazione.

- `BeforeTargets` e `AfterTargets`. Questi attributi `Target` specificano che questa destinazione deve essere eseguita prima o dopo le destinazioni specificate (MSBuild 4.0).

  Una destinazione non viene mai eseguita due volte durante una compilazione, anche se ne dipende una destinazione successiva nella compilazione. Dopo che una destinazione è stata eseguita, il contributo alla compilazione è completo.

  Le destinazioni possono avere un attributo `Condition`. Se la condizione specificata restituisce `false`, la destinazione non viene eseguita e non ha effetto sulla compilazione. Per altre informazioni sulle condizioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).

## <a name="initial-targets"></a>Destinazioni iniziali

 L'attributo `InitialTargets` dell'elemento [Project](../msbuild/project-element-msbuild.md) specifica le destinazioni che verranno eseguite per prime, anche se vengono specificate destinazioni nella riga di comando o nell'attributo `DefaultTargets`. Le destinazioni iniziali vengono in genere usate per il controllo degli errori.

 Il valore dell'attributo `InitialTargets` può essere un elenco ordinato di destinazioni delimitate da punto e virgola. L'esempio seguente specifica che viene eseguita la destinazione `Warm` e quindi la destinazione `Eject`.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

 I progetti importati possono avere attributi `InitialTargets` specifici. Tutte le destinazioni iniziali vengono aggregate ed eseguite nell'ordine specificato.

 Per altre informazioni, vedere [Procedura: Specificare quale destinazione compilare per prima](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Destinazioni predefinite

 L'attributo `DefaultTargets` dell'elemento [Project](../msbuild/project-element-msbuild.md) specifica la destinazione o le destinazioni che vengono compilate se non viene specificata una destinazione in modo esplicito in una riga di comando.

 Il valore dell'attributo `DefaultTargets` può essere un elenco ordinato di destinazioni predefinite delimitate da punto e virgola. L'esempio seguente specifica che viene eseguita la destinazione `Clean` e quindi la destinazione `Build`.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

 È possibile eseguire l'override delle destinazioni predefinite usando l'opzione **-target** nella riga di comando. L'esempio seguente specifica che viene eseguita la destinazione `Build` e quindi la destinazione `Report`. Quando si specificano le destinazioni in questo modo, le destinazioni predefinite vengono ignorate.

 `msbuild -target:Build;Report`

 Se sia le destinazioni iniziali che quelle predefinite vengono specificate e se non viene specificata alcuna destinazione della riga di comando, MSBuild esegue prima le destinazioni iniziali e quindi le destinazioni predefinite.

 I progetti importati possono avere attributi `DefaultTargets` specifici. Il primo attributo `DefaultTargets` rilevato determina le destinazioni predefinite che verranno eseguite.

 Per altre informazioni, vedere [Procedura: Specificare quale destinazione compilare per prima](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>Prima destinazione

 Se non sono presenti destinazioni iniziali, destinazioni predefinite o destinazioni della riga di comando, MSBuild esegue la prima destinazione rilevata nel file di progetto o nei file di progetto importati.

## <a name="target-dependencies"></a>Dipendenze tra destinazioni

 Le destinazioni possono descrivere relazioni di dipendenza reciproche. L'attributo `DependsOnTargets` indica che una destinazione dipende da altre destinazioni. Ad esempio,

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

 Il codice precedente indica a MSBuild che la destinazione `Serve` dipende dalla destinazione `Chop` e dalla destinazione `Cook`. MSBuild esegue la destinazione `Chop` e quindi esegue la destinazione `Cook` prima di eseguire la destinazione `Serve`.

## <a name="beforetargets-and-aftertargets"></a>BeforeTargets e AfterTargets

 In MSBuild 4.0 è possibile specificare l'ordine delle destinazioni usando gli attributi `BeforeTargets` e `AfterTargets`.

 Considerare lo script seguente.

```xml
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Compile">
        <Message Text="Compiling" />
    </Target>
    <Target Name="Link">
        <Message Text="Linking" />
    </Target>
</Project>
```

 Per creare una destinazione `Optimize` intermedia da eseguire dopo la destinazione `Compile`, ma prima della destinazione `Link`, aggiungere la destinazione seguente nell'elemento `Project`.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Determinare l'ordine di compilazione delle destinazioni

 MSBuild determina l'ordine di compilazione delle destinazioni, come segue:

1. Vengono eseguite le destinazioni `InitialTargets`.

2. Vengono eseguite le destinazioni specificate nella riga di comando dall'opzione **-target**. Se non si specifica alcuna destinazione nella riga di comando, vengono eseguite le destinazioni `DefaultTargets`. Se nessuna delle due destinazioni è presente, viene eseguita la prima destinazione rilevata.

3. Viene valutato l'attributo `Condition` della destinazione. Se l'attributo `Condition` è presente e restituisce `false`, la destinazione non viene eseguita e non ha effetto sulla compilazione.

    Le altre destinazioni che elencano la destinazione condizionale in `BeforeTargets` o `AfterTargets` vengono ancora eseguite nell'ordine prescritto.

4. Prima che la destinazione venga eseguita o ignorata, vengono eseguite le relative destinazioni `DependsOnTargets`, a meno che l'attributo `Condition` non sia applicato alla destinazione e restituisca `false`.

   > [!NOTE]
   > Una destinazione viene considerata ignorata se non viene eseguita perché i relativi elementi di output sono aggiornati (vedere le informazioni relative alla [compilazione incrementale](../msbuild/incremental-builds.md)). Questa verifica viene eseguita subito prima dell'esecuzione delle attività all'interno della destinazione e non influisce sull'ordine di esecuzione delle destinazioni.

5. Prima che la destinazione venga eseguita o ignorata, vengono eseguite le eventuali altre destinazioni che la elencano in un attributo `BeforeTargets`.

6. Prima che la destinazione venga eseguita, ne vengono confrontati gli attributi `Inputs` e `Outputs`. Se MSBuild determina che sono presenti file di output scaduti rispetto al file o ai file di input corrispondenti, MSBuild esegue la destinazione. In caso contrario, MSBuild ignora la destinazione.

7. Dopo che la destinazione viene eseguita o ignorata, vengono eseguite le eventuali altre destinazioni che la elencano in un attributo `AfterTargets`.

## <a name="see-also"></a>Vedere anche

- [Destinazioni](../msbuild/msbuild-targets.md)
