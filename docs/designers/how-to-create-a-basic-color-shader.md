---
title: 'Procedura: Creare uno shader con colore di base'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f15bba37f5a03da934fae9ba4689da7775cfdb92
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844868"
---
# <a name="how-to-create-a-basic-color-shader"></a>Procedura: Creare uno shader con colore di base

Questo articolo illustra come usare la finestra di progettazione shader e il linguaggio DGSL (Directed Graph Shader Language) per creare uno shader con colore uniforme. Questo shader imposta il colore finale su un valore di colore RGB costante.

## <a name="create-a-flat-color-shader"></a>Creare uno shader con colore uniforme

È possibile implementare uno shader con colore uniforme scrivendo il valore di colore di una costante di colore RGB nel colore di output finale.

Prima di iniziare, assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.

1. Creare uno shader DGSL da utilizzare. Per informazioni su come aggiungere uno shader DGSL al progetto, vedere la sezione Introduzione in [Finestra di progettazione shader](../designers/shader-designer.md).

2. Eliminare il nodo **Colore punto**. Usare lo strumento **Seleziona** per selezionare il nodo **Colore punto** e scegliere **Modifica** > **Elimina** nella barra dei menu.

3. Aggiungere un nodo **Costante colore** al grafico. Nella **casella degli strumenti**, in **Costanti**, selezionare **Costante colore** e spostarlo nell'area di progettazione.

4. Specificare un valore di colore per il nodo **Costante colore**. Usare lo strumento **Seleziona** per selezionare il nodo **Costante colore** e quindi specificare un valore di colore nella proprietà **Output** della finestra **Proprietà**. Per arancione, specificare un valore di (1.0, 0,5, 0,2, 1.0).

5. Connettere la costante di colore al colore finale. Per creare le connessioni, spostare il terminale **RGB** del nodo **Costante colore** nel terminale **RGB** del nodo **Colore finale** e quindi spostare il terminale **Alfa** del nodo **Costante colore** nel terminale **Alfa** del nodo **Colore finale**. Queste connessioni impostano il colore finale sulla costante di colore definita nel passaggio precedente.

La figura seguente illustra il grafico shader completato e un'anteprima dello shader applicato a un cubo.

> [!NOTE]
> Nella figura è stato specificato un colore arancione per illustrare meglio l'effetto dello shader.

![Grafico shader e risultato in un modello 3&#45;D](../designers/media/digit-flat-color-effect.png)

Alcune forme potrebbero produrre anteprime migliori per alcuni shader. Per altre informazioni su come visualizzare in anteprima gli shader nella finestra di progettazione shader, vedere [Finestra di progettazione shader](../designers/shader-designer.md).

## <a name="see-also"></a>Vedere anche

- [Procedura: Applicare uno shader a un modello 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Procedura: Esportare uno shader](../designers/how-to-export-a-shader.md)
- [Finestra di progettazione shader](../designers/shader-designer.md)
- [Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md)