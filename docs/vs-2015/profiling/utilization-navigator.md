---
title: Strumento di spostamento di utilizzo | Documenti di Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4aec8cc1a707535e9cf6ae204be0a7ff67ea51d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788322"
---
# <a name="utilization-navigator"></a>Strumento di spostamento di utilizzo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare lo strumento di spostamento di utilizzo nel visualizzatore di concorrenza per selezionare un intervallo di tempo in una traccia. Il visualizzatore di concorrenza mostra l'utilizzo dei core della CPU da parte del processo di destinazione nel tempo. Questo rende più semplice esaminare i modelli di utilizzo della CPU e consente inoltre il confronto tra i dati di utilizzo e i dati in altre visualizzazioni. Lo strumento di spostamento di utilizzo è disponibile nella parte superiore di ogni visualizzazione nel visualizzatore di concorrenza. Nella figura seguente è illustrato lo strumento di spostamento di utilizzo.  
  
 ![Strumento di spostamento di utilizzo con un intervallo di tempo selezionato](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator")  
Strumento di spostamento di utilizzo con un intervallo di tempo selezionato  
  
 Nell'illustrazione, l'intervallo selezionato è definito da un rettangolo rosso, denominato *controllo thumb*.  
  
 Ecco come usare lo strumento di spostamento di utilizzo per modificare l'intervallo di tempo visualizzato:  
  
- È possibile eseguire una panoramica trascinando il controllo thumb verso sinistra o destra. (Tastiera: spostare lo stato attivo sul controllo thumb, quindi premere il tasto freccia SINISTRA o DESTRA).  
  
- È possibile modificare l'estensione dell'intervallo trascinando uno dei quadratini di ridimensionamento. (Tastiera: spostare lo stato attivo sul quadratino di ridimensionamento, quindi premere il tasto freccia DESTRA o SINISTRA).  
  
  Se si modifica l'intervallo usando un altro controllo zoom del visualizzatore di concorrenza, lo strumento di spostamento di utilizzo viene aggiornato per riflettere la modifica.
