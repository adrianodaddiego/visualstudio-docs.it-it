---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 5, installare pacchetti
titleSuffix: ''
description: Passaggio 5 della procedura dettagliata di base sulle funzionalità di Visual Studio, che illustra le funzionalità di Visual Studio per la gestione dei pacchetti in un ambiente Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bf38def7be9607868df8f9c116266632ffcad710
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831238"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Passaggio 5: installare pacchetti nell'ambiente Python

**Passaggio precedente: [eseguire il codice nel debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La community degli sviluppatori di Python produce migliaia di pacchetti utili che è possibile incorporare nei propri progetti. Visual Studio offre un'interfaccia utente per gestire i pacchetti nei propri ambienti Python.

1. Selezionare il comando di menu **Visualizza** > **Altre finestre** > **Ambienti Python**. La finestra **Ambienti Python** viene visualizzata come peer in **Esplora soluzioni** e visualizza i diversi ambienti disponibili per l'utente. L'elenco include entrambi gli ambienti installati usando il programma di installazione di Visual Studio e quelli installati separatamente. L'ambiente in grassetto è l'ambiente predefinito che viene usato per i nuovi progetti.

   ![Finestra Ambienti Python](media/environments/environments-default-view-blue.png)

2. La scheda **Panoramica** dell'ambiente consente di accedere rapidamente a una finestra **interattiva** per l'ambiente corrispondente unitamente alla cartella di installazione e agli interpreti. Ad esempio, selezionare **Apri finestra interattiva** per visualizzare una finestra **interattiva** in Visual Studio per quell'ambiente specifico.

3. Selezionare la scheda **Pacchetti** e verrà visualizzato un elenco di pacchetti installati attualmente nell'ambiente.

   ![Pacchetti installati in un ambiente](media/environments/environments-installed-packages-blue.png)

4. Installare `matplotlib` immettendo il nome corrispondente nel campo di ricerca, quindi selezionare **pip install**

   ![Installazione di matplotlib nell'ambiente](media/environments/environments-add-matplotlib1.png)

5. Se richiesto, dare il consenso per l'elevazione dei privilegi.

6. Una volta installato, il pacchetto verrà visualizzato nella finestra **Ambienti Python**. La **X**, a destra del pacchetto, lo disinstalla.

   ![Completamento dell'installazione matplotlib nell'ambiente](media/environments/environments-add-matplotlib2.png)

   Sotto l'ambiente potrebbe essere visualizzato un indicatore di stato di piccole dimensioni a indicare che Visual Studio sta compilando il database di IntelliSense per il pacchetto appena installato. La scheda **IntelliSense** offre anche informazioni più dettagliate. Si noti che, fino al completamento del database, le funzionalità di IntelliSense come il completamento automatico e la verifica della sintassi non saranno attive nell'editor del pacchetto.

   Si noti che Visual Studio 2017 15.6 e versioni successive usano un metodo diverso e più veloce per l'uso di IntelliSense e visualizzano un messaggio in merito nella scheda **IntelliSense**.

7. Creare un nuovo progetto facendo clic su **File** > **Nuovo** > **Progetto** e selezionare il modello **Applicazione Python**. Nel file di codice che viene visualizzato incollare il codice seguente che crea una cosinusoide come nei passaggi dell'esercitazione precedente, questa volta tracciata graficamente:

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

8. Eseguire il programma con (**F5**) o senza il debugger (**CTRL**+**F5**) per visualizzare l'output:

   ![Output di esempio matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Usare Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Approfondimento

- [Ambienti Python](managing-python-environments-in-visual-studio.md)
