---
title: Status | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25f452dcb473abf87d8992f36f5326973937e85e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967872"
---
# <a name="status"></a>Status
L'opzione *Status* di **VSPerfCmd.exe** visualizza informazioni sullo stato del profiler e di eventuali processi in corso di profilatura.

 L'opzione **Status** deve essere l'unica opzione specificata nella riga di comando. Prima di poter visualizzare qualsiasi stato è necessario inizializzare il profiler con l'opzione *Start* di **VSPerfCmd.exe**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Parametri
 nessuno

## <a name="remarks"></a>Osservazioni
 L'opzione **Status** consente di visualizzare le informazioni sullo stato seguenti per il profiler.

 **Nome file di output** Percorso e nome del file di dati del profiler corrente.

 **Modalità di raccolta** SAMPLE o TRACE

 **Numero massimo di processi** Numero massimo di processi di cui è possibile eseguire la profilatura contemporaneamente e numero di processi attivi.

 **Numero massimo di thread** Numero massimo di thread di cui è possibile eseguire la profilatura contemporaneamente.

 **Numero di buffer** Numero di buffer di memoria dedicati alla scrittura dei dati di profilatura.

 **Dimensione dei buffer** Dimensione di un buffer di memoria in byte.

 L'opzione **Status** visualizza le informazioni sullo stato seguenti per ogni processo in corso di profilatura.

 **Processo**  Nome del processo di cui è stata eseguita la profilatura.

 **ID processo** Identificatore di sistema del processo.

 **Num. thread** Numero di thread in esecuzione.

 **Conteggio Start/Stop** Conteggio del profiler interno principale per controllare la raccolta dei dati per questo processo. Il conteggio deve essere uguale a uno per raccogliere i dati. Il conteggio Start/Stop può essere modificato dalle API del profiler e dalle opzioni di VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** e **ThreadOff**.

 **Conteggio Suspend/Resume** Conteggio del profiler interno principale per controllare la raccolta dei dati per questo processo. Il conteggio deve essere minore o uguale a zero per raccogliere i dati. Il conteggio **Suspend/Resume** può essere modificato solo dalle API del profiler.

 **Utenti con diritti di accesso al monitor** Elenca i nomi degli utenti che hanno accesso al profiler. È possibile concedere l'accesso ad altri utenti tramite l'opzione **Admin** di VSPerfCmd.exe.

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)