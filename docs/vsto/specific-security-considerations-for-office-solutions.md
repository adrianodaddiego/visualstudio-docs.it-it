---
title: Considerazioni sulla sicurezza specifiche per le soluzioni Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8a29c813a5217e68541fd076eadf62bf54710014
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436479"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Considerazioni sulla sicurezza specifiche per le soluzioni Office
  Le funzionalità di sicurezza fornite da Microsoft .NET Framework e Microsoft Office consentono di proteggere le soluzioni Office da potenziali rischi di sicurezza. Questo argomento illustra alcuni di tali rischi e fornisce suggerimenti utili su come proteggersi. Sono incluse anche informazioni su come le impostazioni di sicurezza di Microsoft Office possono influire sulle soluzioni Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Modifica dello scopo del codice attendibile in un nuovo documento dannoso
 Un utente malintenzionato potrebbe eseguire codice attendibile che dovrà essere usato per uno scopo specifico, ad esempio il download di informazioni personali per un'applicazione di occupazione, e riutilizzarlo in un altro documento, ad esempio un foglio di lavoro. Il codice non può stabilire che il documento originale non è in esecuzione e può introdurre altre minacce, ad esempio la divulgazione di informazioni personali o l'esecuzione di codice con privilegi di livello superiore, quando viene aperto da un altro utente. In alternativa, l'autore dell'attacco può modificare i dati nel foglio di lavoro in modo che, quando inviato a un utente, si comporta in modo imprevisto. Modificando i valori, le formule o le caratteristiche di presentazione di un foglio di lavoro collegato al codice, un utente malintenzionato può attaccare un altro utente inviando un file modificato. La modifica dei valori nel foglio di lavoro può anche consentire agli utenti di accedere a informazioni che non dovrebbero poter visualizzare.

 Dal momento che per l'esecuzione è necessario che il percorso dell'assembly e quello del documento abbiano evidenze sufficienti, questo tipo di attacco non è facilmente realizzabile. I documenti allegati a messaggi di posta elettronica o su server Intranet non attendibili, ad esempio, non hanno autorizzazioni sufficienti per essere eseguiti.

 Per consentire questo attacco, il codice deve essere scritto in modo da supportare decisioni basate su dati potenzialmente non attendibili. Si supponga di creare un foglio di lavoro che presenta una cella nascosta contenente il nome di un server di database. L'utente invia il foglio di lavoro a una pagina ASPX, che prova a connettersi a tale server usando l'autenticazione SQL e una password hardcoded dell'account sa. Un intruso potrebbe sostituire il contenuto della cella nascosta con un altro nome computer e ottenere la password dell'account sa. Per evitare questo problema non usare mai le password hardcoded e verificare sempre gli ID del server a fronte di un elenco interno di server noti come affidabili prima di accedere al server.

### <a name="recommendations"></a>Suggerimenti

- Convalidare sempre l'input e i dati, che derivino dall'utente, dal documento, da un database, da un servizio Web, o da qualsiasi altra origine.

- Prestare attenzione nell'esposizione di determinati tipi di funzionalità, come l'acquisizione di dati privilegiati per conto dell'utente e il relativo inserimento in un foglio di lavoro non protetto.

- A seconda del tipo di applicazione, può rivelarsi utile verificare che il documento originale sia in esecuzione prima di eseguire qualsiasi codice. Ad esempio, verificare che venga eseguito da un documento archiviato in un percorso noto e sicuro.

