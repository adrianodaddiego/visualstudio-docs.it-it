---
title: 'Procedura: Specificare opzioni di strumentazione aggiuntive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4bc6eeb208ab6d80168431f110f0f6169abbc82
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442142"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Procedura: Specificare le opzioni di strumentazione aggiuntive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile instrumentare i binari dall'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] o mediante gli strumenti della riga di comando. Se si instrumenta un file binario dall'IDE, è possibile controllare il volume dei dati raccolti durante la strumentazione specificando opzioni di strumentazione aggiuntive per lo strumento [VSInstr](../profiling/vsinstr.md). Queste opzioni sono disponibili a livello di sessione o di destinazione. Ad esempio, per includere o escludere funzioni specifiche durante il processo di strumentazione, è possibile usare l'opzione di strumentazione aggiuntiva a livello di destinazione.  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
> Ogni probe inserito modifica leggermente il comportamento del programma originale, causando un sovraccarico in fase di analisi. Benché venga sottratta un'approssimazione di questo sovraccarico, si verificano comunque effetti minimi in termini di tempo sulle applicazioni con multithreading. Le opzioni dello strumento [VSInstr](../profiling/vsinstr.md) consentono di controllare la raccolta dei dati durante la profilatura.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Per specificare un'opzione di strumentazione aggiuntiva  
  
1. In **Esplora prestazioni** selezionare **Sessione prestazioni** e quindi fare clic con il pulsante destro del mouse e selezionare **Proprietà**.  
  
2. In **Pagine delle proprietà** fare clic sulle proprietà di **Avanzate**.  
  
3. Digitare le opzioni nella casella **Opzioni di strumentazione aggiuntive**.  
  
     Ad esempio, usare /CONTROL:THREAD per specificare il livello di profilatura. Per un elenco completo di opzioni, vedere [VSInstr](../profiling/vsinstr.md).  
  
4. Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
