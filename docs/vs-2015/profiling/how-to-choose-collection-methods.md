---
title: 'Procedura: Scegliere un metodo di raccolta | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ff14ce88f2032b998214ed11310a15550321dc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088444"
---
# <a name="how-to-choose-collection-methods"></a>Procedura: Scegliere i metodi di raccolta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supportano tre metodi di raccolta dei dati relativi alle prestazioni: campionamento, strumentazione e concorrenza. È anche possibile usare il metodo di campionamento o di strumentazione per raccogliere dati di durata e allocazione di memoria .NET.  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  È possibile usare la proprietà **Metodo** della sessione di prestazioni per specificare il metodo di raccolta più appropriato per un'applicazione. Il metodo di raccolta può essere impostato dalla Creazione guidata sessione di prestazioni, da Esplora prestazioni o dalle pagine delle proprietà di una sessione di prestazioni. Se si usano gli strumenti della riga di comando, vedere [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md) per altre informazioni.  
  
## <a name="performance-wizard"></a>Creazione guidata sessione di prestazioni  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Per selezionare un metodo di raccolta usando la Creazione guidata sessione di prestazioni  
  
- Nella prima pagina della procedura guidata selezionare una delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Campionamento CPU**|Consente di raccogliere le statistiche dell'applicazione utili per l'analisi iniziale e per l'analisi dei problemi relativi all'uso della CPU.|  
|**Strumentazione**|Consente di raccogliere i dati di intervallo dettagliati utili per l'analisi mirata e per l'analisi dei problemi relativi alle prestazioni di input/output.|  
|**Allocazione della memoria .NET**|Consente di raccogliere i dati relativi all'allocazione della memoria [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] usando il metodo di profilatura del campionamento.|  
|**Concorrenza**|Consente di raccogliere i dati numerici sui conflitti di risorse.|  
  
## <a name="performance-explorer"></a>Esplora prestazioni  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>Per selezionare un metodo di raccolta usando Esplora prestazioni  
  
1. Nella barra degli strumenti di **Esplora prestazioni** fare clic sulla freccia accanto all'elenco a discesa **Metodo**.  
  
2. Fare clic sul metodo di raccolta preferito.  
  
## <a name="performance-session-property-pages"></a>Pagine delle proprietà della sessione di prestazioni  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Per selezionare il metodo di campionamento o di strumentazione usando le proprietà della sessione di prestazioni  
  
1. In **Esplora prestazioni** selezionare la sessione di prestazioni.  
  
     L'estensione del nome di un file di sessione di prestazioni è psess.  
  
2. Fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.  
  
3. In **Pagine delle proprietà** fare clic su **Generale**.  
  
4. Fare clic sul metodo di raccolta preferito.  
  
    - Per informazioni sulle altre opzioni disponibili quando si raccolgono i dati di campionamento, vedere [Raccolta di statistiche sulle prestazioni tramite il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md).  
  
    - Per informazioni sulle altre opzioni disponibili quando si raccolgono i dati di campionamento, vedere [Raccolta di dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Per selezionare la raccolta dei dati di memoria .NET usando le proprietà della sessione di prestazioni  
  
1. In **Esplora prestazioni** selezionare la sessione di prestazioni.  
  
     L'estensione del nome di un file di sessione di prestazioni è psess.  
  
2. Fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.  
  
3. In **Pagine delle proprietà** fare clic su **Generale**.  
  
4. Fare clic su **Campionamento** o **Strumentazione**.  
  
5. Fare clic su **Raccogliere le informazioni sull'allocazione dell'oggetto .NET** per raccogliere le dimensioni e il numero delle allocazioni degli oggetti [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
6. (Facoltativo) Fare clic su **Raccogliere anche le informazioni sulla durata dell'oggetto .NET** per raccogliere dati sulle generazioni di Garbage Collection in cui è stata recuperata la memoria dell'oggetto.  
  
     Per informazioni sulle altre opzioni disponibili quando si raccolgono i dati di memoria .NET, vedere [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Per selezionare la raccolta dei dati di concorrenza usando le proprietà della sessione di prestazioni  
  
1. In **Esplora prestazioni**fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.  
  
2. In **Pagine delle proprietà** fare clic su **Generale**.  
  
3. Fare clic su **Concorrenza**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configuring Performance Sessions](../profiling/configuring-performance-sessions.md)  (Configurazione di sessioni di prestazioni)  
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)   
 [Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)
