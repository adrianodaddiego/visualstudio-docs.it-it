---
title: .NET compiler Platform (&quot;Roslyn&quot;) estendibilità | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b910d1eb8dcbbe6696c447a7c3a94db533dbbcb3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347908"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET compiler Platform (&quot;Roslyn&quot;) extensibility
Lo scopo fondamentale di .NET Compiler Platform ("Roslyn") è di aprire i compilatori c# e Visual Basic e consentendo di strumenti e agli sviluppatori di condividere i compilatori di informazioni dettagliate sui programmi. Strumenti di analisi codice migliorare la qualità del codice e generatori aiuto nella costruzione dell'applicazione del codice. Man mano che strumenti acquisisce più intelligenti, devono accedere a più e più della conoscenza di codice avanzato che possiedono solo dai compilatori. Anziché essere opachi traduttori (codice sorgente e oggetto codice out), i compilatori Roslyn offrono API che è possibile usare per le attività correlate a codice negli strumenti e applicazioni.

 L'aspetto più interessante è che i compilatori Roslyn, le relative API, esempi e procedure dettagliate e gli strumenti reali partendo da queste API sono tutte completamente open source in [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Visitare il sito di SharePoint Server per altre informazioni e iniziare a usare Roslyn. È possibile trovare collegamenti per ottenere la versione più recente C# e le funzionalità di Visual Basic che è possibile usare come un utente finale, oltre a collegamenti per iniziare a usare come generatore strumento sfruttando APIs Roslyn.

## <a name="see-also"></a>Vedere anche
- [Iniziare con gli analizzatori di Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)