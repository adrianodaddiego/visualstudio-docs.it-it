---
title: Attività FindInList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c2f6c5f14f6eff818a265e097f02e2bc76c7372
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996647"
---
# <a name="findinlist-task"></a>FindInList (attività)
Trova in un elenco specificato un elemento con un itemspec corrispondente.

## <a name="parameters"></a>Parametri
 Nella tabella che segue vengono descritti i parametri dell'attività [FindInList](../msbuild/findinlist-task.md).

|Parametro|Description|
|---------------|-----------------|
|`CaseSensitive`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, la ricerca fa distinzione tra maiuscole e minuscole, in caso contrario non la fa. Il valore predefinito è `true`.|
|`FindLastMatch`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, restituisce l'ultima corrispondenza, in caso contrario restituisce la prima corrispondenza. Il valore predefinito è `false`.|
|`ItemFound`|Parametro di output di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Il primo elemento corrispondente trovato nell'elenco, se presente.|
|`ItemSpecToFind`|Parametro `String` obbligatorio.<br /><br /> L'argomento itemspec da cercare.|
|`List`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> L'elenco in cui eseguire la ricerca dell'argomento itemspec.|
|`MatchFileNameOnly`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene confrontata solo la parte del nome file dell'itemspec, in caso contrario l'intero itemspec. Il valore predefinito è `true`.|

## <a name="remarks"></a>Osservazioni
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)