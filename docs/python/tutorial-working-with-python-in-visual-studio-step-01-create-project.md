---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 1, creare un progetto
titleSuffix: ''
description: Panoramica e passaggio 1 della procedura dettagliata di base delle funzionalità di Python in Visual Studio, inclusi i prerequisiti e la creazione di un nuovo progetto Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ed4fdbfe7090a66d955461f2c3a394f6fb661c5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62430744"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Esercitazione: usare Python in Visual Studio

Python è un linguaggio di programmazione molto diffuso affidabile, flessibile, facile da imparare, il cui uso è gratuito in tutti i sistemi operativi e supportato sia da un'attiva community di sviluppatori che da numerose librerie gratuite. Il linguaggio supporta tutte le modalità di sviluppo, tra cui applicazioni Web, servizi Web, app desktop, script e calcolo scientifico. Viene usato in molte università, nonché da scienziati, sviluppatori professionisti e non professionisti.

Visual Studio offre un supporto dei linguaggi di prima classe per Python. Completare le fasi dell'esercitazione indicate di seguito:

- [Passaggio 0: installazione](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Passaggio 1: creare un progetto Python (questo articolo)](#step-1-create-a-new-python-project)
- [Passaggio 2: scrivere ed eseguire codice per usare Visual Studio IntelliSense](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Passaggio 3: creare altro codice nella finestra Interattiva REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Passaggio 4: eseguire il programma completo nel debugger di Visual Studio](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Passaggio 5: installare pacchetti e gestire gli ambienti Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Passaggio 6: usare Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Passaggio 1: Creare un nuovo progetto Python

Per *progetto* si intende la modalità con cui Visual Studio gestisce tutti i file inclusi nella creazione di una singola applicazione, come codice sorgente, risorse, configurazioni e così via. Un progetto formalizza e gestisce la relazione tra i file del progetto, nonché le risorse esterne che vengono condivise tra più progetti. Di conseguenza, il progetto consente all'applicazione di espandersi e crescere molto più facilmente rispetto alla semplice gestione delle relazioni di un progetto in cartelle ad hoc, script, file di testo e persino nel processo mentale dello sviluppatore.

In questa esercitazione si inizia con un semplice progetto che contiene un singolo file di codice vuoto.

1. In Visual Studio selezionare **File** > **Nuovo** > **Progetto** (**CTRL**+**MAIUSC**+**N**), che visualizza la finestra di dialogo **Nuovo progetto**. Qui è possibile esplorare i modelli tra i diversi linguaggi, quindi selezionarne uno per il progetto e specificare dove inserire i file Visual Studio.

1. Per visualizzare i modelli Python, selezionare **Installati** > **Python** a sinistra oppure cercare "Python". La ricerca è un ottimo modo per trovare un modello quando non si ricorda la posizione nell'albero dei linguaggi.

    ![Finestra di dialogo Nuovo progetto con visualizzati i progetti Python](media/vs-getting-started-python-01-new-project.png)

    Il supporto per Python in Visual Studio include vari modelli di progetto, incluse applicazioni Web che usano i framework Bottle, Flask e Django insieme a Servizi cloud di Azure. Per gli scopi di questa procedura dettagliata, tuttavia, si inizierà con un progetto vuoto.

1. Selezionare il modello **Applicazione Python**, specificare un nome per il progetto e selezionare **OK**.

1. Dopo qualche secondo, Visual Studio visualizza la struttura del progetto nella finestra **Esplora soluzioni** (1). Il file di codice predefinito è aperto nell'editor (2). La finestra **Proprietà** (3) offre anche la possibilità di visualizzare informazioni aggiuntive per qualsiasi elemento selezionato in **Esplora soluzioni**, tra cui la posizione esatta su disco.

    ![Esplora soluzioni con un progetto Python](media/vs-getting-started-python-02-windows.png)

1. Dedicare qualche minuto ad acquisire familiarità con **Esplora soluzioni**, il luogo in cui cercare file e cartelle nel progetto.

    ![L'espansione di Esplora soluzioni consente di visualizzare le varie funzionalità](media/vs-getting-started-python-03-solution-explorer.png)

    (1) In grassetto viene visualizzato il progetto con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Sul disco questo progetto è rappresentato nella cartella del progetto da un file con estensione *.pyproj*.

    (2) Al primo livello è presente una *soluzione* che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata su disco da un file con estensione *sln*, è un contenitore per uno o più progetti correlati. Ad esempio, se si scrive un'estensione C++ per l'applicazione Python, il progetto C++ può risiedere nella stessa soluzione. La soluzione può contenere anche un progetto per un servizio web, insieme ai progetti per i programmi di test dedicati.

    (3) Nel progetto si possono vedere i file di origine, in questo caso un solo file con estensione *py*. Se si seleziona un file, le rispettive proprietà vengono visualizzate nella finestra **Proprietà**. Facendo doppio clic su un file, questo verrà aperto nel modo più appropriato.

    (4) Il nodo **Ambienti Python** è visualizzabile anche dal progetto. Attraverso l'espansione è possibile visualizzare gli interpreti Python disponibili. Espandere un nodo dell'interprete per visualizzare le librerie installate in tale ambiente (5).

    Fare doppio clic su qualsiasi nodo o elemento in **Esplora soluzioni** per accedere a un menu di comandi validi. Ad esempio, il comando **Rinomina** consente di modificare il nome di un nodo o di un elemento, inclusi il progetto e la soluzione.

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Scrivere ed eseguire codice](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Approfondimento

- [Progetti Python in Visual Studio](managing-python-projects-in-visual-studio.md)
- [Informazioni sul linguaggio Python in python.org](https://www.python.org)
- [Python per utenti meno esperti](https://www.python.org/about/gettingstarted/) (python.org)
