---
title: Elemento UsingTask (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bf2882120f2e4c27e33b105585ba56261122055d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445648"
---
# <a name="usingtask-element-msbuild"></a>Elemento UsingTask (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Associa l'attività a cui si fa riferimento in un elemento [Task](../msbuild/task-element-msbuild.md) all'assembly che contiene l'implementazione dell'attività.  
  
 \<Project>  
 \<UsingTask>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Description|  
|---------------|-----------------|  
|`AssemblyName`|Sono obbligatori sia l'attributo `AssemblyName` che l'attributo `AssemblyFile`.<br /><br /> Nome dell'assembly da caricare. L'attributo `AssemblyName` accetta assembly con nome sicuro, anche se non è obbligatorio un nome sicuro. L'uso di questo attributo equivale a caricare un assembly usando il metodo <xref:System.Reflection.Assembly.Load%2A> in .NET.<br /><br /> Non è possibile usare questo attributo se viene usato l'attributo `AssemblyFile`.|  
|`AssemblyFile`|È obbligatorio l'attributo `AssemblyName` o l'attributo `AssemblyFile`.<br /><br /> Percorso del file dell'assembly. Questo attributo accetta percorsi completi o percorsi relativi. I percorsi relativi sono relativi alla directory del file di progetto o file di destinazioni in cui viene dichiarato l'elemento `UsingTask`. L'uso di questo attributo equivale a caricare un assembly usando il metodo <xref:System.Reflection.Assembly.LoadFrom%2A> in .NET.<br /><br /> Non è possibile usare questo attributo se viene usato l'attributo `AssemblyName`.|  
|`TaskFactory`|Attributo facoltativo.<br /><br /> Specifica la classe nell'assembly responsabile della generazione di istanze del nome `Task` specificato.  L'utente può specificare anche un elemento figlio `TaskBody` che la factory delle attività riceve e usa per generare l'attività. I contenuti dell'elemento `TaskBody` sono specifici per la factory delle attività.|  
|`TaskName`|Attributo obbligatorio.<br /><br /> Il nome dell'attività a cui fare riferimento da un assembly. In caso di ambiguità, questo attributo deve specificare sempre gli spazi dei nomi completi. In caso di ambiguità, MSBuild sceglie una corrispondenza arbitraria, con potenziali risultati imprevisti.|  
|`Condition`|Attributo facoltativo.<br /><br /> La condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Description|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Il set di parametri visualizzati nell'attività generata dall'elemento `TaskFactory` specificato.|  
|[Task](../msbuild/task-element-msbuild.md)|I dati che vengono passati all'elemento `TaskFactory` per generare un'istanza dell'attività.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Description|  
|-------------|-----------------|  
|[Progetto](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="remarks"></a>Osservazioni  
 È possibile fare riferimento alle variabili di ambiente, alle proprietà della riga di comando e alle proprietà a livello di progetto in qualsiasi punto nell'elemento `UsingTask` se viene visualizzato nel file di progetto in modo esplicito o tramite un file di progetto importato. Per altre informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md) (Attività).  
  
> [!NOTE]
> Le proprietà a livello di progetto non hanno alcun effetto se l'elemento `UsingTask` proviene da uno dei file con estensione tasks registrati a livello globale con il motore MSBuild. Le proprietà a livello di progetto non sono globali per MSBuild.  
  
 In MSBuild 4.0 è possibile caricare gli elementi UsingTask dai file con estensione overridetask.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare l'elemento `UsingTask` con un attributo `AssemblyName`.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare l'elemento `UsingTask` con un attributo `AssemblyFile`.  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
