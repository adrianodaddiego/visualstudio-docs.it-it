---
title: Caratteri speciali di MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7af1f137624c0af1fce02fde524d7fb4178cbad
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65084050"
---
# <a name="msbuild-special-characters"></a>Caratteri speciali di MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] riserva alcuni caratteri per usi speciali in contesti specifici. L'escape di tali caratteri è necessario solo se devono essere usati letteralmente nel contesto in cui sono riservati. Ad esempio, un asterisco ha un significato speciale solo negli attributi `Include` e `Exclude` di una definizione di elemento e nelle chiamate a `CreateItem`. Se un asterisco deve apparire come asterisco in uno di questi contesti, è necessario eseguirne l'escape. In ogni altro contesto, è sufficiente digitare l'asterisco nel punto in cui deve essere visualizzato.

 Per eseguire l'escape di un carattere speciale, usare la sintassi %\<xx>, dove \<xx> rappresenta il valore esadecimale ASCII del carattere. Per altre informazioni, vedere [Procedura: Caratteri di escape speciali in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Caratteri speciali
 Nella tabella seguente sono elencati i caratteri speciali di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]:

|**Carattere**|**ASCII**|**Utilizzo riservato**|
|-------------------|---------------|------------------------|
|%|%25|Riferimento ai metadati|
|$|%24|Riferimento alle proprietà|
|@|%40|Riferimento a elenchi di elementi|
|&#96;|%27|Condizioni e altre espressioni|
|;|%3B|Separatore di elenco|
|?|%3F|Carattere jolly per i nomi di file negli attributi `Include` e `Exclude`|
|*|%2A|Carattere jolly per l'uso nei nomi di file negli attributi `Include` e `Exclude`|

## <a name="see-also"></a>Vedere anche
- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
- [Elementi](../msbuild/msbuild-items.md)