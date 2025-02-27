---
title: 'Procedura: Dividere una classe in classi parziali (Progettazione classi)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e1426b1ad9799984f7b14604a1d8b685e9ce8813
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615404"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Procedura: Dividere una classe in classi parziali in Progettazione classi

È possibile usare la parola chiave `partial` (`Partial` in Visual Basic) per dividere la dichiarazione di una classe o struttura in più dichiarazioni. È possibile usare tutte le dichiarazioni parziali che si desidera.

Le dichiarazioni possono essere in uno o più file di origine. Tutte le dichiarazioni devono trovarsi nello stesso assembly e nello stesso spazio dei nomi.

Le classi parziali sono utili in varie situazioni. In un progetto di grandi dimensioni, ad esempio, la separazione di una classe in più file consente a più programmatori di lavorare sul progetto contemporaneamente. Quando si lavora con il codice generato da Visual Studio, è possibile modificare la classe senza dover ricreare il file di origine. (Il codice wrapper per Windows Form e per servizi web è un esempio di codice generato da Visual Studio.) È possibile creare codice che usa classi generate automaticamente senza dover modificare il file creato da Visual Studio.

Esistono due tipi di metodi parziali, chiamati dichiarazione e implementazione in C# e Visual Basic.

**Progettazione classi** supporta classi e metodi parziali. La forma del tipo nel diagramma classi fa riferimento a una singola posizione di dichiarazione per la classe parziale. Se la classe parziale è definita in più file, è possibile specificare la posizione di dichiarazione che verrà usata da **Progettazione classi** impostando la proprietà **Percorso nuovi membri** nella finestra **Proprietà**. In altre parole, quando si fa doppio clic su una forma di classe, **Progettazione classi** passa al file di origine che contiene la dichiarazione di classe identificata dalla proprietà **Percorso nuovi membri**. Quando si fa doppio clic su un metodo parziale in una forma di classe, **Progettazione classi** passa alla dichiarazione del metodo parziale. Inoltre, nella finestra **Proprietà** la proprietà **Nome file** fa riferimento alla posizione di dichiarazione. Per le classi parziali, **Nome file** elenca tutti i file che contengono codice di dichiarazione e implementazione per tale classe. Per i metodi parziali, tuttavia, **Nome file** elenca solo il file che contiene la dichiarazione del metodo parziale.

L'esempio seguente suddivide la definizione della classe `Employee` in due dichiarazioni, ognuna delle quali definisce una routine differente. Le due definizioni parziali negli esempi possono trovarsi in un singolo file di origine o in due file di origine differenti.

> [!NOTE]
> Visual Basic usa definizioni di classi parziali per separare il codice generato da Visual Studio dal codice creato dall'utente. Il codice viene separato in file di origine distinti. Ad esempio, **Progettazione Windows Form** definisce classi parziali per controlli come `Form`. In questi controlli il codice generato non deve essere modificato.

Per altre informazioni sui tipi parziali in Visual Basic, vedere [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Esempio

Per suddividere una definizione di classe, usare la parola chiave `partial` (`Partial` in Visual Basic), come illustrato nell'esempio seguente:

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="see-also"></a>Vedere anche

- [Classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial (Tipo) (Riferimenti per C#)](/dotnet/csharp/language-reference/keywords/partial-type)
- [parziale (Metodo) (Riferimenti per C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)