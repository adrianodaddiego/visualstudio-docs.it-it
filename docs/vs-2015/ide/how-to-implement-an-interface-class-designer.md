---
title: "Procedura: Implementare un'interfaccia (Progettazione classi) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1b437fb34902783002baedee992a21ee61a86c2e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685617"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Procedura: Implementare un'interfaccia (Progettazione classi)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Progettazione classi è possibile implementare un'interfaccia nel diagramma classi connettendola a una classe che fornisce il codice per i metodi di interfaccia. Progettazione classi genera un'implementazione dell'interfaccia e visualizza la relazione tra l'interfaccia e la classe come relazione di ereditarietà. È possibile implementare un'interfaccia tracciando una linea di ereditarietà tra l'interfaccia e la classe oppure trascinando l'interfaccia dalla visualizzazione classi.  
  
> [!TIP]
> È possibile creare le interfacce allo stesso modo in cui vengono creati altri tipi di elemento. Se l'interfaccia esiste ma non viene visualizzata nel diagramma classi, è necessario innanzitutto visualizzarla. Per altre informazioni, vedere [Procedura: Creare tipi usando Progettazione classi](../ide/how-to-create-types-by-using-class-designer.md) e [come: Visualizzare i tipi esistenti (Progettazione classi)](../ide/how-to-view-existing-types-class-designer.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Per implementare un'interfaccia tracciando una linea di ereditarietà  
  
1. Nel diagramma classi visualizzare l'interfaccia e la classe che implementa l'interfaccia.  
  
2. Tracciare una linea di ereditarietà dalla classe e all'interfaccia.  
  
    Viene visualizzato un simbolo di interfaccia collegato alla classe, mentre un'etichetta con il nome dell'interfaccia identifica la relazione di ereditarietà. Visual Studio genera stub per tutti i membri di interfaccia.  
  
   Per altre informazioni, vedere [Procedura: Creare ereditarietà tra tipi (Progettazione classi)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>Per implementare un'interfaccia dalla finestra Visualizzazione classi  
  
1. Nel diagramma classi visualizzare la classe che deve implementare l'interfaccia.  
  
2. Aprire Visualizzazione classi e individuare l'interfaccia.  
  
    > [!TIP]
    > Se non è già visualizzata, aprire Visualizzazione classi dal menu **Visualizza**. Per altre informazioni sulla visualizzazione classi, vedere [Viewing Classes and Their Members](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333) (Visualizzazione delle classi e dei relativi membri).  
  
3. Trascinare il nodo di interfaccia nella forma della classe nel diagramma.  
  
     Viene visualizzato un simbolo di interfaccia collegato alla classe, mentre un'etichetta con il nome dell'interfaccia identifica la relazione di ereditarietà. Visual Studio genera stub per tutti i membri di interfaccia. A questo punto, l'interfaccia è stata implementata.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare tipi usando Progettazione classi](../ide/how-to-create-types-by-using-class-designer.md)   
 [Procedura: Visualizzare i tipi esistenti (Progettazione classi)](../ide/how-to-view-existing-types-class-designer.md)   
 [Procedura: Creare ereditarietà tra tipi (Progettazione classi)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring di classi e tipi (Progettazione classi)](../ide/refactoring-classes-and-types-class-designer.md)
