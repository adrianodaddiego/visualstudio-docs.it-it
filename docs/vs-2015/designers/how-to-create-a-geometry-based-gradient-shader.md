---
title: 'Procedura: Creare uno shader con sfumatura basata sulla geometria | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eda8424aeb28231df0ae0355931989bec13a89b7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436168"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Procedura: Creare uno shader con sfumatura basata sulla geometria
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo documento illustra come usare la finestra di progettazione shader e il linguaggio DGSL (Directed Graph Shader Language) per creare uno shader con sfumatura basata sulla geometria. Questo shader ridimensiona un valore di colore RGB costante in base all'altezza di ogni punto di un oggetto nello spazio globale.  
  
 Questo documento illustra le attività seguenti:  
  
- Aggiunta di nodi a un grafico shader  
  
- Impostazione delle proprietà del nodo  
  
- Disconnessione di nodi  
  
- Connessione ai nodi  
  
## <a name="creating-a-geometry-based-gradient-shader"></a>Creazione di uno shader con sfumatura basata sulla geometria  
 È possibile implementare uno shader basato sulla geometria incorporando la posizione del pixel nello shader. Nei linguaggi shader, oltre al colore e alla posizione sullo schermo 2D, un pixel contiene altre informazioni. Un pixel, noto in alcuni sistemi come *frammento*, è costituito da una raccolta di valori che descrivono l'area corrispondente a un pixel. Lo shader descritto in questo documento utilizza l'altezza di ciascun pixel di un oggetto 3D nello spazio globale per influire sul colore di output finale del frammento.  
  
 Prima di iniziare, assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.  
  
#### <a name="to-create-a-geometry-based-gradient-shader"></a>Per creare uno shader con sfumatura basata sulla geometria  
  
1. Creare uno shader DGSL da utilizzare. Per informazioni su come aggiungere uno shader DGSL al progetto, vedere la sezione Introduzione in [Finestra di progettazione shader](../designers/shader-designer.md).  
  
2. Scollegare il nodo **Colore punto** dal nodo **Colore finale**. Scegliere il terminale **RGB** del nodo **Colore punto** e quindi scegliere **Interrompi collegamenti**. In questo modo si crea lo spazio per il nodo che viene aggiunto nel passaggio successivo.  
  
3. Aggiungere un nodo **Per** al grafico. Nella **casella degli strumenti**, in **Matematica**, selezionare **Per** e spostarlo nell'area di progettazione.  
  
4. Aggiungere un nodo **Mascheramento vettore** al grafico. Nella **casella degli strumenti**, in **Utilità**, selezionare **Mascheramento vettore** e spostarlo nell'area di progettazione.  
  
5. Specificare i valori di maschera per il nodo **Mascheramento vettore**. In modalità **Seleziona** selezionare il nodo **Mascheramento vettore** e nella finestra **Proprietà** impostare la proprietà **Verde / Y** su **True**. Impostare quindi le proprietà **Rosso / X**, **Blu / Z** e **Alfa / W** su **False**. In questo esempio, le proprietà **Rosso / X**, **Verde / Y** e **Blu / Z** corrispondono ai componenti x, y e z del nodo **Posizione globale** e **Alfa / W** non viene usato. Poiché solo **Verde / Y** è impostato su **True**, dopo il mascheramento del vettore di input rimane solo il componente y.  
  
6. Aggiungere un nodo **Posizione globale** al grafico. Nella **casella degli strumenti**, in **Costanti**, selezionare **Posizione globale** e spostarlo nell'area di progettazione.  
  
7. Mascherare la posizione del frammento nello spazio globale. In modalità **Seleziona** spostare il terminale **Output** del nodo **Posizione globale** nel terminale **Vettore** del nodo **Mascheramento vettore**. Questa connessione maschera la posizione del frammento in modo da ignorare i componenti x e z.  
  
8. Moltiplicare la costante di colore RGB per la posizione mascherata nello spazio globale. Spostare il terminale **RGB** del nodo **Colore punto** nel terminale **Y** del nodo **Per** e quindi spostare il terminale **Output** del nodo **Mascheramento vettore** nel terminale **X** del nodo **Per**. Tale connessione consente di ridimensionare il valore del colore in base all'altezza del pixel nello spazio globale.  
  
9. Collegare il valore del colore ridimensionato al colore finale. Spostare il terminale **Output** del nodo **Per** nel terminale **RGB** del nodo **Colore finale**.  
  
   La figura seguente illustra il grafico shader completato e un'anteprima dello shader applicato a una sfera.  
  
> [!NOTE]
> In questa figura è stato specificato un colore arancione per illustrare meglio l'effetto dello shader, ma poiché la forma di anteprima non ha una posizione nello spazio globale, lo shader non può essere interamente visualizzato in anteprima nella finestra di progettazione dello shader. Per poter illustrare l'effetto completo, lo shader deve essere visualizzato in anteprima in una scena reale.  
  
 ![Grafico shader e anteprima del relativo effetto](../designers/media/digit-gradient-effect-graph.png "Digit-Gradient-Effect-Graph")  
  
 Alcune forme potrebbero produrre anteprime migliori per alcuni shader. Per informazioni su come visualizzare in anteprima gli shader nella finestra di progettazione shader, vedere la sezione **Anteprima degli shader** in [Finestra di progettazione shader](../designers/shader-designer.md).  
  
 Nella figura seguente illustra lo shader descritto in questo documento applicato alla scena 3D illustrata in [come: Modello di terreno 3D](../designers/how-to-model-3-d-terrain.md). L'intensità del colore aumenta con l'altezza del punto nello spazio globale.  
  
 ![Effetto sfumatura applicato a un modello di terreno 3D](../designers/media/digit-gradient-effect-result.png "Digit-Gradient-Effect-Result")  
  
 Per altre informazioni su come applicare uno shader a un modello 3D, vedere [come: Applicare uno Shader a un modello 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Applicare uno Shader a un modello 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Procedura: Esportare uno Shader](../designers/how-to-export-a-shader.md)   
 [Procedura: Modello di terreno 3D](../designers/how-to-model-3-d-terrain.md)   
 [Procedura: Creare uno shader con trama in scala di grigi](../designers/how-to-create-a-grayscale-texture-shader.md)   
 [Finestra di progettazione shader](../designers/shader-designer.md)   
 [Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md)
