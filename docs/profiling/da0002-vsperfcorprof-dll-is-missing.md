---
title: 'DA0002: VSPerfCorProf.dll mancante | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa263f6ceab515627fd33070517e3393aeec419d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936731"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll mancante

|||
|-|-|
|ID regola|DA0002|
|Category|Uso degli strumenti di profilatura|
|Metodi di profilatura|Profilatura tramite gli strumenti da riga di comando VSPerfCmd e VSPerfASPNETCmd|
|Messaggio|Il file è stato raccolto senza impostare correttamente le variabili di ambiente con *VSPerfCLREnv.cmd*. La risoluzione dei simboli per i file binari gestiti potrebbe non essere effettuata.|
|Tipo regola|Informazioni|

## <a name="cause"></a>Causa
 Il profiler non è in grado di trovare *VSPerfCorProf.dll* durante l'esecuzione della profilatura. Questo avviso si verifica quando vengono usati gli strumenti da riga di comando per la raccolta di dati del profiler senza usare lo strumento *VSPerfCLREnv.cmd* per inizializzare le variabili di ambiente necessarie. L'avviso può essere generato anche se un altro profiler è in esecuzione all'avvio degli strumenti di profilatura.

## <a name="rule-description"></a>Descrizione della regola
 Prima di eseguire la profilatura è necessario impostare variabili di ambiente specifiche per consentire al profiler di risolvere i simboli nei file binari di .NET Framework. Questo avviso indica che lo strumento *VSPerfCLREnv.cmd* non è stato eseguito prima della raccolta dei dati di profilatura. È possibile che i simboli per i file binari gestiti non vengano risolti. Per altre informazioni sull'uso degli strumenti di profilatura dalla riga di comando, vedere [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Quando si profilano applicazioni gestite usando gli strumenti da riga di comando negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], eseguire lo strumento da riga di comando [VSPerfCLREnv](../profiling/vsperfclrenv.md) prima di iniziare la raccolta dei dati.