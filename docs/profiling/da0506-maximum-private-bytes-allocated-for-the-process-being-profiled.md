---
title: 'DA0506: Byte privati massimi allocati per il processo sottoposto a profilatura | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd3ae6b45d910723f04cf8b828cbce62f8fdc1a7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935906"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Byte privati massimi allocati per il processo sottoposto a profilatura

|||
|-|-|
|ID regola|DA0506|
|Category|Monitoraggio risorse|
|Metodo di profilatura|Tutti|
|Messaggio|Dati raccolti a solo scopo informativo. Il contatore di byte privati di processo misura la memoria virtuale allocata dal processo sottoposto a profilatura che non può essere condivisa con altri processi. Il valore restituito corrisponde al valore massimo osservato per tutti gli intervalli di misurazione.|
|Tipo regola|Informazioni|

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.

## <a name="rule-description"></a>Descrizione della regola
 Questo messaggio indica la quantità massima di memoria virtuale che il processo ha attualmente allocato in byte (byte privati). I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.

 Per i processi a 32 bit in esecuzione in un computer a 32 bit, il limite superiore della parte privata dello spazio degli indirizzi del processo è di 2 GB. Tramite l'opzione di Boot.ini [/3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) i processi a 3 bit possono acquisire fino a 32 GB di memoria virtuale. Un processo a 32 bit in esecuzione su un computer a 64 bit può acquisire fino a 4 GB di memoria virtuale privata.

 Un processo a 64 bit in esecuzione su un computer a 64 bit può acquisire fino a 8 TB di memoria virtuale privata.

 Il valore indicato è il valore massimo fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.

 Per altre informazioni sugli spazi degli indirizzi del processo, vedere [Virtual Address Space](http://go.microsoft.com/fwlink/?LinkId=177832) (Spazio degli indirizzi virtuali) nella documentazione relativa alla gestione della memoria di Windows.

## <a name="how-to-use-rule-data"></a>Come usare i dati della regola
 Usare il valore indicato per confrontare le prestazioni di versioni o compilazioni diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.

 Un valore massimo di byte privati di processo quasi al limite architettonico in base al quale vengono definite le dimensioni massime di uno spazio degli indirizzi di processo può determinare eccezioni di memoria insufficiente. Per altre informazioni, vedere [Investigating Memory Issues](http://go.microsoft.com/fwlink/?LinkID=177833) (Analisi dei problemi di memoria) in MSDN Magazine.