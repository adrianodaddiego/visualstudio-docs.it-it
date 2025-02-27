---
title: 'Procedura: Dividere una classe in classi parziali (Progettazione classi) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 23d344d2f350b5b7a2e376e8856c916d9baa01f2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702616"
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Procedura: dividere una classe in classi parziali (Progettazione classi)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile dividere la dichiarazione di una classe o struttura in più dichiarazioni usando la parola chiave `Partial` in Visual Basic o la parola chiave `partial` in Visual C#. Si può usare il numero di dichiarazioni parziali desiderato, in un numero qualsiasi di file di origine differenti oppure in un singolo file di origine. Tutte le dichiarazioni, tuttavia, devono trovarsi nello stesso assembly e nello stesso spazio dei nomi.  
  
 Le classi parziali sono utili in varie situazioni. Ad esempio, quando si lavora su progetti di grandi dimensioni, la separazione di una classe in più file consente a più programmatori di lavorare in contemporanea. Quando si lavora con il codice generato da Visual Studio, è possibile modificare la classe senza dover ricreare il file di origine. (Il codice wrapper per Windows Form e per servizi Web è un esempio di codice generato da Visual Studio.) È possibile creare codice che usa classi generate automaticamente senza dover modificare il file creato da Visual Studio.  
  
 Esistono due tipi di metodi parziali, chiamati dichiarazione e implementazione in Visual C# e Visual Basic.  
  
 Progettazione classi supporta classi e metodi parziali. La forma del tipo nel diagramma classi fa riferimento a una singola posizione di dichiarazione per la classe parziale. Se la classe parziale è definita in più file, è possibile specificare la posizione di dichiarazione che verrà usata da Progettazione classi impostando la proprietà **Percorso nuovi membri** nella finestra **Proprietà**. In altre parole, quando si fa doppio clic su una forma di classe, Progettazione classi passa al file di origine che contiene la dichiarazione di classe identificata dalla proprietà **Percorso nuovi membri**. Quando si fa doppio clic su un metodo parziale in una forma di classe, Progettazione classi passa alla dichiarazione del metodo parziale. Inoltre, nella finestra **Proprietà** la proprietà **Nome file** fa riferimento alla posizione di dichiarazione. Per le classi parziali, **Nome file** elenca tutti i file che contengono codice di dichiarazione e implementazione per tale classe. Per i metodi parziali, tuttavia, **Nome file** elenca solo il file che contiene la dichiarazione del metodo parziale.  
  
 L'esempio seguente suddivide la definizione della classe `Employee` in due dichiarazioni, ognuna delle quali definisce una routine differente. Le due definizioni parziali negli esempi possono trovarsi in un singolo file di origine o in due file di origine differenti.  
  
> [!NOTE]
> Visual Basic usa definizioni di classi parziali per separare il codice generato da Visual Studio dal codice creato dall'utente. Il codice viene separato in file di origine distinti. Ad esempio, **Progettazione Windows Form** definisce classi parziali per controlli come `Form`. In questi controlli il codice generato non deve essere modificato.  
  
 Per altre informazioni sui tipi parziali in Visual Basic, vedere [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448).  
  
## <a name="example"></a>Esempio  
 Per suddividere una definizione di classe in Visual Basic, usare la parola chiave `Partial`, come illustrato nell'esempio seguente.  
  
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
  
## <a name="example"></a>Esempio  
 Per suddividere una definizione di classe in Visual C#, usare la parola chiave `partial`, come illustrato nell'esempio seguente.  
  
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
  
## <a name="see-also"></a>Vedere anche  
 [Classi e metodi parziali](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)   
 [parziale (Tipo)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)   
 [parziale (Metodo) (Riferimenti per C#)](https://msdn.microsoft.com/library/43f40242-17e0-4452-8573-090503ad3137)   
 [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)
