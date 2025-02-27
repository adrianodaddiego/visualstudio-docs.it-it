---
title: Funzionalità IntelliTrace | Microsoft Docs
ms.date: 09/19/2018
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 762fc8a28b8c5b3f8729ecd728d12ed5cdbbafc6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846373"
---
# <a name="intellitrace-features-c-visual-basic-c"></a>Funzionalità IntelliTrace (C#, Visual Basic, C++)

È possibile utilizzare IntelliTrace per registrare gli eventi e il metodo chiama l'applicazione, che consente di esaminare il relativo stato (stack di chiamate e i valori delle variabili locali) in diversi momenti dell'esecuzione. È sufficiente avviare il debug come di consueto: IntelliTrace viene attivato per impostazione predefinita e si possono vedere le informazioni registrate da IntelliTrace nella nuova finestra **Strumenti di diagnostica** nella scheda **Eventi**. Selezionare un evento e fare clic su **Attiva debug cronologico** per visualizzare gli stack di chiamate e le variabili locali registrati per questo evento.

Per una descrizione dettagliata, vedere [procedura dettagliata: Utilizzo di IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition ma non le edizioni Professional o Community.

Per verificare che IntelliTrace è abilitato, aprire la pagina delle opzioni **Strumenti > Opzioni > IntelliTrace**. **Abilita IntelliTrace** deve essere selezionata per impostazione predefinita.

> [!NOTE]
> L'ambito di tutte le impostazioni nella pagina delle opzioni di **IntelliTrace** è Visual Studio nel suo insieme, non i singoli progetti o le singole soluzioni. Una modifica di queste impostazioni si applica a tutte le istanze di Visual Studio, le sessioni di debug tutti e tutti i progetti o soluzioni.

## <a name="ChooseEvents"></a> Scegliere gli eventi registrati da IntelliTrace (C#, Visual Basic)

È possibile attivare o disattivare la registrazione di eventi di IntelliTrace specifici.

Se il debug è in corso, interromperlo. Passare a **strumenti > Opzioni > IntelliTrace > eventi IntelliTrace**. Scegliere gli eventi di IntelliTrace per registrare.

## <a name="Snapshots"></a> Raccogliere le istantanee (C#, Visual Basic, C++)

Questo non è abilitato per impostazione predefinita, ma IntelliTrace è possibile acquisire snapshot dell'applicazione in tutti gli eventi di passaggio del debugger e del punto di interruzione ed è possibile visualizzare questi snapshot in una sessione di debug cronologica. Uno snapshot offre una visualizzazione dello stato dell'applicazione completo. Per abilitare l'acquisizione di snapshot, passare a **strumenti > Opzioni > IntelliTrace > Generale**e selezionare **istantanee di IntelliTrace (gestite e native)**. Per altre informazioni, vedere [Visualizzare lo stato precedente dell'applicazione con IntelliTrace](../debugger/view-historical-application-state.md)

Gli snapshot sono disponibili in Visual Studio Enterprise 2017 versione 15.5 e versioni successive e richiede Windows 10 Anniversary Update o versione successiva.  Per le app .NET Core e ASP.NET Core, è necessario Visual Studio Enterprise 2017 versione 15.7. Per le app native destinate a Windows, Visual Studio Enterprise 2017 versione 15.9 Preview 2 è obbligatorio.

## <a name="GoingFurther"></a> Raccogli eventi di IntelliTrace e informazioni di chiamata (C#, Visual Basic)

Questo non è abilitato per impostazione predefinita, ma IntelliTrace è in grado di registrare le chiamate ai metodi insieme agli eventi. Per abilitare la raccolta di chiamate passano al metodo **strumenti > Opzioni > IntelliTrace > Generale**e selezionare **eventi IntelliTrace e informazioni (solo gestite) di chiamata**.

Informazioni sulle chiamate non è attualmente disponibile per le app .NET Core e ASP.NET Core.

In tal modo è possibile visualizzare la cronologia dello stack di chiamate e scorrere in avanti e indietro le chiamate nel codice. IntelliTrace registra i dati, ad esempio nomi delle funzioni, punti di ingresso e uscita delle funzioni e alcuni valori di parametri e valori restituiti.

