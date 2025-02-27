---
title: WinCounter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9424eb099516761866ec459888ff830fcf56a28b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54791564"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'opzione **WinCounter** specifica un contatore delle prestazioni di Windows o di un'applicazione per la raccolta di dati a intervalli prestabiliti durante l'esecuzione della profilatura. I contatori delle prestazioni di Windows e dell'applicazione sono elencati come contrassegni nel file di dati di profilatura. È possibile specificare più contatori delle prestazioni da raccogliere in opzioni separate.  
  
 Per impostazione predefinita, i dati dei contatori vengono raccolti ogni 500 millisecondi. Usare l'opzione **AutoMark** per specificare un intervallo di raccolta diverso.  
  
 È possibile usare una sola opzione **AutoMark**. Se vengono specificate più opzioni **AutoMark**, viene usata l'ultima.  
  
 L'opzione **WinCounter** può essere usata solo con l'opzione **Start**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Path`  
 Contatore delle prestazioni di Windows nel formato del percorso del contatore PDH.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **WinCounter** può essere usata solo con l'opzione **Start**.  
  
 **Start:** `Method`  
 L'opzione **Start** inizializza il profiler sul metodo di profilatura specificato.  
  
## <a name="exclusive-options"></a>Opzioni esclusive  
 L'opzione **AutoMark** può essere usata solo con l'opzione **WinCounter**.  
  
 **AutoMark:** `Milliseconds`  
 Specifica il numero di millisecondi tra le raccolte di dati dei contatori delle prestazioni di Windows.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene impostata la raccolta dei dati di due contatori delle prestazioni di Windows a intervalli di 1000 millisecondi.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)
