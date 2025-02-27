---
title: Creazione di file dei dati di profilatura portabili tramite la riga di comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d343392c9e554c5e51325964949cd3ea13237b8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434282"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Creazione di file dei dati di profilatura portabili tramite la riga di comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per semplificare la condivisione dei dati di profilatura è possibile usare lo strumento della riga di comando [VSPerfReport](../profiling/vsperfreport.md) per incorporare i simboli di un'esecuzione della profilatura nel file con estensione vsp.  
  
 È anche possibile creare un file di dati di profilatura preanalizzati (con estensione vsps), più piccolo e più facile da caricare nell'IDE.  
  
> [!NOTE]
> Verificare che i file di simboli (con estensione pdb) siano disponibili per **VSPerfReport**. Per altre informazioni, vedere [Procedura: Specificare i percorsi di File di simboli dalla riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
> Per altre informazioni sul percorso di **VSReport**, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Non è possibile filtrare i dati di profilatura di un file con estensione vsps.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Per incorporare i simboli per un'esecuzione della profilatura in un file di dati di profilatura (con estensione vsp)  
  
- In una finestra del prompt dei comandi, digitare il comando seguente:  
  
   \<percorso><strong>VSPerfReport \<</strong>file VSP> **/PackSymbols**  
  
   Per impostazione predefinita il file con estensione vsps è denominato con il nome base del file con estensione vsp. È possibile specificare un nome alternativo con l'opzione **Output**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Per creare un file di riepilogo dati di profilatura  
  
- In una finestra del prompt dei comandi, digitare il comando seguente:  
  
   \<percorso><strong>VSPerfReport \<</strong>file VSP> **/SummaryFile** [**/Output:**\<nome file>]  
  
   Per impostazione predefinita il file con estensione vsps è denominato con il nome base del file con estensione vsp. È possibile specificare un nome alternativo con l'opzione **Output**.
