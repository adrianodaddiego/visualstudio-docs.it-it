---
title: Novità di Live Unit Testing in Visual Studio 2017
titleSuffix: ''
ms.date: 10/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
- Live Unit Testing What's New
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 96ac53900806cc37e215342573f998be995289f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62785884"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Novità di Live Unit Testing per Visual Studio 2017

In questo argomento vengono elencate le nuove funzionalità aggiunte a Live Unit Testing in ogni versione di Visual Studio a partire da Visual Studio 2017 versione 15.3. Per una panoramica di come usare Live Unit Testing, vedere [Live Unit Testing con Visual Studio](live-unit-testing.md).

## <a name="version-154"></a>Versione 15.4

A partire da Visual Studio 2017 versione 15.4, Live Unit Testing include miglioramenti in numerose aree:

- **Individuazione migliorata**. Per gli utenti che non conoscono la funzionalità Live Unit Testing, l'IDE di Visual Studio visualizza una barra color oro che cita Live Unit Testing ogni volta che l'utente apre una soluzione che include unit test ma senza che Live Unit Testing sia abilitato. Le informazioni presentate nella barra color oro offrono all'utente altri dettagli su Live Unit Testing e su come abilitarlo. La barra color oro consente di visualizzare informazioni anche quando i prerequisiti di Live Unit Testing non vengono soddisfatti. Sono inclusi:

   - Mancano gli adattatori di test.
   - Sono presenti versioni precedenti degli adattatori di test.
   - È necessario un ripristino dei pacchetti NuGet a cui fa riferimento la soluzione.

- **Integrazione con le notifiche del centro attività**. L'IDE di Visual Studio consente ora di visualizzare una notifica dell'elaborazione in background di Live Unit Testing nel centro attività, in modo che gli utenti possano stabilire facilmente ciò che accade quando Live Unit Testing è abilitato. Ciò contribuisce a risolvere il problema chiave dell'avvio di Live Unit Testing in una soluzione di grandi dimensioni. In precedenza, per alcuni minuti precedenti la visualizzazione delle icone di code coverage, gli utenti non potevano stabilire se Live Unit Testing fosse effettivamente abilitato e in esecuzione. Ora non è più così.

- **Supporto per la versione 1 del framework MSTest**: Live Unit Testing usa tre framework di testing unità di grande diffusione: xUnit, NUnit e MSTest. In precedenza, Live Unit Testing funzionava solo quando i progetti di unit test MSTest usavano la versione 2 di MSTest. A partire da Visual Studio 2017 versione 15.4, è supportata anche la versione 1 di MSTest.

- **Prestazioni e affidabilità**: Live Unit Testing ora assicura una migliore capacità di rilevamento di un eventuale caricamento incompleto dei progetti, evitando così l'arresto anomalo. I miglioramenti delle prestazioni di compilazione evitano anche che i progetti MSBuild vengano sottoposti a una nuova valutazione se il sistema rileva che non è stata apportata alcuna modifica al file di progetto.

- **Miglioramenti vari dell'interfaccia utente**:  l'opzione **Live Test Set-Include/Exclude** (Set Live Test-Includi/Escludi), disponibile se si fa clic con il pulsante destro del mouse, è stata rinominata in **Live Unit Testing Include/Exclude** (Includi/Escludi Live Unit Testing), perché creava confusione. L'opzione **Reset clean** (Reimposta e pulisci) nel menu **Test** > **Live Unit Testing** è stata rimossa. Ora è accessibile da **Strumenti** > **Opzioni** > **Live Unit Testing** selezionando **Delete Persisted Data** (Elimina dati persistenti).

## <a name="version-153"></a>Versione 15.3

A partire da Visual Studio 2017 versione 15.3, Live Unit Testing include miglioramenti in due aree principali:

- Supporto di .NET Core e.NET Standard. È possibile usare Live Unit Testing in soluzioni .NET Core e .NET Standard, scritte in C# o in Visual Basic.

- Miglioramenti delle prestazioni. Si noterà che le prestazioni sono notevolmente più veloci dopo la prima compilazione completa e la prima esecuzione di test in Live Unit Testing. Si percepirà anche un significativo miglioramento delle prestazioni durante gli avvii successivi di Live Unit Testing nella stessa soluzione. I dati generati da Live Unit Testing dovranno ora essere salvati in modo permanente e riusati il più possibile con i controlli aggiornati.

Oltre a queste aggiunte principali, Live Unit Testing include anche i miglioramenti seguenti:

- Una nuova icona becher viene ora usata per distinguere un metodo di test dai metodi regolari. Un'icona becher vuota indica che il test specifico non è incluso in Live Unit Testing.

- Quando si fa clic su un metodo di test dalla finestra a comparsa dell'interfaccia utente di un'icona di code coverage di un Live Unit Testing, è ora possibile eseguire il debug di test direttamente da questo contesto all'interno della finestra dell'interfaccia utente e senza dover uscire dall'editor del codice. Questa funzionalità è particolarmente utile quando si esamina un test non riuscito.

- In Strumenti/Opzioni/Live Unit Testing/Generale sono state aggiunte altre opzioni configurabili. È possibile limitare la memoria usata per Live Unit Testing. È possibile anche specificare il percorso del file relativo ai dati permanenti di Live Unit Testing per la soluzione aperta.

- Nella barra dei menu di Test/Live Unit Testing sono state aggiunte altre voci di menu. **Reset Clean** (Reimposta e pulisci), che elimina i dati permanenti e li rigenera. **Opzione**, che consente di passare a Strumenti/Opzioni/Live Unit Testing/Generale.

- È ora possibile usare gli attributi seguenti per specificare nel codice sorgente che si vuole escludere da Live Unit Testing determinati metodi di test:

   - Per xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
   - Per NUnit: `[Category("SkipWhenLiveUnitTesting")]`
   - Per MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Vedere anche

- [Introduzione di Live Unit Testing](live-unit-testing-intro.md)
- [Live Unit Testing con Visual Studio](live-unit-testing.md)
