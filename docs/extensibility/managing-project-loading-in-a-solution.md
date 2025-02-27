---
title: La gestione del caricamento di progetti in una soluzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a80430c4a5dcf5526445275b89fa2da7f02f5529
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340597"
---
# <a name="manage-project-loading-in-a-solution"></a>Caricamento di progetti in una soluzione di gestione
Soluzioni di Visual Studio possono contenere un numero elevato di progetti. Il comportamento di Visual Studio predefinito consiste nel caricare tutti i progetti in una soluzione al momento che la soluzione è aperta e per non consentire all'utente di accedere a nessuno dei progetti finché non termina il caricamento di tutti gli elementi. Quando il processo di caricamento di progetti a lungo termine più di due minuti, viene visualizzato un indicatore di stato che mostra il numero totale di progetti e il numero di progetti caricati. L'utente può scaricare i progetti mentre si lavora in una soluzione con più progetti, ma questa procedura presenta alcuni svantaggi: i progetti non caricati non vengono compilati come parte di un comando Ricompila soluzione e le descrizioni di IntelliSense dei tipi e membri di chiusi i progetti non vengono visualizzati.

 Gli sviluppatori possono ridurre i tempi di caricamento delle soluzioni e gestire il caricamento di comportamento mediante la creazione di un caricamento della soluzione responsabile del progetto. Il gestore di caricamento della soluzione può assicurarsi che i progetti vengono caricati prima di avviare una compilazione in background, ritardare il caricamento in background fino al completamento di altre attività in background ed eseguire altre attività di gestione di caricamento progetto.

## <a name="create-a-solution-load-manager"></a>Creare un caricamento della soluzione di gestione
 Gli sviluppatori possono creare un caricamento della soluzione gestione implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e Visual Studio che informa che il gestore di caricamento della soluzione è attivo.

### <a name="activate-a-solution-load-manager"></a>Attivare un gestore di caricamento della soluzione
 Visual Studio consente un solo gestore di caricamento di soluzioni in un determinato momento, pertanto è necessario informare Visual Studio quando si desidera attivare il caricamento della soluzione gestione. Se un secondo gestore di caricamento di soluzioni viene attivato in un secondo momento, la gestione del carico di soluzione verrà disconnesso.

 È necessario ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> del servizio e impostare il [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) proprietà:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> viene chiamato quando Visual Studio viene arrestato o quando un altro pacchetto diventa il gestore di caricamento di soluzione attiva chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con il [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) proprietà.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie per diversi tipi di gestore di caricamento della soluzione
 È possibile implementare i responsabili di caricamento di soluzioni in modi diversi, a seconda dei tipi di soluzioni che sono disponibili solo per la gestione.

 Se il gestore di caricamento della soluzione è destinato a gestire il caricamento in generale della soluzione, può essere implementata come parte di un pacchetto VSPackage. Il pacchetto deve essere impostato su autoload aggiungendo il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> nel pacchetto VSPackage con un valore di <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Il gestore di caricamento della soluzione può quindi essere attivato nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (metodo).

> [!NOTE]
> Per altre informazioni sui pacchetti di caricamento automatico, vedere [caricamento di VSPackage](../extensibility/loading-vspackages.md).

 Poiché Visual Studio riconosce solo i manager di carico soluzione ultimo da attivare, sempre gestori carico soluzione generale dovrebbero rilevare se è una gestione del carico esistente prima di attivare autonomamente. Se il chiamante `GetProperty()` sul servizio per la soluzione [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) restituisce `null`, non vi è alcun gestore di caricamento di soluzione attiva. Se non viene restituito null, controllare se l'oggetto è quello utilizzato per la gestione del carico di soluzione.

 Se il gestore di caricamento della soluzione è destinato a gestire solo alcuni tipi di soluzione, il pacchetto VSPackage può sottoscrivere gli eventi di caricamento della soluzione (chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) e usare il gestore eventi per <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> per attivare il gestore di caricamento della soluzione.

 Se il gestore di caricamento della soluzione è destinato a gestire solo le soluzioni specifiche, le informazioni di attivazione possono essere reso persistente come parte del file della soluzione chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> per la sezione della soluzione precedente.

 I responsabili di carico specifica soluzione verrà disattivato se stessi nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> gestore eventi, in ordine non sarà in conflitto con altri gestori di caricamento della soluzione.

 Se è necessario un gestore di caricamento della soluzione solo per rendere persistenti le proprietà di caricamento di progetti globale (ad esempio, proprietà impostate in una pagina Opzioni), è possibile attivare la gestione del carico di soluzione nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> gestore eventi, mantenere l'impostazione di proprietà della soluzione, quindi disattivare il gestore di caricamento della soluzione.

## <a name="handle-solution-load-events"></a>Gestire gli eventi di caricamento della soluzione
 Per sottoscrivere gli eventi di caricamento della soluzione, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando si attiva la gestione del carico di soluzione. Se si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, è possibile rispondere agli eventi che riguardano il caricamento delle proprietà del progetto diverso.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Questo evento viene generato prima dell'apertura di una soluzione.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Questo evento viene generato dopo che la soluzione è stata caricata completamente, ma prima di background viene eseguito nuovamente il caricamento del progetto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Questo evento viene generato dopo che una soluzione è stata caricata inizialmente completamente, presenza o meno un gestore di caricamento della soluzione. Inoltre viene generato dopo il caricamento in background o richiesta caricato ogni volta che la soluzione diventa completamente caricata. Allo stesso tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> viene riattivato.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Questo evento viene generato prima il caricamento di un progetto (o i progetti). Per garantire che gli altri processi in background vengano completati prima che i progetti vengono caricati, impostare `pfShouldDelayLoadToNextIdle` al **true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Questo evento viene generato quando un batch di progetti sta per essere caricato. Se `fIsBackgroundIdleBatch` è true, i progetti devono essere caricati in background; se `fIsBackgroundIdleBatch` è false, i progetti sono da caricare in modo sincrono in seguito a una richiesta dell'utente, ad esempio se l'utente espande un progetto in Esplora soluzioni in sospeso. È possibile gestire questo evento per eseguire operazioni costose che in caso contrario, dovrà essere eseguita in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Questo evento viene generato dopo il caricamento di un batch di progetti.

## <a name="detect-and-manage-solution-and-project-loading"></a>Rilevare e gestire il caricamento di progetti e soluzioni
 Per rilevare lo stato di caricamento di progetti e soluzioni, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con i valori seguenti:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` restituisce `true` se la soluzione e tutti i relativi progetti vengono caricati, in caso contrario `false`.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` restituisce `true` se un batch di progetti attualmente caricato in background, in caso contrario `false`.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` restituisce `true` se un batch di progetti attualmente caricato in modo sincrono a causa di un comando dell'utente o di altro tipo di caricamento esplicito, in caso contrario `false`.

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` restituisce `true` se la soluzione attualmente viene chiuso, in caso contrario `false`.

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` restituisce `true` se viene aperta una soluzione attualmente in corso, in caso contrario `false`.

È inoltre possibile garantire che i progetti e soluzioni vengono caricate chiamando uno dei metodi seguenti:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: chiamata di questo metodo forza i progetti in una soluzione per caricare prima di eseguire il metodo restituisce.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: chiamata di questo metodo forza i progetti in `guidProject` caricare prima il metodo restituisce.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: chiamata di questo metodo forza il progetto in `guidProjectID` caricare prima il metodo restituisce.
