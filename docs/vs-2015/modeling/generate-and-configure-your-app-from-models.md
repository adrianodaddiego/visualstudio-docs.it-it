---
title: Generare e configurare l'app da modelli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 4dc8f572-a09e-4d19-a92d-f1df383e728b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bb12d80c581b0ea0b605932083cf4f62fe764e30
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073488"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generare e configurare l'app da modelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile generare o configurare parti dell'applicazione da un modello. Il modello può essere in linguaggio UML o DSL.  
  
 Un modello rappresenta i requisiti in modo più diretto rispetto al codice. Derivando il comportamento dell'applicazione direttamente dal modello, è possibile rispondere ai cambiamenti di requisiti con maggiore rapidità e affidabilità che non semplicemente aggiornando il codice. Anche se la configurazione della derivazione richiede un impegno iniziale, l'investimento di tempo risulta sicuramente proficuo quando i requisiti sono destinati a cambiare o si prevede di realizzare più varianti del prodotto.  
  
## <a name="generating-the-code-of-your-application-from-a-model"></a>Generazione del codice dell'applicazione da un modello  
 Il modo più semplice per generare codice consiste nell'usare modelli di testo. È possibile generare codice nello stesso [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che contiene il modello di soluzione. Per altre informazioni, vedere:  
  
- [Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
- [Generare file da un modello UML](../modeling/generate-files-from-a-uml-model.md)  
  
- [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)  
  
  Questo metodo può essere facilmente applicato in modo incrementale. Partire da un'applicazione che funziona solo per un caso specifico e sceglierne alcune parti da variare rispetto al modello. Rinominare i file di origine di queste parti in modo che diventino file modello di testo (con estensione tt). A questo punto, i file cs di origine verranno automaticamente generati dai file modello e l'applicazione funzionerà nel modo consueto.  
  
  Sarà quindi possibile sostituire una parte del codice con un'espressione del modello di testo che legge il modello e genera la parte sostituita del file di origine. Affinché sia l'applicazione possa essere rieseguita e funzioni come di consueto, è necessario che almeno un valore del modello generi il codice sorgente originale. Dopo avere testato valori del modello differenti, è possibile continuare a inserire espressioni del modello in un'altra parte del codice.  
  
  Grazie a questo metodo incrementale, la generazione di codice risulta generalmente un approccio a basso rischio. Il livello di prestazioni garantito dalle applicazioni risultanti è in genere pressoché simile a quello della versione scritta manualmente.  
  
  Tuttavia, se si parte da un'applicazione esistente, potrebbe rendersi necessaria un'attività di refactoring non indifferente per separare i diversi comportamenti regolati dal modello in modo che possano essere variati in modo indipendente. Si consiglia di valutare questo aspetto dell'applicazione quando si effettua una stima del costo del progetto.  
  
## <a name="configuring-your-application-from-a-model"></a>Configurazione dell'applicazione in base a un modello  
 Se si vuole variare il comportamento dell'applicazione in fase di esecuzione, non è possibile usare la generazione di codice, poiché genera il codice sorgente prima che venga compilata l'applicazione. Al contrario, è possibile progettare l'applicazione in modo che legga il modello UML o DSL e che il comportamento vari di conseguenza. Per altre informazioni, vedere:  
  
- [Leggere un modello UML nel codice programma](../modeling/read-a-uml-model-in-program-code.md)  
  
- [Procedura: Aprire un modello da file nel codice del programma](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
  Questo metodo può anche essere applicato in modo incrementale, ma ciò comporta maggiore impegno nelle fasi iniziali. Sarà infatti necessario scrivere il codice che leggerà il modello e configurare un framework che ne renda i valori accessibili alle parti variabili. La generalizzazione delle parti variabili è un approccio più dispendioso rispetto alla generazione di codice.  
  
  Il livello di prestazioni garantito da un'applicazione generica è solitamente inferiore a quello delle controparti specifiche.  Se le prestazioni sono cruciali, è opportuno che il piano del progetto includa una valutazione di questo rischio.  
  
## <a name="developing-a-derived-application"></a>Sviluppo di un'applicazione derivata  
 Per lo sviluppo di un'applicazione derivata potranno rivelarsi utili le linee guida descritte di seguito.  
  
- **Avviare specifico e quindi generalizzare.** Scrivere prima una versione specifica dell'applicazione. Questa versione dovrebbe funzionare in un set di condizioni specifico. Dopo avere verificato il corretto funzionamento dell'applicazione, sarà possibile derivarne una parte da un modello. Estendere gradualmente le parti derivate.  
  
     Ad esempio, progettare un sito Web che include un set specifico di pagine Web prima di progettare un'applicazione Web che presenta pagine definite in un modello.  
  
- **Modellare gli aspetti variabili.** Identificare gli aspetti che varieranno tra una distribuzione e l'altra o nel tempo con il mutare dei requisiti. Questi sono gli aspetti che devono essere derivati da un modello.  
  
     Ad esempio, se il set di pagine Web e dei relativi collegamenti cambia, ma lo stile e il formato delle pagine rimangono gli stessi, sarà necessario che il modello descriva i collegamenti, ma non il formato delle pagine.  
  
- **Separare le problematiche.** Se gli aspetti variabili possono essere suddivisi in aree indipendenti, usare modelli separati per ogni area. Usando ModelBus, è possibile definire operazioni che influiscono su entrambi modelli e i vincoli reciproci.  
  
     Ad esempio, usare un modello per definire la navigazione delle pagine Web e un modello differente per definire il layout delle pagine. Per altre informazioni, vedere [integrare i modelli UML con altri modelli e strumenti](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
- **Il requisito, non sulla soluzione del modello.** Progettare il modello DSL o adattare il modello UML in modo che descriva i requisiti dell'utente. Non progettare invece la notazione in base agli aspetti variabili dell'implementazione.  
  
     Ad esempio, il modello della navigazione Web deve rappresentare le pagine Web e i reciproci collegamenti ipertestuali. Il modello della navigazione Web non deve rappresentare frammenti di HTML o classi dell'applicazione.  
  
- **Generazione e interpretazione?** Se i requisiti per una particolare distribuzione sono destinati a cambiare di rado, generare il codice programma dal modello. Se è possibile che i requisiti cambino di frequente o che ne coesistano più varianti nella stessa distribuzione, scrivere l'applicazione in modo che possa leggere e interpretare un modello.  
  
     Ad esempio, se si usa il modello del sito Web per sviluppare una serie di siti Web differenti e installati separatamente, sarà necessario generare il codice del sito dal modello.  Se, invece, si usa il modello per controllare un sito che cambia quotidianamente, sarà preferibile scrivere un server Web che legga il modello e che presenti il sito conformemente a tale modello.  
  
- **UML o DSL?** Prendere in considerazione la creazione della notazione dei modelli tramite stereotipi per estendere UML. Definire un modello DSL se non si ha un diagramma UML appropriato. Evitare tuttavia di alterare la semantica standard di UML.  
  
     Ad esempio, un diagramma classi UML è una raccolta di caselle e di frecce. Con questa notazione si può, teoricamente, definire qualsiasi elemento. L'uso del diagramma classi è tuttavia consigliato solo quando si descrive un set di tipi. Ad esempio, è possibile adattare diagrammi classi per descrivere tipi differenti di pagine Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Generare file da un modello UML](../modeling/generate-files-from-a-uml-model.md)   
 [Leggere un modello UML nel codice programma](../modeling/read-a-uml-model-in-program-code.md)   
 [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Procedura: Aprire un modello da File nel codice programma](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
