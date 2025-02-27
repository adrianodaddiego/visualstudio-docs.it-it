---
title: 'CA1049: I tipi proprietari di risorse native devono essere disposable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 34a7b8352da8e8e8a3b92f36fe1d636633e3a8c9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686123"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: I tipi delle risorse native devono essere disposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Fa riferimento a un tipo di un <xref:System.IntPtr?displayProperty=fullName> campo, una <xref:System.UIntPtr?displayProperty=fullName> campo o una <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> campo, ma non implementa <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola presuppone che <xref:System.IntPtr>, <xref:System.UIntPtr>, e <xref:System.Runtime.InteropServices.HandleRef> campi archiviano i puntatori alle risorse non gestite. I tipi che allocano risorse non gestite devono implementare <xref:System.IDisposable> per consentire ai chiamanti di rilasciare quelle risorse su richiesta e ridurre la durata degli oggetti che contengono le risorse.

 Il modello di progettazione consigliato per pulire le risorse non gestite è fornire sia impliciti che un utile strumento per rendere disponibili tali risorse tramite il <xref:System.Object.Finalize%2A?displayProperty=fullName> (metodo) e il <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo, rispettivamente. Il garbage collector chiama la <xref:System.Object.Finalize%2A> metodo di un oggetto in corrispondenza di un determinato momento dopo l'oggetto viene determinato come non è più raggiungibile. Dopo aver <xref:System.Object.Finalize%2A> viene chiamato, un'ulteriore operazione di garbage collection è necessaria per liberare l'oggetto. Il <xref:System.IDisposable.Dispose%2A> metodo consente al chiamante rilasciare in modo esplicito le risorse su richiesta, prima di quando sarebbe rilasciate al garbage collector. Dopo che pulisce le risorse non gestite, <xref:System.IDisposable.Dispose%2A> deve chiamare il <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> metodo per consentire al garbage collector di sapere che <xref:System.Object.Finalize%2A> non è più necessario chiamare; Ciò elimina la necessità di ulteriori garbage collection e consente di abbreviare la durata dell'oggetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il tipo non fa riferimento a una risorsa non gestita. In caso contrario, non eliminare un avviso da questa regola poiché non si implementa <xref:System.IDisposable> può rendere le risorse non gestite disponibili o sottoutilizzate.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che implementa <xref:System.IDisposable> per pulire una risorsa non gestita.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2115: Chiamare GC. KeepAlive durante l'utilizzo di risorse native](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Chiamare GC. SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: I tipi proprietari di campi eliminabili devono essere eliminabili](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Vedere anche
  [Criterio Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
