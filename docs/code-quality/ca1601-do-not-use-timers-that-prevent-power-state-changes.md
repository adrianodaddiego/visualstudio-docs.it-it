---
title: 'CA1601: Non usare i timer che impediscono le modifiche allo stato di potenza'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc6db6dff5ee4c4e4d387399dbf79277046d6c02
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797454"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Non usare i timer che impediscono le modifiche allo stato di potenza

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Category|Microsoft.Mobility|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un timer ha un intervallo impostato su si verificano più di una volta al secondo.

## <a name="rule-description"></a>Descrizione della regola
 Non eseguire il polling più spesso di una volta al secondo o utilizzare i timer che si verificano più frequentemente una volta al secondo. Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Impostare gli intervalli di timer in presenti meno di una volta al secondo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Questa regola deve essere eliminata solo se è richiesta l'attivazione di più di una volta al secondo il timer e le considerazioni sulla mobilità può essere ignorati.