- Se nell'applicazione vengono eseguite operazioni privilegiate, può essere opportuno visualizzare un avviso all'apertura del documento. È ad esempio possibile creare una schermata iniziale o una finestra di dialogo di avvio in cui viene segnalato che l'applicazione accederà a informazioni personali, consentendo all'utente di scegliere se continuare o annullare l'operazione. Se un avviso di questo tipo viene visualizzato da un documento apparentemente innocuo, l'utente finale potrà chiudere l'applicazione prima che si verifichino danni.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Codice bloccato dalla protezione del modello a oggetti di Outlook
 Microsoft Office può limitare l'uso da parte del codice di determinate proprietà, metodi e oggetti nel modello a oggetti. Limitando l'accesso a questi oggetti, Outlook aiuta a evitare che virus e worm di posta elettronica usando il modello a oggetti per scopi dannosi. Questa funzionalità di sicurezza è nota come protezione del modello a oggetti di Outlook. Se un componente aggiuntivo VSTO prova a usare una proprietà o metodo mentre è abilitata la protezione del modello a oggetti, Outlook visualizza un avviso di sicurezza che consente all'utente di arrestare l'operazione oppure l'utente concedere l'accesso a proprietà o del metodo per un periodo limitato di t IME. Se l'utente interrompe l'operazione, i componenti aggiuntivi di Outlook creati con le soluzioni Office in Visual Studio generano un'eccezione <xref:System.Runtime.InteropServices.COMException>.

 La protezione del modello a oggetti ha effetto sui componenti aggiuntivi in diversi modi, in base al fatto che Outlook venga usato o meno con Microsoft Exchange Server:

- Se Outlook non viene usato con Exchange, l'amministratore può abilitare o disabilitare la protezione del modello a oggetti per tutti i componenti aggiuntivi nel computer.

- Se Outlook viene usato con Exchange, l'amministratore può abilitare o disabilitare la protezione del modello a oggetti per tutti i componenti aggiuntivi nel computer oppure specificare che determinati componenti aggiuntivi possano essere eseguiti senza la protezione del modello a oggetti. È anche possibile modificare il comportamento della protezione del modello a oggetti per alcune aree del modello a oggetti. Ad esempio, gli amministratori possono consentire automaticamente componenti aggiuntivi VSTO di inviare posta elettronica a livello di codice anche se è abilitata la protezione del modello a oggetti.

  A partire da Outlook 2007, il comportamento della protezione del modello a oggetti è stato modificato per migliorare l'esperienza utente e dello sviluppatore, aiutando al contempo a mantenere Outlook sicuro. Per altre informazioni, vedere [modifiche della sicurezza in Outlook 2007 di codice](http://go.microsoft.com/fwlink/?LinkId=73429).

### <a name="minimize-object-model-guard-warnings"></a>Ridurre al minimo degli avvisi di sicurezza di oggetti modello
 Per evitare la visualizzazione di avvisi di sicurezza quando si usano proprietà e metodi sottoposti a limitazioni, assicurarsi che il componente aggiuntivo VSTO ottenga oggetti di Outlook dal campo `Application` della classe `ThisAddIn` nel progetto. Per altre informazioni su questo campo, vedere [programma VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Per la protezione del modello a oggetti possono essere considerati attendibili solo gli oggetti Outlook ottenuti da questo oggetto. Al contrario, oggetti ottenuti da un nuovo oggetto `Microsoft.Office.Interop.Outlook.Application` non vengono considerati attendibili e, se la protezione del modello a oggetti è attivata, le proprietà e i metodi sottoposti a limitazioni genereranno avvisi di sicurezza.

 Se la protezione del modello a oggetti è attivata, nell'esempio di codice seguente viene visualizzato un avviso di sicurezza. La proprietà `To` della classe `Microsoft.Office.Interop.Outlook.MailItem` è limitata dalla protezione del modello a oggetti. Il `Microsoft.Office.Interop.Outlook.MailItem` oggetto viene considerato attendibile perché il codice lo ottiene da un `Microsoft.Office.Interop.Outlook.Application` creato usando la **nuove** operatore, invece che dal `Application` campo.

 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]

 Esempio di codice seguente viene illustrato come utilizzare con restrizioni alla proprietà di un `Microsoft.Office.Interop.Outlook.MailItem` oggetto considerata attendibile dalla protezione del modello a oggetti. Il codice usa il campo `Application` attendibile per ottenere l'oggetto `Microsoft.Office.Interop.Outlook.MailItem`.

 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]

