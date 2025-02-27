---
title: Disegnare forme e tracciati
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e0efd4b4f9fb301f5bcba4a12857647a8d911f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899336"
---
# <a name="draw-shapes-and-paths"></a>Disegnare forme e tracciati

Nella finestra di progettazione XAML la parola *forma* indica esattamente una forma. Ad esempio: un rettangolo, un cerchio o un'ellissi. Un *tracciato* è una versione più flessibile di una forma. È possibile ad esempio modificarne la forma o combinarli per creare nuove forme.

Le forme e i tracciati usano la grafica vettoriale per una scalabilità ottima negli schermi ad alta risoluzione. Per altre informazioni sulla grafica vettoriale, guardare il video [What are Vector Graphics?](https://www.youtube.com/watch?v=MoCSwF0n-io) (Che cos'è la grafica vettoriale?) o leggere la definizione di [grafica vettoriale](http://www.webopedia.com/TERM/V/vector_graphics.html).

## <a name="Shape"></a> Disegnare una forma
 Le forme sono disponibili nel pannello **Asset** .

 ![Categoria Forme nel pannello Asset](../designers/media/b4_shapes_assetspanel.png)

 Trascinare la forma da usare nella tavola da disegno. Usare quindi gli handle della forma per ridimensionarla, ruotarla, spostarla o inclinarla.

 ![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="Path"></a> Disegnare un tracciato
 Un tracciato è costituito da una serie di linee e curve collegate. Usare un tracciato per creare forme interessanti, non disponibili nel pannello **Asset** .

 È possibile disegnare un tracciato usando una riga, una penna o una matita. Questi strumenti sono disponibili nel pannello **Strumenti** .

 ![Strumento Penna](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png) ![Opzioni dello strumento Penna](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png)

### <a name="draw-a-straight-line"></a>Disegnare una linea retta
 Usare lo strumento **Penna** ![strumento Penna](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png)oppure lo strumento **Linea** ![strumento Linea](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png).

 **Uso dello strumento Penna** ![strumento Penna](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png)

 Nella tavola da disegno fare clic una volta per definire il punto di inizio, quindi fare di nuovo clic per definire la fine della linea.

 **Uso dello strumento Linea** ![strumento Linea](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png)

 Nella tavola da disegno trascinare il puntatore dal punto in cui si vuole che abbia inizio la riga e quindi rilasciare il puntatore nel punto in cui si vuole che termini la linea.

### <a name="draw-a-curve"></a>Disegnare una curva
 Usare lo strumento **Penna** ![strumento Penna](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Nella tavola da disegno fare clic una volta per definire il punto di inizio di una linea, quindi fare clic e trascinare il puntatore per creare la curva desiderata.

 Per chiudere il tracciato, fare clic sul primo punto della linea.

### <a name="change-the-shape-of-a-curve"></a>Cambiare la forma di una curva
 Usare lo strumento **Selezione diretta** ![strumento Selezione diretta](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Fare clic sulla forma, quindi trascinare qualsiasi punto della forma per modificare le forme della curva.

### <a name="draw-a-free-form-path"></a>Disegnare un tracciato a mano libera
 Usare lo strumento **Matita** ![strumento Matita](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png).

 Nella tavola da disegno disegnare un tracciato a mano libera, proprio come se si usasse una vera matita.

### <a name="remove-part-of-a-path"></a>Eliminare una parte di un tracciato
 Usare lo strumento **Selezione diretta** ![strumento Selezione diretta](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Selezionare il tracciato contenente il segmento da eliminare, quindi fare clic su **Elimina** .

### <a name="remove-a-point-in-a-path"></a>Rimuovere un punto da un tracciato
 Usare lo strumento **Selezione** ![strumento Selezione](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) e lo strumento **Penna** ![strumento Penna](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Usare lo strumento **Selezione** ![strumento Selezione](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) per selezionare il tracciato. Usare quindi lo strumento **Penna** ![strumento Penna](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) per fare clic sul punto da rimuovere.

### <a name="add-a-point-to-a-path"></a>Aggiungere un punto a un tracciato
 Usare lo strumento **Selezione** ![strumento Selezione](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) e lo strumento **Penna** ![strumento Penna](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Usare lo strumento **Selezione** ![strumento Selezione](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) per selezionare il tracciato. Usare lo strumento **Penna** ![strumento Penna](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) per fare clic in un punto qualsiasi del tracciato in cui si vuole aggiungere il punto.

## <a name="Convert"></a> Convertire una forma in un tracciato
 Per modificare una forma in modo analogo alla modifica di un tracciato, convertire la forma in tracciato.

 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png) [Uso dei tracciati: Convertire una forma in un tracciato](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

## <a name="Combine"></a> Combinare tracciati
 È possibile combinare forme e tracciati in un unico tracciato.

 ![Combinare tracciati](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|||||
|-|-|-|-|
|![Due forme prima della combinazione](../designers/media/b1_1.png)|Due forme prima della combinazione|![Interseca](../designers/media/b1_4.png)|Interseca|
|![Escludi sovrapposizione](../designers/media/b1_2.png)|Unisci|![](../designers/media/b1_5.png)|Escludi sovrapposizione|
|![Sottrai](../designers/media/b1_3.png)|Dividi|![](../designers/media/b1_6.png)|Sottrai|

 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png) [Uso dei tracciati: Combinare tracciati](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="Compound"></a> Creare un tracciato composto
 Quando si crea un tracciato composto, eventuali parti del tracciato che si intersecano vengono sottratte dal risultato e il tracciato risultante assume le proprietà visive del percorso situato più in basso.

 È possibile separare un tracciato composto in qualsiasi momento dopo averlo creato.

 ![Interrompere un tracciato composto](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png) [Uso dei tracciati: Creare un tracciato composto](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="Clipping"></a> Creare un tracciato di ritaglio
 Un tracciato di ritaglio è un tracciato o una forma applicato a un altro oggetto, in modo da nascondere le parti dell'oggetto mascherato esterne al tracciato di ritaglio.

 ![Tracciato di ritaglio](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.png) [Uso dei tracciati: Creare un tracciato di ritaglio](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).

## <a name="see-also"></a>Vedere anche

- [Creazione di un'interfaccia utente usando Blend per Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)