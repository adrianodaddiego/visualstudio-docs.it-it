---
title: Elemento Task (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6683aac3c5a4314df6fde3d72dd9085b6608d8a3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669575"
---
# <a name="task-element-msbuild"></a>Elemento Task (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Crea ed esegue un'istanza di un'attività di [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Il nome dell'elemento viene determinato dal nome dell'attività da creare.  
  
 \<Project>  
 \<Target>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Condition`|Attributo facoltativo. Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Attributo facoltativo. Può contenere uno dei valori seguenti:<br /><br /> -   **WarnAndContinue** o **true**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento [Target](../msbuild/target-element-msbuild.md) e della compilazione continua e tutti gli errori delle attività vengono considerati avvisi.<br />-   **ErrorAndContinue**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento `Target` e della compilazione continua e tutti gli errori delle attività vengono considerati errori.<br />-   **ErrorAndStop** o **false** (impostazione predefinita). Quando un'attività ha esito negativo, le attività rimanenti nell'elemento `Target` e la compilazione non vengono eseguite e l'intero elemento `Target` e la compilazione vengono considerati come non riusciti.<br /><br /> Le versioni di .NET Framework precedenti alla 4.5 supportano solo i valori `true` e `false`.<br /><br /> Per altre informazioni, vedere [Procedura: Ignorare gli errori nelle attività](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Obbligatorio se la classe dell'attività contiene una o più proprietà contrassegnate con l'attributo `[Required]`.<br /><br /> Un parametro per l'attività definita dall'utente che contiene il valore del parametro come valore. L'elemento `Task` può includere qualsiasi numero di parametri, con ogni attributo mappato a una proprietà .NET nella classe dell'attività.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Output](../msbuild/output-element-msbuild.md)|Archivia gli output dell'attività nel file di progetto. Possono esistere zero o più elementi `Output` in un'attività.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Destinazione](../msbuild/target-element-msbuild.md)|Elemento contenitore per le attività [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
  
## <a name="remarks"></a>Note  
 Un elemento `Task` in un file di progetto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] crea un'istanza di un'attività, ne imposta le proprietà e la esegue. L'elemento `Output` archivia i parametri di output nelle proprietà o negli elementi da usare in altri punti nel file di progetto.  
  
 In presenza di elementi [OnError](../msbuild/onerror-element-msbuild.md) nell'elemento padre `Target` di un'attività, questi verranno comunque valutati se l'attività ha esito negativo e `ContinueOnError` ha il valore `false`. Per altre informazioni sulle attività, vedere [Attività](../msbuild/msbuild-tasks.md).  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente crea un'istanza della classe dell'[attività Csc](../msbuild/csc-task.md), imposta sei proprietà ed esegue l'attività. Dopo l'esecuzione, il valore della proprietà `OutputAssembly` dell'oggetto viene inserito in un elenco di elementi denominato `FinalAssemblyName`.  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
