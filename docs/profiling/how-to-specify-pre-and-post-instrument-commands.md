---
title: 'Procedura: Specificare comandi pre- e post-strumentazione | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dec06f7f45666845dfcc7080ed4b18db8baba993
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539063"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Procedura: Specificare comandi pre- e post-strumentazione

È possibile specificare i comandi da eseguire prima o dopo che vengano instrumentati i file binari in una sessione di prestazioni. Tutti i comandi eseguibili dalla riga di comando possono essere specificati come eventi pre-strumentazione o post-strumentazione. Ad esempio, è possibile specificare comandi che automatizzano la riapposizione della firma di un assembly con una chiave con nome sicuro in un file batch eseguito dopo la strumentazione dei file binari.

È possibile specificare comandi per tutti i file binari instrumentati nell'esecuzione della profilatura o per singoli file binari. Tuttavia, è possibile specificare un solo comando pre-strumentazione da eseguire prima e un solo comando post-strumentazione da eseguire dopo il processo di strumentazione. Non è possibile specificare comandi sia per tutti i file binari che per singoli file binari. Quando si specificano comandi per tutti i file binari, i comandi vengono eseguiti prima o dopo la strumentazione di ogni file binario della sessione.

La directory di lavoro nella quale vengono eseguiti i comandi dipende dal sistema operativo in cui è in esecuzione [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] e dalla piattaforma di destinazione dell'applicazione profilata.

Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="to-specify-pre-instrument-commands"></a>Per specificare comandi pre-strumentazione

1. Effettuare uno dei passaggi indicati di seguito.

    - Per specificare comandi pre-strumentazione per tutti i file binari in una sessione di prestazioni, selezionare il nodo della sessione di prestazioni in **Esplora prestazioni** e quindi fare clic con il pulsante destro del mouse e selezionare **Proprietà**.

    - Per specificare comandi pre-strumentazione per un file binario specifico, fare clic con il pulsante destro del mouse sul nome del file binario nell'elenco **Destinazioni** della sessione di prestazioni e quindi selezionare **Proprietà**.

2. In **Pagine delle proprietà** fare clic su **Strumentazione**.

3. Digitare il comando nella casella di testo **Riga di comando** in **Eventi pre-strumentazione**.

    > [!NOTE]
    > È possibile fare clic sul pulsante con i puntini di sospensione **(...)** adiacente alla casella **Riga di comando** per individuare e selezionare il file con estensione EXE, CMD o BAT appropriato.

4. Fare clic su **OK**.

     Per disabilitare l'esecuzione del comando senza rimuoverlo, selezionare la casella di controllo **Escludere dalla strumentazione**. Per modificare le impostazioni del compilatore o del linker, usare le pagine delle proprietà del progetto.

## <a name="to-specify-post-instrument-commands"></a>Per specificare comandi post-strumentazione

1. Effettuare uno dei passaggi indicati di seguito.

    - Per specificare comandi post-strumentazione per tutti i file binari in una sessione di prestazioni, selezionare il nodo della sessione di prestazioni in **Esplora prestazioni** e quindi fare clic con il pulsante destro del mouse e selezionare **Proprietà**.

    - Per specificare comandi post-strumentazione per un file binario specifico, fare clic con il pulsante destro del mouse sul nome del file binario nell'elenco **Destinazioni** della sessione di prestazioni e quindi selezionare **Proprietà**.

2. In **Pagine delle proprietà** fare clic su **Strumentazione**.

3. Digitare il comando nella casella di testo **Riga di comando** in **Eventi post-strumentazione**.

    > [!NOTE]
    > È possibile fare clic sul pulsante con i puntini di sospensione **(...)** adiacente alla casella **Riga di comando** per individuare e selezionare il file con estensione EXE, CMD o BAT appropriato.

4. Fare clic su **OK**.

     Per disabilitare l'esecuzione del comando senza rimuoverlo, selezionare la casella di controllo **Escludere dalla strumentazione**. Per modificare le impostazioni del compilatore o del linker, usare le pagine delle proprietà del progetto.

## <a name="see-also"></a>Vedere anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
