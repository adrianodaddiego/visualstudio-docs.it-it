---
title: 'CA2122: Non esporre in modo indiretto metodi con richieste di collegamento'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8239b27cd92f66ae8f74ddb1accd95535bf56f93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542337"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Non esporre in modo indiretto metodi con richieste di collegamento

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un membro pubblico o protetto ha un [richieste di collegamento](/dotnet/framework/misc/link-demands) e viene chiamato da un membro che non esegue controlli di sicurezza.

## <a name="rule-description"></a>Descrizione della regola
 Una richiesta di collegamento controlla esclusivamente le autorizzazioni del chiamante immediato. Se un membro `X` non effettua richieste alcuna sicurezza dei relativi chiamanti e chiamate di codice protetto da una richiesta di collegamento, un chiamante senza l'autorizzazione necessaria possa usare `X` per accedere al membro protetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Aggiungere una protezione [dati e modellazione](/dotnet/framework/data/index) o richiesta di collegamento per il membro in modo che non fornisca accesso non protetto non è più al membro protetto dalla richiesta di collegamento.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che il codice non concede i chiamanti accesso a operazioni o risorse che possono essere usate in modo distruttivo.

## <a name="example-1"></a>Esempio 1
 Gli esempi seguenti mostrano una libreria che viola la regola e un'applicazione che illustra i punti deboli della libreria. La libreria di esempio fornisce due metodi che insieme violano la regola. Il `EnvironmentSetting` metodo è protetto da una richiesta di collegamento per l'accesso illimitato alle variabili di ambiente. Il `DomainInformation` metodo non rende SecurityDemand dei chiamanti prima di chiamare `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Esempio 2
 La seguente applicazione chiama il membro della libreria non protetto.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Questo esempio produce il seguente output:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Richieste di collegamento](/dotnet/framework/misc/link-demands)
- [Dati e modellazione](/dotnet/framework/data/index)