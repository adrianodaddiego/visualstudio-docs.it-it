---
title: Attività GetFrameworkPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b836a0fef26f34e83f7238ebe4f6c64731b84257
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977669"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath (attività)
Recupera il percorso degli assembly [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

## <a name="task-parameters"></a>Parametri dell'attività
Nella tabella che segue vengono descritti i parametri dell'attività `GetFrameworkPath` .

|Parametro|Description|
|---------------|-----------------|
|`FrameworkVersion11Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 1.1 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion20Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 2.0 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion30Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 3.0 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion35Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 3.5 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion40Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 4.0 del framework, se presenti. In caso contrario restituisce `null`.|
|`Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly del framework più recente, se disponibili. In caso contrario restituisce `null`.|

## <a name="remarks"></a>Osservazioni
Se sono installate diverse versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], l'attività restituisce la versione in cui deve essere eseguito [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] in base alla progettazione.

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio
Nell'esempio seguente viene usata l'attività `GetFrameworkPath` per archiviare il percorso a [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nella proprietà `FrameworkPath`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkPath>
            <Output
                TaskParameter="Path"
                PropertyName="FrameworkPath" />
        </GetFrameworkPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
