---
title: 'DA0008: Numero ridotto di campioni raccolti | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b33193f30edd19ef18ead5cf15f2e41d352f4d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936618"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Numero ridotto di campioni raccolti

|||
|-|-|
|ID regola|DA0008|
|Category|Uso degli strumenti di profilatura|
|Metodo di profilatura|Campionamento|
|Messaggio|È stato raccolto un numero ridotto di campioni. Si consiglia di eseguire il campionamento più a lungo o di aumentare la frequenza di campionamento per ottenere risultati più significativi.|
|Tipo regola|Informazioni|

## <a name="cause"></a>Causa
 Durante l'esecuzione della profilatura sono stati raccolti solo alcuni campioni.

## <a name="rule-description"></a>Descrizione della regola
 Quando viene usato il metodo di campionamento, è necessario raccogliere un numero di campioni statisticamente significativo per assicurarsi che i dati siano rappresentativi dell'effettivo comportamento del programma. Per ridurre al minimo gli errori di campionamento, provare a raccogliere almeno 1000 campioni di comportamento dell'esecuzione delle istruzioni del programma. Se non si raccoglie un numero sufficiente di campioni è possibile che l'analisi dei dati di profilatura porti a conclusioni fuorvianti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 È consigliabile profilare un'esecuzione più lunga dell'applicazione o usare una frequenza di campionamento più elevata per ottenere risultati significativi a livello statistico. Per informazioni su come modificare la frequenza di campionamento nell'IDE di Visual Studio, vedere [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md). Per altre informazioni sulla modifica della frequenza di campionamento quando si usa la riga di comando degli strumenti di profilatura, vedere [Timer](../profiling/timer.md) nel riferimento di [VSPerfCmd](../profiling/vsperfcmd.md).