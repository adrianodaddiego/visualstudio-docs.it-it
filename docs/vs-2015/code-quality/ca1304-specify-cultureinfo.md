---
title: 'CA1304: Specificare CultureInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f5d4333508d6faec3df81f860f5b5b2b526be324
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692090"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Specificare CultureInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo o costruttore chiama un membro che ha un overload che accetta un <xref:System.Globalization.CultureInfo?displayProperty=fullName> parametro e il metodo o costruttore non chiama l'overload che accetta il <xref:System.Globalization.CultureInfo> parametro. Questa regola ignora le chiamate ai metodi seguenti:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
 Quando un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider?displayProperty=fullName> oggetto non viene specificato, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali. Inoltre, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] membri scelgono le impostazioni cultura predefinite e la formattazione basato su presupposti che potrebbero non essere corretti per il codice. Per verificare che il codice funzioni come previsto per gli scenari, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle linee guida seguenti:

- Se il valore verrà visualizzato all'utente, usare le impostazioni cultura correnti. Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Se il valore verrà archiviato e utilizzato dal software, vale a dire, mantenuto in un file o database, usare le impostazioni cultura invarianti. Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Se non si conosce la destinazione del valore, dispone al consumer di dati o provider di specificare le impostazioni cultura.

  Si noti che <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> viene usato solo per recuperare le risorse localizzate con un'istanza del <xref:System.Resources.ResourceManager?displayProperty=fullName> classe.

  Anche se il comportamento predefinito del membro di overload è adatto alle proprie esigenze, è preferibile chiamare in modo esplicito l'overload specifico delle impostazioni cultura in modo che quest'ultima è autodocumentato e più facilmente gestibili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, usare l'overload che accetta un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> e specificare l'argomento in base alle linee guida elencate in precedenza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si è certi che il provider di impostazioni cultura o il formato predefinito è la scelta corretta e la gestibilità del codice non è una priorità di sviluppo importanti.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `BadMethod` fa sì che due delle violazioni di questa regola. `GoodMethod` corregge la prima violazione passando le impostazioni cultura invarianti per System.String.Compare e corregge la violazione secondo passando le impostazioni cultura correnti <xref:System.String.ToLower%2A> perché `string3` viene visualizzato all'utente.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente mostra l'effetto delle impostazioni cultura correnti sul valore predefinito <xref:System.IFormatProvider> sarà selezionata per il <xref:System.DateTime> tipo.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Questo esempio produce il seguente output:

 **6/4/1900 12:15:12 PM**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Regole correlate
 [CA1305: Specificare IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Vedere anche
 [NIB: Utilizzo della classe CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
