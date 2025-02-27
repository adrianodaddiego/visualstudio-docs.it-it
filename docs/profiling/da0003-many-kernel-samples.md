---
title: 'DA0003: Numero elevato di campioni del kernel | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1cd12b4944da36e480aa44f312b44133c657365f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970680"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Numero elevato di campioni del kernel

|||
|-|-|
|ID regola|DA0003|
|Category|Uso degli strumenti di profilatura|
|Metodi di profilatura|Campionamento|
|Messaggio|È presente un numero elevato di campioni in modalità kernel. Questa circostanza potrebbe indicare un volume elevato di attività I/O oppure un rapporto elevato di cambi di contesto. Si consiglia di profilare nuovamente l'applicazione utilizzando la modalità strumentazione.|
|Tipo regola|Informazioni|

## <a name="cause"></a>Causa
 Una parte significativa degli esempi di stack di chiamate raccolti per l'applicazione era in esecuzione in modalità kernel. Si consiglia di profilare l'applicazione usando un altro metodo di profilatura.

## <a name="rule-description"></a>Descrizione della regola
 In Windows è possibile eseguire il codice in modalità kernel oppure in modalità utente. La modalità kernel è chiamata anche modalità privilegiata. Solo il codice di sistema di basso livello, ad esempio un driver di dispositivo, viene eseguito in modalità kernel. Un'applicazione in modalità utente può passare alla modalità kernel per eseguire operazioni di I/O, per attendere primitive di sincronizzazione di thread o processi o per eseguire chiamate di sistema.

 Il campionamento è più efficace quando si profilano applicazioni che per la maggior parte del tempo eseguono operazioni in modalità utente. Il numero di campioni raccolti durante l'esecuzione dell'applicazione in modalità kernel può indicare operazioni di I/O frequenti o può indicare che si stanno verificando cambi di contesto. Nessuna di queste operazioni può essere analizzata usando il metodo di campionamento. Se è stato acquisito un numero eccessivo di campioni in modalità kernel, è possibile che i dati di campionamento non contengano un numero sufficiente di campioni in modalità utente per essere statisticamente significativi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Si consiglia di profilare nuovamente l'applicazione usando una delle opzioni seguenti:

- Profilare usando il metodo di strumentazione.

- Aumentare la frequenza di campionamento per tentare di raccogliere più campioni in modalità utente.