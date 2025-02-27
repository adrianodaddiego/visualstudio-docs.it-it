---
title: R Markdown
description: Come creare documenti R Markdown in Visual Studio per generare report, presentazioni e dashboard di alta qualità.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: b8f87f831c8076b22a61d7032d16be8d13f21b62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998630"
---
# <a name="create-r-markdown-documents"></a>Creare documenti R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) è un formato di documento che trasforma l'analisi in R in documenti, report, presentazioni e dashboard di alta qualità.

R Tools per Visual Studio (RTVS) offre un modello di elemento R Markdown, il supporto dell'editor (tra cui IntelliSense per il codice R all'interno dell'editor), funzionalità di generazione di file e anteprima dinamica.

## <a name="using-r-markdown"></a>Uso di R Markdown

1. Chiudere Visual Studio.
1. (Una sola volta) Installare `pandoc` da [pandoc.org](http://pandoc.org/installing.html).
1. Riavviare Visual Studio, che deve rilevare l'installazione di pandoc.
1. Installare i pacchetti `knitr` e `rmarkdown`. È possibile eseguire questa operazione dalla [finestra interattiva](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Creare un nuovo file R Markdown usando il comando di menu **File** > **Nuovo** > **File** e selezionando **R** > **R Markdown** dall'elenco. Nel contesto di un progetto fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Aggiungi R Markdown** oppure scegliere **Aggiungi** > **Nuovo elemento** e selezionare **R Markdown** nell'elenco.

1. Il contenuto predefinito del nuovo file è il seguente:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~

## <a name="previews"></a>Anteprime

Visual Studio 2017 versione 15.5 e versioni successive forniscono automaticamente l'anteprima dinamica per R Markdown. Per abilitare la sincronizzazione automatica tra l'editor e l'anteprima, selezionare **R Tools** > **Markdown** > **Sincronizzazione automatica** (**CTRL**+**MAIUSC**+**Y**). Se non si usa la sincronizzazione automatica, è possibile aggiornare l'anteprima tramite **R Tools** > **Markdown** > **Ricarica il riquadro di anteprima di R markdown**.

È anche possibile visualizzare in anteprima il file in formato HTML, PDF e Microsoft Word. A tale scopo, fare clic con il pulsante destro del mouse nell'editor e scegliere uno dei comandi **Anteprima**. Gli stessi comandi sono disponibili anche nel menu **R Tools** > **Markdown**. Nelle versioni precedenti di Visual Studio questi comandi sono disponibili nel menu **R Tools** > **Pubblica**.

![Anteprima dinamica di R Markdown e altri comandi di menu Anteprima](media/rmarkdown-live-preview.png)
