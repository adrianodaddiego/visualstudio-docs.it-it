---
title: 'CA1404: Chiamare GetLastError immediatamente dopo P/Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2cd6e3228d67b8dd04cda15549f6b1d172d02916
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546160"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Chiamare GetLastError immediatamente dopo P/Invoke

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Category|Microsoft.Interoperability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Viene eseguita una chiamata per il <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> metodo o Win32 equivalente `GetLastError` (funzione) e la chiamata immediatamente precedente non è una piattaforma metodo invoke.

## <a name="rule-description"></a>Descrizione della regola
 Una piattaforma di richiamare codice non gestito accede a metodo e viene definito tramite il `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributo. In genere, in caso di errore, le funzioni non gestite chiamano Win32 `SetLastError` funzione per impostare un codice di errore associato con l'errore. Il chiamante della funzione non riuscita chiama Win32 `GetLastError` funzione per recuperare il codice di errore e determinare la causa dell'errore. Il codice di errore viene gestito in un singolo thread e viene sovrascritto dalla chiamata successiva a `SetLastError`. Dopo una chiamata a una piattaforma non riuscita invoke (metodo), codice gestito può recuperare il codice di errore chiamando il <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> (metodo). Poiché il codice di errore può essere sovrascritti da chiamate interne da altri metodi della libreria di classi gestita, il `GetLastError` o <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> metodo deve essere chiamato immediatamente dopo la chiamata al metodo PInvoke.

 La regola ignora le chiamate ai seguenti membri gestiti quando si verificano tra la chiamata alla piattaforma di richiamano il metodo e la chiamata a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Questi membri non modificano l'errore codice e sono utili per determinare il successo di alcuni platform invoke chiamate al metodo.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, spostare la chiamata a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> in modo che lo segue immediatamente la chiamata alla piattaforma metodo invoke.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se il codice tra la piattaforma al metodo invoke e <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> chiamata al metodo non può causare in modo esplicito o implicito modificare il codice di errore.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un metodo che viola la regola e un metodo che soddisfa la regola.

 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1060: Spostare i P/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Utilizzare equivalenti gestiti dell'API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)