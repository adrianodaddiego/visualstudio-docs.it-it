---
title: Attività UnregisterAssembly | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ef7ef7f4ec930b8aa338a8be33c4009b3009b20
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666148"
---
# <a name="unregisterassembly-task"></a>Attività UnregisterAssembly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Annulla la registrazione degli assembly specificati ai fini dell'interoperabilità COM. Esegue operazioni inverse rispetto all'[attività RegisterAssembly](../msbuild/registerassembly-task.md).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `UnregisterAssembly` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`Assemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly di cui annullare la registrazione.|  
|`AssemblyListFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Contiene informazioni sullo stato tra l'attività `RegisterAssembly` e l'attività `UnregisterAssembly`. Questo impedisce all'attività di tentare l'annullamento della registrazione di un assembly che non è riuscita nell'attività `RegisterAssembly`.<br /><br /> Se questo parametro è specificato, i parametri `Assemblies` e `TypeLibFiles` verranno ignorati.|  
|`TypeLibFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Annulla la registrazione della libreria dei tipi indicata dall'assembly specificato. **Nota:** questo parametro è necessario solo se il nome dei file della libreria dei tipi non corrisponde a quello dell'assembly.|  
  
## <a name="remarks"></a>Osservazioni  
 Per la corretta esecuzione dell'attività non è necessario che l'assembly sia presente. Se si prova ad annullare la registrazione di un assembly inesistente, l'attività verrà comunque eseguita correttamente e verrà visualizzato un avviso. Questa situazione si verifica perché l'attività ha la funzione di rimuovere la registrazione dell'assembly dal Registro di sistema. Se l'assembly non esiste, non si trova nel Registro di sistema e l'attività viene pertanto eseguita correttamente.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension>, che a sua volta eredita dalla classe <xref:System.MarshalByRefObject>. La classe `MarshalByRefObject` offre la stessa funzionalità della classe <xref:Microsoft.Build.Utilities.Task>, ma è possibile crearne un'istanza nel relativo dominio dell'applicazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente l'attività `UnregisterAssembly` viene usata per annullare la registrazione dell'assembly eventualmente presente nel percorso specificato dalle proprietà `OutputPath` e `FileName`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività RegisterAssembly](../msbuild/registerassembly-task.md)   
 [Tasks](../msbuild/msbuild-tasks.md)  (Attività)  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
