---
title: 'DA0012: Uso elevato della reflection | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33617b71c8ba13c459df8bcf29fb8a51cf948299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936457"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Utilizzo elevato della reflection

|||
|-|-|
|ID regola|DA0012|
|Category|Uso di .NET Framework|
|Metodi di profilatura|Campionamento|
|Messaggio|È possibile che si stia usando la reflection in modo eccessivo. L'operazione è dispendiosa.|
|Tipo regola|Avviso|

## <a name="cause"></a>Causa
 Le chiamate ai metodi System.Reflection, ad esempio InvokeMember e GetMember, o ai metodi Type, ad esempio MemberInvoke, costituiscono una percentuale significativa dei dati di profilatura. Ove possibile considerare la possibilità di sostituire questi metodi con associazione anticipata ai metodi di assembly dipendenti.

## <a name="rule-description"></a>Descrizione della regola
 La reflection è una funzionalità flessibile di .NET Framework che può essere usata per eseguire l'associazione tardiva dell'applicazione a un assembly di runtime dipendente oppure per creare ed eseguire dinamicamente nuovi tipi durante il runtime. Tuttavia, queste tecniche possono ridurre le prestazioni se vengono usate frequentemente o chiamate in cicli ridotti.

 Per altre informazioni, vedere la sezione [Reflection and Late Binding](http://go.microsoft.com/fwlink/?LinkId=177826) (Reflection e associazione tardiva) in Chapter 5 - Improving Managed Code Performance (Capitolo 5 - Miglioramento delle prestazioni del codice gestito) nel volume Improving .NET Application Performance and Scalability (Miglioramento delle prestazioni e della scalabilità delle applicazioni .NET) della libreria Microsoft Patterns and Practices in MSDN.

## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilatura. Esaminare le funzioni chiamanti del metodo System.Type o System.Reflection per trovare le sezioni del programma che fanno maggior uso delle API Reflection di .NET. Evitare di usare metodi che restituiscono metadati. Quando le prestazioni dell'applicazione sono di importanza fondamentale potrebbe essere necessario evitare l'uso dell'associazione tardiva e la creazione dinamica di tipi durante il runtime.