---
title: Eseguire il debug di progetti di Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b48335ccaa8bd21cf9f6e108d043ecf706903bb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441878"
---
# <a name="debug-office-projects"></a>Eseguire il debug di progetti di Office
  È possibile eseguire il debug di progetti di Office usando gli stessi strumenti di Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] che si usano per altri progetti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Le funzionalità del debugger di[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ad esempio la possibilità di inserire punti di interruzione e visualizzare le variabili nella finestra **Variabili locali** , sono disponibili anche quando si esegue il debug di progetti di Office. Per altre informazioni sulle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] strumenti di debug, vedere [eseguire il Debug in Visual Studio](../debugger/debugging-in-visual-studio.md).

> [!TIP]
> Per semplificare il debug, chiudere tutte le istanze dell'applicazione di Office aperte, prima di generare ed eseguire il debug.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

> [!NOTE]
> Se ti interessa sviluppare soluzioni che estendono l'esperienza di Office attraverso [piattaforme multiple](https://dev.office.com/add-in-availability)? Consultare la nuova [modello di componenti aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office con footprint ridotto rispetto alle soluzioni e componenti aggiuntivi VSTO e si possono essere compilate usando praticamente qualsiasi tecnologia, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.

## <a name="start-and-stop-the-debugger"></a>Avviare e arrestare il debugger
 È possibile avviare il debug di un progetto di Office come si avvia il debug di altri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proietta; ad esempio, è possibile premere la **F5** chiave. Quando si avvia il debug di un progetto di componente aggiuntivo VSTO, viene avviato un nuovo processo per l'applicazione di Office di destinazione e il componente aggiuntivo VSTO viene caricato.

 Quando si avvia il debug di un progetto a livello di documento, il documento o la cartella di lavoro viene aperta in un nuovo processo di Word o Excel.

 Quando si arresta il debugger, il debugger interrompe improvvisamente il processo di applicazione o viene disconnesso se il debugger è impostato per disconnettersi. Tutti gli altri documenti aperti nel processo dell'applicazione di Office terminata vengono chiusi senza avviso e le modifiche non salvate vengono perse. Questo potrebbe includere tutti i documenti o le cartelle di lavoro che vengono aperti durante l'esecuzione del debugger.

 In genere, si consiglia di disconnettersi dal processo prima di arrestare il debugger in modo da poter chiudere l'applicazione di Office in modo normale. È anche possibile disconnettersi dal processo per prima cosa se si desidera usare un documento o un foglio di lavoro aperto dopo l'arresto del debugger.

 Se si esegue il debug di una personalizzazione a livello di documento per Word, arrestando ripetutamente il debugger e causando la chiusura improvvisa di Word, si può danneggiare il modello Normale. In questo caso, è possibile eliminare il modello Normale danneggiato che verrà ricreato automaticamente alla successiva apertura di Word. Tuttavia, non vengono ricreate le macro che sono state archiviate nel modello Normale.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Eseguire il debug dei componenti aggiuntivi VSTO di Office 2013 con Office 2013 o Office 2016
 Se si usa Visual Studio 2015 e si dispone di entrambe le versioni di Office installate side-by-side, Visual Studio avvia Office 2016. Se si usa Visual Studio 2013, Visual Studio avvia Office 2013.

 Per eseguire il debug del componente aggiuntivo VSTO con una versione di Office diversa (2013 o 2016), aprire **Creazione progetti**e scegliere il pulsante di opzione **Avvia programma esterno** nella scheda **Debug** . Quindi, passare al percorso dell'eseguibile dell'applicazione di Office appropriata.

## <a name="f10-and-f11-behavior"></a>Comportamento di F10 e F11
 Quando si avvia il debug di un progetto di Office **F10** e **F11** non è lo stesso comportamento quando si avvia il debug di altri progetti di Visual Basic o c#. Nei progetti Visual Basic o C#, il debugger si arresta sulla funzione principale. Nei progetti di Office, Visual Studio non dispone di controllo sulla funzione principale dell'applicazione di Office. Tuttavia, durante il debug **F10** e **F11** hanno le stesse funzioni come i progetti Visual Basic e c#.

