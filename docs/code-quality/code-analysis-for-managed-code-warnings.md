---
title: Analisi del codice per gli avvisi del codice gestito
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d6238919db971492ffd226708209b97bceceb9e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540768"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Analisi del codice per gli avvisi del codice gestito
Lo strumento di analisi del codice gestito fornisce avvisi che indicano le violazioni delle regole nelle librerie del codice gestito. Gli avvisi sono organizzati in aree di regole, ad esempio progettazione, localizzazione, prestazioni e sicurezza. Ogni avviso indica una violazione di una regola di analisi del codice gestito. Questa sezione fornisce descrizioni dettagliate ed esempi per ogni avviso di analisi del codice gestito.

 La tabella seguente mostra il tipo di informazioni fornite per ogni avviso.

|Elemento|Descrizione|
|----------|-----------------|
|Tipo|TypeName per la regola.|
|CheckId|Identificatore univoco per la regola. CheckId e Category vengono usati per l'eliminazione di un avviso nell'origine.|
|Category|Categoria dell'avviso.|
|Modifica importante|Indica se la correzione di una violazione della regola è una modifica importante. Per modifica importante si intende che un assembly che presenta una dipendenza dalla destinazione che ha causato la violazione non verrà ricompilato con la nuova versione corretta o potrebbe non riuscire in fase di esecuzione a causa della modifica. Quando sono disponibili più correzioni e almeno una di esse è una modifica importante e una non la è, vengono specificati sia "Importante" che "Non importante".|
|Causa|Codice gestito specifico che ha fatto sì che la regola generasse un avviso.|
|Descrizione|Descrive i problemi alla base dell'avviso.|
|Come correggere le violazioni|Spiega come modificare il codice sorgente per soddisfare la regola e impedire la generazione di un avviso.|
|Esclusione di avvisi|Descrive quando è possibile eliminare un avviso da questa regola.|
|Codice di esempio|Esempi che violano la regola ed esempi corretti che soddisfano la regola.|
|Avvisi correlati|Avvisi correlati.|

## <a name="in-this-section"></a>In questa sezione

|||
|-|-|
|[Avvisi generati da CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Elenchi di tutti gli avvisi generati da CheckId|
|[Avvisi di crittografia](../code-quality/cryptography-warnings.md)|Avvisi che supportano applicazioni e librerie più sicure attraverso l'uso corretto della crittografia.|
|[Avvisi di progettazione](../code-quality/design-warnings.md)|Avvisi che supportano la progettazione corretta delle librerie come specificato dalle linee guida di progettazione di .NET Framework.|
|[Avvisi di globalizzazione](../code-quality/globalization-warnings.md)|Avvisi che supportano applicazioni e librerie internazionalizzate.|
|[Avvisi di interoperabilità](../code-quality/interoperability-warnings.md)|Avvisi che supportano l'interazione con i client COM.|
|[Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)|Avvisi che supportano la manutenzione di applicazioni e librerie.|
|[Mobility Warnings](../code-quality/mobility-warnings.md)|Avvisi che supportano l'utilizzo efficiente dell'energia.|
|[Avvisi di denominazione](../code-quality/naming-warnings.md)|Avvisi che supportano la conformità alle convenzioni di denominazione delle linee guida di progettazione di .NET Framework.|
|[Avvisi di prestazioni](../code-quality/performance-warnings.md)|Avvisi che supportano applicazioni e librerie ad alte prestazioni.|
|[Portability Warnings](../code-quality/portability-warnings.md)|Avvisi che supportano la portabilità tra piattaforme diverse.|
|[Avvisi di affidabilità](../code-quality/reliability-warnings.md)|Avvisi che supportano l'affidabilità di applicazioni e librerie, ad esempio il corretto utilizzo di memoria e thread.|
|[Avvisi di sicurezza](../code-quality/security-warnings.md)|Avvisi che supportano applicazioni e librerie più sicure.|
|[Avvisi di utilizzo](../code-quality/usage-warnings.md)|Avvisi che supportano l'utilizzo appropriato di .NET Framework.|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|Errori che si verificano se i criteri di analisi del codice non sono soddisfatti al momento dell'archiviazione.|