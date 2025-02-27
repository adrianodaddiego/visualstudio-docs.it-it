---
title: Risoluzione dei problemi relativi all'analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: erickson-doug
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 047866f958ebfe6de20d5f7760b72eaab4135ef1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62551472"
---
# <a name="troubleshooting-code-analysis-issues"></a>Risoluzione dei problemi di analisi codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'argomento contiene informazioni sulla risoluzione dei problemi seguenti relativi all'analisi del codice di Visual Studio.  
  
- [Le modifiche apportate a un set di regole di Visual Studio 2010 non si riflettono nelle versioni precedenti di Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
## <a name="ChildRuleSetChangesInPreviousVersions"></a> Le modifiche apportate a un set di regole di Visual Studio 2010 non si riflettono nelle versioni precedenti di Visual Studio  
 Quando si crea un set di regole in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] che contiene un set di regole figlio, è possibile che una modifica al set di regole figlio non venga applicata nelle esecuzioni dell'analisi del codice nei computer che usano una versione precedente di Visual Studio. Per risolvere questo problema, è necessario forzare una riscrittura del set di regole padre, ovvero del set di regole che contiene il set di regole figlio.  
  
1. Aprire il set di regole padre in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
2. Apportare una modifica, ad esempio aggiungere o eliminare una regola, e salvare il set di regole.  
  
3. Riaprire il set di regole, annullare la modifica e salvare nuovamente il set di regole.  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi della qualità delle applicazioni](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Uso di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