## <a name="display-exceptions"></a>Visualizzare le eccezioni
 A causa del modo con cui il codice gestito interagisce con il codice non gestito, in Visual Studio non vengono visualizzati gli errori generati dalle applicazioni di Microsoft Office. Ad esempio, se un componente aggiuntivo in VSTO creati usando gli strumenti di sviluppo per Office in Visual Studio genera un'eccezione, l'applicazione Microsoft Office continua senza visualizzare alcun errore. Per visualizzare questi errori, impostare il debugger in modo che si interrompa in caso di eccezioni di Common Language Runtime. Per altre informazioni, vedere [gestire le eccezioni con il debugger](../debugger/managing-exceptions-with-the-debugger.md).

 Se si imposta il debugger per interrompere l'esecuzione in caso di eccezioni di Common Language Runtime, tutte le eccezioni a questo punto verranno interrotte nel debugger, incluse quelle gestite e alcune eccezioni first-chance del runtime stesso che potrebbero non essere rilevanti per il progetto. Gli errori che fanno riferimento a msosec non trovato, vengono visualizzati in ogni progetto, ma è possibile ignorarli. Queste eccezioni msosec non avranno effetto sulla soluzione.

 È inoltre possibile usare le istruzioni **Try...Catch** sui metodi per raccogliere le eccezioni.

 Per impostazione predefinita, in Visual Studio non vengono visualizzati gli errori di debug Just-In-Time per i progetti di Office. Tuttavia, è possibile abilitare questa funzionalità in modo da poter visualizzare gli errori che vengono generati. Per altre informazioni, vedere [debug in Visual Studio Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md).

## <a name="command-line-arguments"></a>Argomenti della riga di comando
 Se il **azione di avvio** nel **Debug** pagina delle proprietà è impostata su **Avvia progetto**, Visual Studio Usa gli argomenti della riga di comando durante il debug del progetto, anche se si dispone specificare gli argomenti della riga di comando come opzioni di avvio. Se si desidera utilizzare gli argomenti della riga di comando quando si avvia il debug, è necessario selezionare una **azione di avvio** diverso da **Avvia progetto**.

