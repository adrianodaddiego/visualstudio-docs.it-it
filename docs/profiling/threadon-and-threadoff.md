---
title: ThreadOn e ThreadOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2516ff5597151e65276b0fcb2bef5bb81c929cd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965232"
---
# <a name="threadon-and-threadoff"></a>ThreadOn e ThreadOff
In *VSPerfCmd.exe* i sottocomandi **ThreadOff** e **ThreadOn** sono disponibili solo nelle sessioni di profilatura della riga di comando che usano il metodo di strumentazione. **ThreadOff** e **ThreadOn** sospendono e riprendono la profilatura per il thread specificato. **ThreadOff** arresta la profilatura del thread e **ThreadOn** avvia la profilatura del thread.

 Nella maggior parte dei casi si specifica **ThreadOn** o **ThreadOff** come unica opzione in una riga di comando di *VSPerfCmd.exe*, ma questi sottocomandi possono anche essere combinati con i sottocomandi **GlobalOn**, **GlobalOff**, **ProcessOn** e **ProcessOff**.

 I sottocomandi **ThreadOn** e **ThreadOff** interagiscono con i sottocomandi **GlobalOn** e **GlobalOff** che controllano la raccolta dei dati per tutti i processi in una sessione di profilatura da riga di comando e i sottocomandi **ProcessOn** e **ProcessOff** che controllano la raccolta dei dati per un processo specificato.

 I sottocomandi **ThreadOff** e **ThreadOn** influenzano anche il conteggio Start/Stop per i thread, gestito dalle funzioni API del profiler.

- **ThreadOff** imposta immediatamente il conteggio Start/Stop per i thread su 0 e sospende quindi la profilatura.

- **ThreadOn** imposta immediatamente il conteggio Start/Stop per i thread su 1 e riprende quindi la profilatura.

  Per altre informazioni, vedere [API per strumenti di profilatura](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Parametri
 `TID` Identificatore integer del thread da avviare o arrestare.

## <a name="valid-options"></a>Opzioni valide
 **ThreadOn** e **ThreadOff** possono essere specificati su righe di comando che contengono anche i sottocomandi seguenti.

 **Start:** `Method` Inizializza la sessione di profilatura da riga di comando e imposta il metodo di profilatura specificato.

 **GlobalOff**&#124;**GlobalOn** Arresta o avvia la profilatura per tutti i processi in una sessione di profilatura da riga di comando.

 {**ProcessOff**&#124;**ProcessOn**}**:**`TID` Arresta o avvia la profilatura per il processo specificato.

## <a name="example"></a>Esempio
 In questo esempio, il sottocomando **ThreadOff** viene usato per arrestare la raccolta dei dati di profilatura, in modo da raccogliere solo i dati di avvio dell'applicazione.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the thread after startup.
VSPerfCmd.exe /ThreadOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)