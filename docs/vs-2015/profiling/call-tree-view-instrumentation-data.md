---
title: 'Visualizzazione Albero delle chiamate: dati di strumentazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 385d12550692f5f27521afe4dea12e5bdb0aa9d8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54782388"
---
# <a name="call-tree-view---instrumentation-data"></a>Visualizzazione Albero delle chiamate: dati di strumentazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I valori di una funzione nell'albero delle chiamate indicano il tempo per le istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate. I valori percentuali vengono calcolati confrontando il valore delle istanze della funzione con il tempo inclusivo trascorso totale di tutte le funzioni nell'esecuzione della profilatura.  
  
## <a name="general"></a>Generale  
 Le colonne generali identificano la funzione in una riga della visualizzazione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Nome funzione**|Nome della funzione.|  
|**Indirizzo funzione**|Indirizzo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Numero di chiamate**|Numero totale di chiamate effettuate a questa funzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Nome modulo**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome assegnato al processo.|  
|**Sovraccarico temporale per probe esclusivi**|Sovraccarico temporale per questa funzione causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i valori di tempo esclusivo.|  
|**Sovraccarico temporale per probe inclusivi**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|  
|**Livello**|Profondità della funzione nell'albero delle chiamate. Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="elapsed-inclusive-values"></a>Valori di tempo inclusivo trascorso  
 I valori di tempo inclusivo trascorso indicano il tempo nello stack di chiamate delle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate. Il tempo include il tempo dedicato alle funzioni figlio chiamate dalla funzione e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo trascorso**|Tempo inclusivo trascorso totale di tutte le chiamate a questa funzione in questo contesto.|  
|**% tempo inclusivo trascorso**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo trascorso totale di questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="elapsed-exclusive-values"></a>Valori di tempo esclusivo trascorso  
 I valori di tempo esclusivo trascorso indicano il tempo in cui le istanze di una funzione chiamate dalla funzione padre nell'albero delle chiamate hanno eseguito il codice nel corpo della funzione, vale a dire quando la funzione si trovava in cima allo stack di chiamate. Il tempo include il tempo delle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output. Tuttavia, il tempo non include il tempo trascorso nelle funzioni figlio chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo trascorso**|Tempo esclusivo trascorso totale di tutte le chiamate a questa funzione in questo contesto.|  
|**% tempo esclusivo trascorso**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo trascorso totale di questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="application-inclusive-values"></a>Valori di tempo inclusivo applicazione  
 I valori di tempo inclusivo applicazione indicano il tempo in cui le istanze di una funzione chiamate dalla funzione padre nell'albero delle chiamate si trovavano nello stack di chiamate. È escluso il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma è incluso il tempo impiegato nelle funzioni figlio chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo applicazione**|Tempo inclusivo applicazione totale di tutte le chiamate a questa funzione in questo contesto.|  
|**% tempo inclusivo applicazione**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="application-exclusive-values"></a>Valori di tempo esclusivo applicazione  
 I valori di tempo esclusivo applicazione indicano il tempo in cui le istanze di una funzione chiamate dalla funzione padre nell'albero delle chiamate hanno eseguito direttamente il codice nel corpo della funzione, vale a dire quando la funzione si trovava in cima allo stack di chiamate. Il tempo non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output. Inoltre, non include il tempo trascorso nelle funzioni figlio chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo applicazione**|Tempo esclusivo applicazione totale di tutte le chiamate a questa funzione in questo contesto.|  
|**% tempo esclusivo applicazione**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-sampling-data.md)   
 [Visualizzazione Albero delle chiamate: strumentazione](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Albero delle chiamate: campionamento](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
