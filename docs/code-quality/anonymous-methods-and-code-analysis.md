---
title: Avvisi dell'analisi del codice di metodo anonimo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a10c5baaed3a98e44d581b6ddb8d6e3a1883d079
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62560235"
---
# <a name="anonymous-methods-and-code-analysis"></a>Metodi anonimi e analisi del codice

Un' *metodo anonimo* è un metodo che non ha nome. Metodi anonimi vengono spesso usati per passare un blocco di codice come un parametro del delegato. Questo articolo illustra come l'analisi del codice gestisce gli avvisi e metriche per i metodi anonimi.

## <a name="anonymous-methods-declared-in-a-member"></a>Metodi anonimi dichiarati In un membro

Gli avvisi e metriche per un metodo anonimo che viene dichiarato in un membro, ad esempio un metodo o una funzione di accesso, associati con il membro che dichiara il metodo. Non sono associati al membro che chiama il metodo.

Ad esempio, nella classe seguente, gli avvisi che si trovano nella dichiarazione della **anonymousMethod** deve essere generato in base **Method1** e non **Method2**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass
    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End Sub
    Sub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>Metodi anonimi inline

Gli avvisi e metriche per un metodo anonimo che viene dichiarato come un'assegnazione di inline a un campo sono associate al costruttore. Se il campo viene dichiarato come `static` (`Shared` in Visual Basic), le metriche e avvisi associati con il costruttore della classe. In caso contrario, sono associate con il costruttore di istanza.

Ad esempio, nella classe seguente, gli avvisi che si trovano nella dichiarazione della **anonymousMethod1** verrà generato in base al costruttore predefinito generato in modo implicito dei **classe**. Gli avvisi che si trovano nella **anonymousMethod2** verranno applicate in base al costruttore di classe generato in modo implicito.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass
    Dim anonymousMethod1 As ADelegate = Function(ByVal value As Integer) value > 5
    Shared anonymousMethod2 As ADelegate = Function(ByVal value As Integer) value > 5

    Sub Method1()
        anonymousMethod1(10)
        anonymousMethod2(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

Una classe può contenere un metodo anonimo inline che assegna un valore a un campo che contiene più costruttori. In questo caso, le metriche e avvisi associati con tutti i costruttori, a meno che tale costruttore concatenato a un altro costruttore nella stessa classe.

Ad esempio, nella classe seguente, gli avvisi che si trovano nella dichiarazione della **anonymousMethod** deve essere generato in base **Class (int)** e **Class (String)**, ma non rispetto **Class ()**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass

    Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5

    SubNew()
        New(CStr(Nothing))
    End Sub

    Sub New(ByVal a As Integer)
    End Sub

    Sub New(ByVal a As String)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

Gli avvisi vengono generati per i costruttori perché il compilatore genera un metodo univoco per ogni costruttore che non è collegato a un altro costruttore. A causa di questo comportamento, qualsiasi violazione che si verifica nelle **anonymousMethod** deve essere eliminato separatamente. Ciò significa anche che se un nuovo costruttore viene introdotta, gli avvisi che sono stati eliminati in precedenza contro **Class (int)** e **Class (String)** deve anche essere eliminati in base al nuovo costruttore.

È possibile risolvere questo problema in uno dei due modi:

- Dichiarare **anonymousMethod** in un costruttore comune che concatenati tutti i costruttori.
- Dichiarare **anonymousMethod** in un metodo di inizializzazione che viene chiamato da tutti i costruttori.

## <a name="see-also"></a>Vedere anche

- [Analisi della qualità del codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)