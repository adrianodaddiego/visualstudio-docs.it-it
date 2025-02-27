---
title: Calcola metrica codice
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b44f2a36297db3265a3904f1f76596ca6ba0e35
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260468"
---
# <a name="code-metrics-values"></a>Valori della metrica del codice

La maggiore complessità delle applicazioni software moderne aumenta anche la difficoltà di rendere il codice affidabile e facile da gestire. La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Grazie all'uso della metrica del codice, gli sviluppatori possono comprendere quali tipi e/o i metodi devono essere rielaborati o più approfonditi. I team di sviluppo possono identificare i potenziali rischi, comprendere lo stato corrente di un progetto e tenere traccia dello stato durante lo sviluppo di software.

Gli sviluppatori possono utilizzare Visual Studio per generare dati di metrica del codice che consentono di misurare la complessità e della manutenibilità del codice gestito. Dati di metrica codice possono essere generati per un'intera soluzione o un singolo progetto.

Per informazioni su come generare dati di metrica codice in Visual Studio, vedere [come: Generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Misurazioni di software

L'elenco seguente mostra il codice di risultati di metrica per il calcolo di Visual Studio:

- **Indice di manutenibilità** -calcola un valore di indice compreso tra 0 e 100 che rappresenta la relativa semplicità di gestione del codice. Un valore elevato indica una migliore gestibilità. Le classificazioni di codifica a colori sono utilizzabile per identificare rapidamente aree problematiche nel codice. Una classificazione uguale a verde è compreso tra 20 e 100 e indica che il codice ha una buona manutenibilità. Una classificazione uguale a giallo è compreso tra 10 e 19 e indica che il codice sia moderatamente gestibile. Una classificazione uguale a rosso è una classificazione compresa tra 0 e 9 e indica una manutenibilità insufficiente. Per altre informazioni, vedere la [intervallo di indice di manutenibilità e il significato](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) post di blog.

- **Complessità ciclomatica** -misura la complessità del codice strutturale. Viene creato dal calcolo del numero di percorsi del codice diversi nel flusso del programma. Un programma che ha il flusso di controllo complessi richiede altri test per ottenere buona copertura del codice ed è meno facile da gestire. Per altre informazioni, vedere la [di Wikipedia relativa complessità ciclomatica](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Profondità dell'ereditarietà** -indica il numero di diverse classi che ereditano da uno a altro, fino alla classe di base. Profondità dell'ereditarietà è simile alla classe consente di connettere in quanto una modifica in una classe base può influire sulle qualsiasi delle relative classi ereditate. Maggiore questo numero, più profondo l'ereditarietà e maggiore sarà il potenziale per apportare modifiche di classe di base a comportare un'interruzione di modifica. Per la profondità dell'ereditarietà, è consigliabile un valore basso e un valore elevato non è valido. 

- **Accoppiamento di classe** -misura l'accoppiamento di classi univoche tramite i parametri, variabili locali, tipi restituiti, chiamate al metodo, creazioni di istanza generica o modello, le classi di base, le implementazioni dell'interfaccia, i campi definiti nei tipi esterni, e decorazione di attributo. Progettazione software di qualità impone che i tipi e metodi devono avere un'elevata coesione e accoppiamento basso. Accoppiamento elevato indica una progettazione che è difficile da riutilizzare e gestire a causa delle molte interdipendenze con altri tipi. Per altre informazioni, vedere la [accoppiamenti di classi](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) post di blog.

- **Righe di codice** -indica il numero approssimativo di righe di codice. Il conteggio è basato sul codice IL e non è pertanto il numero esatto di righe nel file del codice sorgente. Un conteggio elevato potrebbe indicare che un tipo o metodo sta provando a eseguire troppe operazioni e deve essere suddiviso. Può anche indicare che il tipo o metodo potrebbe essere difficile da gestire.

   > [!NOTE]
   > Il [versione della riga di comando](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) del codice strumento metriche conta le righe effettive di codice perché analizza il codice sorgente anziché IL.

## <a name="anonymous-methods"></a>Metodi anonimi

Un' *metodo anonimo* è semplicemente un metodo che non ha nome. Metodi anonimi vengono spesso usati per passare un blocco di codice come un parametro del delegato. I risultati della metrica per un metodo anonimo che viene dichiarato in un membro, ad esempio un metodo o una funzione di accesso, associati con il membro che dichiara il metodo. Non sono associati al membro che chiama il metodo.

Per altre informazioni sul modo in cui la metrica del codice gestisce i metodi anonimi, vedere [metodi anonimi e analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Codice generato

Alcuni strumenti software e i compilatori di generano il codice che viene aggiunto a un progetto e che lo sviluppatore di progetto non consente di visualizzare o non deve cambiare. In genere, la metrica del codice ignora il codice generato quando si calcola i valori delle metriche. In questo modo i valori delle metriche in base a ciò che lo sviluppatore può visualizzare e modificare.

Codice generato per i moduli di Windows non viene ignorato, poiché si tratta di codice che lo sviluppatore può visualizzare e modificare.

## <a name="next-steps"></a>Passaggi successivi

- [Procedura: Generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md)
- [Utilizzare la finestra Risultati metrica codice](../code-quality/working-with-code-metrics-data.md)
