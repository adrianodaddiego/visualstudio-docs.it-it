---
title: 'CA1903: Utilizzare solo API dal framework di destinazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 146563dfa358367e7c22f8ad37564b85d64eaf1d
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647155"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Usare solo API della versione di .NET Framework di destinazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [CA1903: Utilizzare solo API dal framework di destinazione](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).  
  
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Category|Microsoft.Portability|  
|Modifica importante|Rilievo - quando viene attivato in base alla firma di un membro visibile esternamente o un tipo.<br /><br /> Non sostanziale - Quando viene attivato nel corpo di un metodo.|  
  
## <a name="cause"></a>Causa  
 Un membro o tipo sta utilizzando un membro o un tipo che è stato introdotto in un service pack che non è stata incluso con framework di destinazione del progetto.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Tipi e membri nuovi erano inclusi in .NET Framework 2.0 Service Pack 1 e 2, .NET Framework 3.0 Service Pack 1 e 2 e .NET Framework 3.5 Service Pack 1. Progetti destinati a versioni principali di .NET Framework involontariamente possono richiedere le dipendenze su queste nuove API. Per evitare questa dipendenza, questa regola viene attivata in caso di utilizzo di eventuali nuovi membri e tipi che non sono stati inclusi per impostazione predefinita con framework di destinazione del progetto.  
  
 **Framework di destinazione e le dipendenze di Service Pack**  
  
|||  
|-|-|  
|Quando è il framework di destinazione|Viene attivato in caso di utilizzo di membri introdotti in|  
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N/D|  
  
 Per modificare il framework di destinazione del progetto, vedere [come destinazione una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per rimuovere la dipendenza dal service pack, rimuovere tutti gli utilizzi del nuovo membro o tipo. Se si tratta di una dipendenza intenzionale, eliminare l'avviso o disattivare questa regola.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola se non si tratta di una dipendenza da intenzionale del service pack specificato. In questo caso, l'applicazione potrebbe non riuscire per l'esecuzione nei sistemi senza questo service pack installato. Eliminare l'avviso o disattivare questa regola se fosse una dipendenza intenzionale.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata una classe che utilizza il tipo di valore DateTimeOffset che è disponibile solo in .NET 2.0 Service Pack 1. Questo esempio richiede che .NET Framework 2.0 è stato selezionato nell'elenco a discesa Framework di destinazione nelle proprietà del progetto.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente consente di correggere la violazione descritta in precedenza, sostituendo gli utilizzi del tipo di DateTimeOffset con il tipo DateTime.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di portabilità](../code-quality/portability-warnings.md)   
 [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