## <a name="source-control"></a>Controllo del codice sorgente
 Le proprietà del debug non sono condivise tra più utenti sotto il controllo del codice sorgente. I progetti Visual Basic e C# archiviano le proprietà di debug in un file specifico dell'utente (*NomeProgetto*.vbproj.user o *NomeProgetto*.csproj.user) e questo file non è incluso nel controllo del codice sorgente. Se più di una persona sta eseguendo il debug, è necessario che ciascuna immetta manualmente le proprietà di debug.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Eseguire il debug di set di dati memorizzati nella cache in un progetto a livello di documento
 Ogni volta che si compila un progetto, il dataset viene svuotato e ricreato. Se si desidera eseguire il debug di un dataset memorizzato nella cache, è necessario aprire il documento all'esterno di Visual Studio e quindi connettere il debugger.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Debug progetti documento di Word basati sul documento di Word 97-2003 (*. doc) formato
 Eseguire il debug di un progetto documento di Word basato sul documento di Word 97-2003 ( */* doc *) formato, è necessario aggiungere la cartella del progetto all'elenco delle cartelle attendibili. Per altre informazioni su come eseguire questa operazione, vedere [concedere l'attendibilità a documenti](../vsto/granting-trust-to-documents.md).

## <a name="debug-disabled-add-ins"></a>Debug disabilitato componenti aggiuntivi
 Le applicazioni di Microsoft Office possono disabilitare i componenti aggiuntivi VSTO che si comportano in modo imprevisto. Un'applicazione di Microsoft Office disabilita i componenti aggiuntivi VSTO per impedire che il codice con errori venga caricato ogni volta che viene avviata l'applicazione. Tuttavia, è anche facile causare un comportamento imprevisto durante il normale debug. Per informazioni su come abilitare nuovamente i componenti aggiuntivi VSTO, vedere [come: Riabilitare un VSTO Add-in è stato disabilitato](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).

 Esistono due tipi di disabilitazione usati dalle applicazioni di Microsoft Office per i componenti aggiuntivi VSTO: disabilitazione che causa la chiusura imprevista dell'applicazione e disabilitazione che non causa la chiusura imprevista dell'applicazione.

### <a name="hard-disabling"></a>La disabilitazione hard
 La disabilitazione hard può verificarsi quando un componente aggiuntivo VSTO causa la chiusura imprevista dell'applicazione. Si potrebbe verificare anche nel computer di sviluppo se si arresta il debugger durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> nel componente aggiuntivo VSTO. Dopo che un componente aggiuntivo VSTO viene disabilitato a livello hard, viene visualizzata la **elementi disabilitati** elenco nell'applicazione.

 Se un'applicazione di Office rigida disabilita un componente aggiuntivo in VSTO creati usando gli strumenti di sviluppo per Office in Visual Studio, l'applicazione Disabilita solo il VSTO Add-in ha provocato l'errore. Gli altri componenti aggiuntivi VSTO creati usando gli strumenti di sviluppo di Office in Visual Studio per l'applicazione di Office continueranno il caricamento.

### <a name="soft-disabling"></a>La disabilitazione soft
 La disabilitazione di tipo "soft" può verificarsi quando un componente aggiuntivo VSTO genera un errore che non causa la chiusura imprevista dell'applicazione. Ad esempio, un'applicazione potrebbe eseguire la disabilitazione di tipo "soft" di un componente aggiuntivo VSTO se viene generata un'eccezione non gestita durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> . Dopo che un componente aggiuntivo VSTO viene disabilitato, viene visualizzata la **componenti aggiuntivi di applicazioni inattivi** elenco nell'applicazione e l'applicazione modifica il valore della **LoadBehavior** voce del Registro di sistema per il componente aggiuntivo VSTO per indicare che viene scaricato. Per altre informazioni sul **LoadBehavior** voce del Registro di sistema, vedere [voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Risolvere i problemi di installazione utilizzando il Visualizzatore eventi
 Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] scrive i messaggi nel Visualizzatore eventi di Windows per tutte le eccezioni generate quando si installano o si disinstallano soluzioni Office. È possibile usare questi messaggi per risolvere i problemi di installazione e distribuzione.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Risolvere i problemi di avvio utilizzando un log file e messaggi di errore
 Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] può scrivere tutti gli errori che si verificano durante l'avvio in un file di log o visualizzare ciascun errore in una finestra di messaggio. Per impostazione predefinita, le opzioni sono disattivate. È possibile attivare le opzioni creando le variabili di ambiente.

 Per visualizzare ogni errore in una finestra di messaggio, creare una variabile di ambiente denominata `VSTO_SUPPRESSDISPLAYALERTS` e impostarla su 0 (zero). È possibile eliminare i messaggi eliminando la variabile di ambiente o impostandola su 1 (uno).

 Per scrivere gli errori in un file di log, creare una variabile di ambiente denominata `VSTO_LOGALERTS` e impostarla su 1 (uno). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea il file di log nella cartella che contiene il manifesto della distribuzione per il componente aggiuntivo VSTO o nella cartella che contiene il documento o la cartella di lavoro associata alla personalizzazione. Se il problema persiste, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] consente di creare il file di log in locale *% TEMP %* cartella. Per i componenti aggiuntivi VSTO a livello di applicazione, il nome predefinito è *nome componente aggiuntivo*.vsto.log. Per i progetti a livello di documento, il nome del file di log è *nome documento*.*estensione*.log, ad esempio ExcelWorkbook1.xlsx.log. Per arrestare la registrazione degli errori, eliminare la variabile di ambiente o impostarla su 0 (zero).

## <a name="see-also"></a>Vedere anche

- [Creazione di soluzioni Office](../vsto/building-office-solutions.md)
- [Procedura: Riabilitare un VSTO Add-in è stato disabilitato](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)