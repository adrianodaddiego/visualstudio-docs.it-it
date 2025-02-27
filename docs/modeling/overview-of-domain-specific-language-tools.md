---
title: Informazioni generali sugli strumenti di linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e31d9c01ded7754fd10419f3fd0e18d9616a51eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814124"
---
# <a name="overview-of-domain-specific-language-tools"></a>Informazioni generali sugli strumenti di linguaggio specifico di dominio
Domain-Specific Language Tools (strumenti DSL), che sono ospitati in Visual Studio, consentono di progettare un linguaggio specifico di dominio e quindi generare tutte le operazioni che gli utenti devono disporre per creare modelli basati sulla lingua.

 In Strumenti DSL sono inclusi gli strumenti seguenti:

- Una procedura guidata di creazione di progetti che usa modelli di soluzioni diverse per facilitare l'avvio dello sviluppo di un linguaggio specifico di dominio.

- Una finestra di progettazione con interfaccia grafica per la creazione e la modifica della definizione del linguaggio specifico di dominio.

- Un motore di convalida che assicura che la definizione del linguaggio specifico di dominio sia ben formata e visualizza errori e avvisi in caso di problemi.

- Un generatore di codice che riceve la definizione di un linguaggio specifico di dominio come input e produce codice sorgente come output.

## <a name="the-dsl-tools-solution"></a>Soluzione Strumenti DSL
 La Creazione guidata Finestra di progettazione Domain-Specific Language offre i modelli di soluzione seguenti:

- Flusso di attività

- Diagrammi classi

- Linguaggio minimo

- Modelli componente

- WPF minimo

- Windows.Forms minimo

- Libreria DSL

  Per altre informazioni, vedere [Scelta di un modello di soluzione per un linguaggio specifico di dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

  La procedura guidata crea una soluzione di Visual Studio con i progetti seguenti:

- Dsl

   Il progetto Dsl definisce il linguaggio specifico di dominio e i relativi strumenti di modifica e di elaborazione.

- **DslPackage**

   Al progetto DslPackage determina la modalità di integrazione degli strumenti di linguaggio con Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Interfaccia grafica di Strumenti DSL
 È possibile usare l'interfaccia grafica di Strumenti DSL per aggiungere elementi e relazioni al linguaggio specifico di dominio. Dopo aver aggiunto gli elementi, è possibile definirne l'aspetto eseguendone il mapping alle forme, personalizzandone i colori e aggiungendo elementi Decorator. È anche possibile aggiungere elementi alla casella degli strumenti.

## <a name="validation-in-dsl-tools"></a>Convalida in Strumenti DSL
 DSL è dotato di un livello di convalida che verifica che il modello di dominio soddisfi i requisiti di base per la generazione di codice. Quando si crea un linguaggio specifico di dominio personalizzato, in genere si aggiunge una convalida personalizzata che esprima le regole della logica di business. Per altre informazioni sulla convalida personalizzata, vedere [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).

 È consigliabile convalidare spesso il linguaggio specifico di dominio durante la progettazione. Se il linguaggio specifico di dominio presenta errori di convalida, non è possibile generare codice sorgente. È possibile eseguire il processo di generazione di codice sorgente dai modelli facendo clic su **Trasforma tutti i modelli** sulla barra degli strumenti di Esplora soluzioni. Ogni volta che si modifica la definizione del linguaggio, assicurarsi anche di **trasformare tutti i modelli**. Per altre informazioni, vedere [Procedura: Creare una soluzione per un linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personalizzazione di Strumenti DSL
 È possibile offrire codice aggiuntivo per perfezionare il comportamento del modello e definire vincoli per il linguaggio. Se necessario, è possibile apportare modifiche significative modificando i modelli di testo.

## <a name="distributing-your-dsl-solution"></a>Distribuzione della soluzione DSL
 Strumenti DSL genera un pacchetto che è ospitato in Visual Studio. Il pacchetto visualizza una casella degli strumenti, la finestra di esplorazione DSL e altri elementi dell'interfaccia utente che consentono agli utenti di creare modelli usando il linguaggio specifico di dominio creato.

 Quando si compila e si esegue la soluzione strumenti DSL in Visual Studio, una seconda istanza di Visual Studio viene illustrato l'aspetto del linguaggio specifico di dominio per l'utente del linguaggio. Dopo aver verificato che tutto funzioni correttamente, è possibile distribuire il file `.vsix` disponibile nella cartella di compilazione del progetto DslPackage. Questo file è utilizzabile per installare il linguaggio DSL come un'estensione di Visual Studio in altri computer.  Per altre informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vedere anche

- [Istanza sperimentale](../extensibility/the-experimental-instance.md)
- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)