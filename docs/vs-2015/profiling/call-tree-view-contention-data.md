---
title: 'Visualizzazione Albero delle chiamate: dati sui conflitti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d12f1a2343018f05f0e741222b844c562b50f5e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048385"
---
# <a name="call-tree-view---contention-data"></a>Visualizzazione Albero delle chiamate: dati su conflitti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione Albero delle chiamate consente di visualizzare i percorsi di esecuzione della funzione usati nell'applicazione profilata. La radice dell'albero è il punto di ingresso nell'applicazione o nel componente. Ogni nodo della funzione elenca tutte le funzioni che ha chiamato, il numero di volte per cui la funzione è stata bloccata e il tempo per il quale la funzione è stata bloccata perché in conflitto per una risorsa con altri thread o processi.  
  
 I valori nella visualizzazione Albero delle chiamate sono relativi alle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate. I valori percentuali vengono calcolati confrontando il valore dell'istanza della funzione e il numero totale di conflitti nell'esecuzione della profilatura.  
  
## <a name="highlighting-the-execution-hot-path"></a>Evidenziare il percorso critico di esecuzione  
 Nella visualizzazione Albero delle chiamate è possibile espandere ed evidenziare il percorso di esecuzione del processo o della funzione che ha determinato il maggior numero di conflitti.  
  
- Per visualizzare il percorso più attivo fare clic con il pulsante destro del mouse sul processo o sulla funzione e quindi scegliere **Espandi percorso critico**.  
  
## <a name="setting-the-call-tree-root-node"></a>Impostare il nodo radice dell'albero delle chiamate  
 Ogni processo nell'esecuzione della profilatura viene visualizzato come nodo radice. Per impostare il nodo di inizio della visualizzazione Albero delle chiamate, fare clic con il pulsante destro del mouse sul nodo che si vuole impostare come nodo iniziale e fare clic su **Imposta radice**.  
  
 Quando si imposta il nodo radice si eliminano dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato. Per reimpostare il nodo radice sul nodo originale, fare clic con il pulsante destro del mouse nella visualizzazione Albero delle chiamate e fare clic su **Reimposta radice**.  
  
|Colonna|Description|  
|------------|-----------------|  
|**Tempo blocco esclusivo**|Tempo per il quale l'esecuzione delle istanze della funzione in questo percorso di esecuzione è stata bloccata nell'esecuzione della profilatura. Il tempo non include il tempo di blocco delle funzioni figlio chiamate dalla funzione.|  
|**% tempo blocco esclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco esclusivo per questa funzione in questo percorso di esecuzione.|  
|**Conflitti esclusivi**|Numero di conflitti che si sono verificati nelle istanze di questa funzione in questo percorso di esecuzione. Il numero non include i conflitti delle funzioni figlio chiamate dalla funzione.|  
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresenta conflitti esclusivi delle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate.|  
|**Indirizzo funzione**|Indirizzo della funzione.|  
|**Nome funzione**|Nome completo della funzione.|  
|**Tempo blocco inclusivo**|Tempo totale per il quale l'esecuzione delle istanze della funzione in questo percorso di esecuzione è stata bloccata nell'esecuzione della profilatura. Il tempo include il tempo di blocco delle funzioni figlio chiamate dalla funzione.|  
|**% tempo blocco inclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco inclusivo per le istanze di questa funzione in questo percorso di esecuzione.|  
|**Conflitti inclusivi**|Numero totale di conflitti che hanno bloccato istanze di questa funzione in questo percorso di esecuzione. Il numero include i conflitti delle funzioni figlio chiamate dalla funzione.|  
|**% conflitti inclusivi**|Percentuale del totale di conflitti nell'esecuzione della profilatura corrispondente ai conflitti inclusivi delle istanze di questa funzione in questo percorso di esecuzione.|  
|**Livello**|Livello della funzione nell'albero delle chiamate. Solo nei rapporti della riga di comando di VSReport. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Nome modulo**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md)   
 [Visualizzazione Albero delle chiamate: strumentazione](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Albero delle chiamate: campionamento](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-instrumentation-data.md)   
 [Visualizzazione albero delle chiamate](../profiling/call-tree-view-sampling-data.md)