> [!NOTE]
> Se Outlook viene usato con Exchange, il fatto che tutti gli oggetti Outlook siano ottenuti da `ThisAddIn.Application` non garantisce che il componente aggiuntivo VSTO riuscirà ad accedere al modello a oggetti di Outlook completo. Ad esempio, se un amministratore di Exchange imposta Outlook in modo che vengano respinti tutti i tentativi di accedere alle informazioni di indirizzo usando il modello a oggetti, Outlook non consentirà l'esempio di codice precedente accedere alla proprietà To, anche se il codice Usa il trusted `ThisAddIn.Application` campo.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Specificare quali componenti aggiuntivi da considerare attendibile quando si usa Exchange
 Quando si usa Outlook con Exchange, gli amministratori possono specificare che per determinati componenti aggiuntivi è consentita l'esecuzione senza la protezione del modello a oggetti. I componenti aggiuntivi di Outlook creati usando le soluzioni Office in Visual Studio non possono essere considerati attendibili singolarmente, ma attendibili solo come gruppo.

 Outlook considera attendibile un componente aggiuntivo VSTO in base a un codice hash del punto di ingresso DLL del componente aggiuntivo VSTO. Tutti Outlook componenti aggiuntivi VSTO destinati al [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilizzano la stessa di punto di ingresso DLL (*VSTOLoader. dll*). Ciò significa che se un amministratore considera attendibile qualsiasi aggiuntivo VSTO che ha come destinazione il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] per l'esecuzione senza incontrare ulteriori problemi del modello a oggetti, quindi tutti gli altri componenti aggiuntivi VSTO che hanno come destinazione il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verranno considerati attendibili. Per altre informazioni sull'attendibilità di componenti aggiuntivi specifici per l'esecuzione senza la protezione del modello a oggetti, vedere [Specificare il metodo usato da Outlook per gestire le caratteristiche di prevenzione dei virus](http://go.microsoft.com/fwlink/?LinkId=128773).

## <a name="permission-changes-do-not-take-effect-immediately"></a>Le modifiche alle autorizzazioni non diventano immediatamente effettive
 Se l'amministratore modifica le autorizzazioni per un documento o un assembly, per rendere effettive le modifiche gli utenti devono chiudere e quindi riavviare tutte le applicazioni di Office.

 L'applicazione delle nuove autorizzazioni può essere impedita anche da altre applicazioni che ospitano applicazioni Microsoft Office. Quando vengono modificati i criteri di sicurezza, è consigliabile che gli utenti chiudano tutte le applicazioni che usano Office in modo autonomo o tramite hosting.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Impostazioni del trust center in Microsoft Office system non influiscono sui componenti aggiuntivi o le personalizzazioni a livello di documento
 Gli utenti possono impedire il caricamento dei componenti aggiuntivi VSTO impostando un'opzione nel **Centro protezione**. Tuttavia, i componenti aggiuntivi VSTO a livello di applicazione e le personalizzazioni a livello di documento creati con le soluzioni Office in Visual Studio non sono interessati da tali impostazioni di attendibilità.

 Se l'utente impedisce il caricamento dei componenti aggiuntivi usando il **Centro protezione**, non verranno caricati i tipi di componenti aggiuntivi seguenti:

- Componenti aggiuntivi VSTO COM gestiti e non gestiti

- Smart document gestiti e non gestiti

- Componenti aggiuntivi VSTO di automazione gestiti e non gestiti

- Componenti dati in tempo reale gestiti e non gestiti

  Le procedure seguenti descrivono come usare **Centro protezione** per limitare il caricamento dei componenti aggiuntivi in Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e Microsoft Office 2010. Queste procedure non influiscono sui componenti aggiuntivi o le personalizzazioni create usando gli strumenti di sviluppo di Office in Visual Studio.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>Per disabilitare i componenti aggiuntivi VSTO nelle applicazioni Microsoft Office 2010 e Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]

1. Scegliere la scheda **File** .

2. Scegliere il *NomeApplicazione* **opzioni** pulsante.

3. Nel riquadro delle categorie, scegliere **Centro protezione**.

4. Nel riquadro dei dettagli scegliere Impostazioni **Centro protezione**.

5. Nel riquadro delle categorie scegliere **Componenti aggiuntivi**.

6. Nel riquadro dei dettagli selezionare **Richiedi che i componenti aggiuntivi di applicazioni siano firmati da un autore attendibile** o **Disabilita tutti i componenti aggiuntivi delle applicazioni**.

## <a name="see-also"></a>Vedere anche
- [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)
