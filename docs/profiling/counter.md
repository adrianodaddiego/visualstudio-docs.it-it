---
title: Counter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e21e364d05641089fb7400fbbfa9873510037d62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553084"
---
# <a name="counter"></a>Counter
L'opzione **Counter** raccoglie i dati dai contatori delle prestazioni del processore (hardware).

- Quando si usa il metodo di profilatura basato sul campionamento, l'opzione **Counter** consente di specificare il contatore delle prestazioni del chip e il numero di eventi del contatore da usare come intervallo di campionamento. Quando si usa il campionamento, è possibile specificare un solo contatore.

- Quando si usa il metodo di profilatura basato sulla strumentazione, il numero di eventi del contatore che si verificano nell'intervallo tra l'evento di raccolta corrente e quello precedente vengono elencati come campi separati nei report del profiler. Quando si usa la strumentazione, è possibile specificare più opzioni **Counter**.

  Ogni tipo di processore dispone del proprio set di contatori delle prestazioni dell'hardware. Il profiler definisce un set di contatori delle prestazioni generici comuni a quasi tutti i processori. Per elencare nel computer i contatori generici e quelli specifici del processore, usare il comando **QueryCounters** di VSPerfCmd.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parametri
 `Name` Nome del contatore. Usare l'opzione **/QueryCounters** di VSPerfCmd.exe per elencare i nomi dei contatori disponibili nel computer.

 `Reload` Numero di eventi dei contatori nell'intervallo di campionamento. Non usare con il metodo basato sulla strumentazione.

 `FriendlyName` (Facoltativo) Stringa da usare al posto di `Name` nelle intestazioni di colonna dei report e delle visualizzazioni del profiler.

## <a name="required-options"></a>Opzioni obbligatorie
 L'opzione Counter può essere usata solo con una delle opzioni seguenti:

 **Start:** `Trace` Inizializza il profiler per l'uso del metodo di strumentazione.

 **Launch:** `AppName` Avvia l'applicazione specificata e il profiler. Il profiler deve essere inizializzato per l'uso del metodo basato sul campionamento.

 **Attach:** `PID` Avvia il profiler e lo connette al processo specificato dall'ID processo. Il profiler deve essere inizializzato per l'uso del metodo basato sul campionamento.

## <a name="example"></a>Esempio
 Nell'esempio del metodo basato sul campionamento viene illustrato come campionare un'applicazione ogni 1000 occorrenze del contatore del profiler generico NonHaltedCycles.

 Nell'esempio del metodo basato sulla strumentazione viene illustrato come inizializzare il profiler per la raccolta di eventi del contatore L2InstructionFetches. Il nome del contatore L2InstructionFetches è specifico del processore.

```cmd
; Sample Method Example
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"

;INSTRUMENTATION METHOD EXAMPLE
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"
```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)