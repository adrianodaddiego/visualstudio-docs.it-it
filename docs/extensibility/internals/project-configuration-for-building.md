---
title: Configurazione per la compilazione del progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd9464105d777c0d488175ad67e1481022caa2d1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328534"
---
# <a name="project-configuration-for-building"></a>Configurazione del progetto per la compilazione
L'elenco delle configurazioni di soluzione per una determinata soluzione viene gestito dalla finestra di dialogo configurazioni di soluzione.

 Un utente può creare altre configurazioni di soluzione, ognuno con un nome univoco. Se l'utente crea una nuova configurazione di soluzione, l'IDE per impostazione predefinita al nome di configurazione corrispondente in progetti o di Debug se non esiste alcun nome corrispondente. L'utente può modificare la selezione per soddisfare requisiti specifici, se necessario. L'unica eccezione a questo comportamento è quando il progetto supporta una configurazione che corrisponde al nome della nuova configurazione di soluzione. Si supponga, ad esempio, che una soluzione contiene Project1 e Project2. Project1 dispone di configurazioni di progetto MyConfig1 Debug e delle vendite al dettaglio. Project2 dispone di configurazioni di progetto MyConfig2 Debug e delle vendite al dettaglio.

 Se l'utente crea una nuova configurazione di soluzione denominata MyConfig2, Project1 associa la configurazione di Debug per la configurazione della soluzione per impostazione predefinita. Project2 associa anche la relativa configurazione MyConfig2 per la configurazione della soluzione per impostazione predefinita.

> [!NOTE]
> L'associazione è tra maiuscole e minuscole.

 Quando l'utente seleziona il **la selezione multipla** elemento nell'elenco a discesa configurazione, l'ambiente consente di visualizzare una finestra di dialogo che fornisce l'elenco delle configurazioni disponibili.

 ![Configurazioni multiple](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") configurazioni più

 All'interno di questa finestra di dialogo, l'utente può selezionare una o più configurazioni. Una volta selezionata, i valori delle proprietà visualizzati nella finestra di dialogo Pagine delle proprietà riflettono l'intersezione dei valori per le configurazioni selezionate.

 Visualizzare [configurazione della soluzione](../../extensibility/internals/solution-configuration.md) per informazioni sull'aggiunta e la ridenominazione delle configurazioni per i progetti e soluzioni.

 Dipendenze del progetto e ordine di compilazione sono indipendente dalla configurazione della soluzione: vale a dire, è possibile solo configurare albero una dipendenza per tutti i progetti nella soluzione. Facendo la soluzione o il progetto e scegliere il **dipendenze progetto** o **ordine compilazione progetto** opzione viene visualizzata la la **dipendenze del progetto** nella finestra di dialogo. Può anche essere aperta dal **progetto** menu.

 ![Dipendenze progetto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") dipendenze progetto

 Dipendenze del progetto determinano l'ordine in cui compilare i progetti. Utilizzare la scheda di ordine di compilazione nella finestra di dialogo per visualizzare l'ordine esatto in cui i progetti all'interno di una soluzione di compilazione e utilizzare la scheda dipendenze per modificare l'ordine di compilazione.

> [!NOTE]
> I progetti nell'elenco sono selezionate le caselle di controllo, ma vengono visualizzate in grigio sono state aggiunte dall'ambiente a causa delle dipendenze esplicite specificato dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfacce e non può essere modificato. Ad esempio, aggiungendo un riferimento al progetto da un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto a un altro progetto aggiunge automaticamente una dipendenza di compilazione che può essere rimossi solo eliminando il riferimento. Non è possibile selezionare progetti cui caselle di controllo siano deselezionate e vengono visualizzate in grigio perché questa operazione creerebbe un ciclo di dipendenze (ad esempio Project1 sarebbe dipende Project2 e Project2 sarebbe dipende Project1), che verrebbe stallo la compilazione.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i processi di compilazione includono la compilazione tipiche e le operazioni di collegamento che vengono richiamate con un singolo comando di compilazione. Due altri processi di compilazione possono anche essere supportate: un'operazione di pulizia per eliminare tutti gli elementi di output da una compilazione precedente e un controllo di aggiornamento per determinare se un elemento di output in una configurazione è stato modificato.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> gli oggetti restituiscono un oggetto corrispondente <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (restituito da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) per gestire i processi di compilazione. Per segnalare lo stato di un'operazione di compilazione in corso, le configurazioni di effettuano chiamate a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, un'interfaccia implementata dall'ambiente e qualsiasi altro oggetto interessato agli eventi di stato di compilazione.

 Una volta creato, le impostazioni di configurazione è utilizzabile per determinare se possono essere eseguiti sotto il controllo del debugger. Implementano le configurazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> per supportare il debug.

 Dopo aver implementato le dipendenze di progetto, è possibile modificare a livello di codice le dipendenze tramite il modello di automazione. Si chiama <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> nel modello di automazione. Non sono presenti interfacce a livello di API VSIP disponibili che consentono la manipolazione diretta di configurazioni di gestione di compilazione di soluzioni e le relative proprietà.

 Inoltre, è possibile fornire una griglia nella finestra di dipendenze del progetto. Per altre informazioni, vedere [griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la gestione della distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)