> [!TIP]
> Questa opzione non è abilitata per impostazione predefinita in quanto tale operazione comporta un notevole sovraccarico. Non solo ha IntelliTrace intercettare ogni chiamata al metodo che rende l'applicazione, ma dispone anche di gestire un set di dati molto maggiore se si desidera visualizzare su schermo o renderli persistenti su disco.
>
> È possibile ridurre l'overhead delle prestazioni limitando l'elenco degli eventi che registra IntelliTrace e mantenendo il numero di moduli si raccolgono al minimo. Per altre informazioni, vedere [Controllare quante informazioni di chiamata vengono registrate da IntelliTrace](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Usare la barra di navigazione

È possibile utilizzare la barra di navigazione viene visualizzato a sinistra della finestra del codice. Se non viene visualizzata la barra di navigazione, passare a **Strumenti > Opzioni > IntelliTrace > Avanzate** e selezionare **Visualizza la barra di navigazione in modalità debug**.

La barra di navigazione consente di spostarsi avanti e indietro tra chiamate ai metodi e gli eventi in modalità di debug cronologico. Per altre informazioni sul debug cronologico, vedere [Debug cronologico](../debugger/historical-debugging.md). Dispone di una serie di comandi:

|||
|-|-|
|**Imposta contesto debugger**|Consente di impostare il contesto di debug sull'intervallo di tempo della chiamata dove viene visualizzato.<br /><br /> Questa icona compare solo sullo stack di chiamate corrente.|
|**Torna al sito di chiamata**|Spostare il puntatore e il contesto di debug indietro nel momento in cui è stata chiamata la funzione corrente.<br /><br /> Se si è in modalità debug attivo, questo comando attiva il debug cronologico. Se si passa nuovamente all'interruzione dell'esecuzione originale, il debug cronologico è disattivato e Live debug è attivato.|
|**Passa a chiamata o a evento IntelliTrace precedente**|Spostare il puntatore e il contesto di debug indietro nel tempo all'evento o alla chiamata precedente.<br /><br /> Se si è in modalità debug attivo, questo comando attiva il debug cronologico.|
|**Entra**|Passaggio alla funzione attualmente selezionato.<br /><br /> Questo comando è disponibile solo quando si esegue il debug con IntelliTrace.|
|**Passa a chiamata o a evento IntelliTrace successivo**|Spostare il puntatore e il contesto di debug avanti nel tempo nella chiamata o nell’evento successivo per cui esistono dati IntelliTrace.<br /><br /> Questo comando è disponibile solo quando si esegue il debug con IntelliTrace.|
|**Passa alla modalità attiva**|Torna alla modalità debug attivo|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>Cerca una riga o metodo in IntelliTrace

È possibile cercare i metodi solo quando è state abilitate informazioni sulla chiamata di metodo. È possibile cercare la cronologia di IntelliTrace per un metodo o una riga specifica. Durante l'esecuzione del debugger viene interrotto, fare clic con il pulsante destro del mouse all'interno del corpo della funzione per visualizzare il menu di scelta rapida e fare clic su **Cerca questa riga in IntelliTrace** o **Cerca questo metodo in IntelliTrace**.

### <a name="ControlCallData"></a> Controllare quante informazioni di chiamata vengono registrate da IntelliTrace

Per impostazione predefinita IntelliTrace registra le informazioni per tutti i moduli utilizzati nella soluzione. È possibile disporre delle registrazioni delle informazioni sulle chiamate di IntelliTrace solo per i moduli di interesse. In **Strumenti > Opzioni > IntelliTrace > Moduli** è possibile specificare i moduli da includere o escludere da IntelliTrace. IntelliTrace verrà raccolti solo gli eventi originati da moduli che è stato specificato e le chiamate al metodo che si sono verificati all'interno di moduli che si è interessati.

Per aggiungere più moduli, utilizzare il carattere jolly * all'inizio o alla fine della stringa. Per i nomi dei moduli, utilizzare nomi di file e non nomi di assembly. I percorsi file non sono accettati.

Provare a ridurre al minimo il numero di moduli. È possibile ottenere prestazioni migliori perché non ci sono meno dati da raccogliere. Si ottiene anche meno rumore nell'interfaccia utente perché non ci sono meno dati passino attraverso.

## <a name="SaveSession"></a> Salvare i dati IntelliTrace in file (C#, Visual Basic, C++)

È possibile salvare i dati raccolti da IntelliTrace passando a **Debug > IntelliTrace > Salva la sessione di IntelliTrace** mentre si esegue il debug e l'applicazione è in uno stato di interruzione. La voce di menu è disabilitata e non sarà in grado di salvare i dati che raccolti da IntelliTrace se l'applicazione è ancora in esecuzione o se si interrompe il debug.

È possibile configurare IntelliTrace per salvare automaticamente in un file passando a **Strumenti > Opzioni > IntelliTrace > Avanzate** e selezionando **Archivia le registrazioni IntelliTrace nella directory**. È inoltre possibile configurare una dimensione fissa per il file generato, provocando IntelliTrace per sovrascrivere i dati meno recenti quando si esaurisce lo spazio. Visual Studio crea due file per ogni sessione di IntelliTrace quando vengono salvati automaticamente e il processo di hosting di Visual Studio (vshost.exe) è attivato.

> [!TIP]
> Per risparmiare spazio su disco, disattivare il salvataggio dei file automaticamente quando non sono più necessari. Tutti i file esistenti non verranno eliminati. È sempre possibile salvare il file su richiesta dal menu di scelta rapida.

Quando si salvano i dati di IntelliTrace per file, è possibile ottenere un file con estensione iTrace per ogni processo IntelliTrace raccolti da. È quindi possibile aprire il file con estensione iTrace in Visual Studio passando a **File > Apri > File** e selezionando il file con estensione iTrace dalla finestra di dialogo Apri file. Per altre informazioni, vedere [Uso dei dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Blog

[IntelliTrace in Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)

[Procedura dettagliata del debug attivo tramite IntelliTrace in Visual Studio 2015 (Editor di testo)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[Procedura dettagliata del debug attivo tramite IntelliTrace in Visual Studio 2015 (Social Club)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[IntelliTrace in Visual Studio Enterprise 2015 ora supporta!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[Raccogliere i dati da un servizio windows utilizzando l'agente di raccolta autonomo IntelliTrace](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[Modifica il piano di raccolta IntelliTrace](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan)

[TraceSource personalizzato e il debug mediante IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)

[Agente di raccolta autonomo IntelliTrace e pool di applicazioni in esecuzione in account di Active Directory](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>Forum

[Debugger di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)

## <a name="videos"></a>Video

[IntelliTrace esperienza](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Debug cronologico con IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
