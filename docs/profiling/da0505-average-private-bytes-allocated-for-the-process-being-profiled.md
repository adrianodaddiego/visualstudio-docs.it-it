---
title: 'DA0505: Byte privati medi allocati per il processo sottoposto a profilatura | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 901f568caf7e01c93cde82ccfc66a04df838d491
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935952"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Byte privati medi allocati per il processo sottoposto a profilatura

|||
|-|-|
|ID regola|DA0505|
|Category|Gestione delle risorse|
|Metodo di profilatura|Tutti|
|Messaggio|Dati raccolti a solo scopo informativo. Il contatore di byte privati di processo misura la memoria virtuale allocata dal processo sottoposto a profilatura che non può essere condivisa con altri processi. Il valore restituito corrisponde al valore medio rilevato per tutti gli intervalli di misurazione.|
|Tipo regola|Informazioni|

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.

## <a name="rule-description"></a>Descrizione della regola
 Questo messaggio indica la quantità media di memoria virtuale che il processo ha attualmente allocato in byte (byte privati). I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.

 Per i processi a 32 bit in esecuzione in un computer a 32 bit, il limite superiore della parte privata dello spazio degli indirizzi del processo è di 2 GB. Tramite l'opzione di Boot.ini [/3GB](http://go.microsoft.com/fwlink/?LinkId=177831) i processi a 32 bit possono acquisire fino a 3 GB di memoria virtuale. Un processo a 32 bit in esecuzione su un computer a 64 bit può acquisire fino a 4 GB di memoria virtuale privata.

 Un processo a 64 bit in esecuzione su un computer a 64 bit può acquisire fino a 8 TB di memoria virtuale privata.

 Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.

 Per altre informazioni sugli spazi degli indirizzi del processo, vedere [Virtual Address Space](http://go.microsoft.com/fwlink/?LinkId=177832) (Spazio degli indirizzi virtuali) nella documentazione relativa alla gestione della memoria di Windows.

## <a name="how-to-use-rule-data"></a>Come usare i dati della regola
 Usare il valore indicato per confrontare le prestazioni di versioni o compilazioni diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.