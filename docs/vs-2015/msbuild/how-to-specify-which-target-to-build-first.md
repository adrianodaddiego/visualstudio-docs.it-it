---
title: 'Procedura: Specificare quale destinazione compilare per prima | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d7d47746aed2e663eb1fa25e3bb9ca2c6bed2c9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076419"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Procedura: Specificare quale destinazione compilare per prima
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un file di progetto può contenere uno o più elementi `Target` che definiscono come viene compilato il progetto. Il motore [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) compila il primo progetto che trova e le eventuali dipendenze, a meno che il file di progetto contenga un attributo `DefaultTargets` o `InitialTargets` oppure venga specificata una destinazione nella riga di comando usando l'opzione **/target**.  
  
## <a name="using-the-initialtargets-attribute"></a>Uso dell'attributo InitialTargets  
 L'attributo `InitialTargets` dell'elemento `Project` specifica una destinazione che verrà eseguita per prima, anche se vengono specificate destinazioni nella riga di comando o nell'attributo `DefaultTargets`.  
  
#### <a name="to-specify-one-initial-target"></a>Per specificare una destinazione iniziale  
  
- Specificare la destinazione predefinita nell'attributo `InitialTargets` dell'elemento `Project`. Ad esempio:  
  
   `<Project InitialTargets="Clean">`  
  
  È possibile specificare più di una destinazione iniziale nell'attributo `InitialTargets` elencando le destinazioni in ordine e usando il punto e virgola per separare ogni destinazione. Le destinazioni nell'elenco verranno eseguite in sequenza.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Per specificare più di una destinazione iniziale  
  
- Elencare le destinazioni iniziali, separate da punto e virgola, nell'attributo `InitialTargets` dell'elemento `Project`. Ad esempio, per eseguire la destinazione `Clean` e poi la destinazione `Compile`, digitare:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Uso dell'attributo DefaultTargets  
 L'attributo `DefaultTargets` dell'elemento `Project` specifica la destinazione o le destinazioni che vengono compilate se non viene specificata una destinazione in modo esplicito nella riga di comando. Se vengono specificate destinazioni sia nell'attributo `InitialTargets` che nell'attributo `DefaultTargets` e nessuna destinazione viene specificata nella riga di comando, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] esegue le destinazioni specificate nell'attributo `InitialTargets` seguito dalle destinazioni specificate nell'attributo `DefaultTargets`.  
  
#### <a name="to-specify-one-default-target"></a>Per specificare una destinazione predefinita  
  
- Specificare la destinazione predefinita nell'attributo `DefaultTargets` dell'elemento `Project`. Ad esempio:  
  
   `<Project DefaultTargets="Compile">`  
  
  È possibile specificare più di una destinazione predefinita nell'attributo `DefaultTargets` elencando le destinazioni in ordine e usando il punto e virgola per separare ogni destinazione. Le destinazioni nell'elenco verranno eseguite in sequenza.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Per specificare più di una destinazione predefinita  
  
- Elencare le destinazioni predefinite, separate da punto e virgola, nell'attributo `DefaultTargets` dell'elemento `Project`. Ad esempio, per eseguire la destinazione `Clean` e poi la destinazione `Compile`, digitare:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Uso dell'opzione /target  
 Se nel file di progetto non viene definita una destinazione predefinita o se non si vuole usare la destinazione predefinita, è possibile usare l'opzione della riga di comando **/target** per specificare un'altra destinazione. Viene eseguita la destinazione o le destinazioni specificate con l'opzione **/target** invece delle destinazioni specificate dall'attributo `DefaultTargets`. Le destinazioni specificate nell'attributo `InitialTargets` vengono eseguite sempre per prime.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Per usare per prima una destinazione diversa da quella predefinita  
  
- Specificare la destinazione da usare per prima tramite l'opzione della riga di comando **/target**. Ad esempio:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Per usare per prime più destinazioni diverse da quelle predefinite  
  
- Elencare le destinazioni, separate da punto e virgola o virgola, usando l'opzione della riga di comando **/target**. Ad esempio:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Vedere anche
  [MSBuild](msbuild.md)  
 [Destinazioni](../msbuild/msbuild-targets.md)   
 [Procedura: Pulire una compilazione](../msbuild/how-to-clean-a-build.md)
