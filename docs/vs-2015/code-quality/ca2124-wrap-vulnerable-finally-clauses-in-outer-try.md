---
title: 'CA2124: Incapsulamento vulnerabile delle clausole finally in esterno try | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 755cce18afcad3fde621fb5a960cc780906afe51
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385988"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Nelle versioni 1.0 e 1.1 del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], un metodo pubblico o protetto contiene un `try` / `catch` / `finally` blocco. Il `finally` blocco viene visualizzato per reimpostare lo stato di sicurezza e non è racchiuso un `finally` blocco.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola individua `try` / `finally` blocchi nel codice destinato alle versioni 1.0 e 1.1 del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] che potrebbero essere vulnerabili ai filtri eccezioni dannoso presenti nello stack di chiamate. Se vengono eseguite operazioni, ad esempio la rappresentazione nel blocco try e viene generata un'eccezione, il filtro può essere eseguito prima il `finally` blocco. Nell'esempio della rappresentazione, ciò significa che il filtro viene eseguito come utente rappresentato. I filtri sono attualmente è possibile implementare solo in Visual Basic.

> [!WARNING]
> **Nota** nelle versioni 2.0 e versioni successive del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], il runtime protegge automaticamente una `try` / `catch` /  `finally` bloccare dai filtri eccezioni dannoso, se si verifica la reimpostazione direttamente all'interno del metodo che contiene il blocco di eccezioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Posizionare il wrapping `try` / `finally` in un blocco try esterno. Vedere il secondo esempio che segue. In tal modo il `finally` da eseguire prima del codice di filtro.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="pseudo-code-example"></a>Esempio di pseudocodice

### <a name="description"></a>Descrizione
 Lo pseudocodice seguente illustra il modello rilevato da questa regola.

### <a name="code"></a>Codice

```
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

## <a name="example"></a>Esempio
 Il pseudo-codice seguente viene illustrato il modello che è possibile usare per proteggere il codice e soddisfano questa regola.

```
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```
