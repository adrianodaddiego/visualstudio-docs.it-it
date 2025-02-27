---
title: "DA0006: Eseguire l'override di Equals() per i tipi di valore | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e30894ec98dd1db4de0b724082467a681a0fa696
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970691"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Eseguire l'override di Equals() per i tipi di valore

|||
|-|-|
|ID regola|DA0006|
|Category|Uso di .NET Framework|
|Metodi di profilatura|Campionamento|
|Messaggio|Eseguire l'override di Equals e dell'operatore di uguaglianza sui tipi di valore.|
|Tipo di messaggio|Avviso|

## <a name="cause"></a>Causa
 Le chiamate al metodo Equals o agli operatori di uguaglianza di un tipo valore pubblico rappresentano una percentuale significativa dei dati di profilatura. Considerare la possibilità di implementare un metodo più efficiente.

## <a name="rule-description"></a>Descrizione della regola
 Per i tipi di valore, l'implementazione ereditata di Equals usa la libreria <xref:System.Reflection> e confronta il contenuto di tutti i campi del tipo. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti confrontino o ordinino le istanze oppure le usino come chiavi di tabelle hash, il tipo di valore deve implementare Equals. Se il linguaggio di programmazione in uso supporta l'overload degli operatori, è necessario specificare anche un'implementazione degli operatori di uguaglianza e disuguaglianza.

 Per altre informazioni su come eseguire l'override del metodo Equals e degli operatori di uguaglianza, vedere [Linee guida per l'implementazione del metodo Equals e dell'operatore di uguaglianza (==)](http://go.microsoft.com/fwlink/?LinkId=177818).

## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso
 Per un esempio di implementazione di Equals e degli operatori di uguaglianza, vedere la regola di analisi del codice [CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)