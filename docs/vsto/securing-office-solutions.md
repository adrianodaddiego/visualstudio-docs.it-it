---
title: Proteggere le soluzioni Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 31a17fdf51e838405c93efca79d7994cd40ece5c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978596"
---
# <a name="secure-office-solutions"></a>Proteggere le soluzioni Office
  Il modello di sicurezza per le soluzioni Office comprende diverse tecnologie: il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], il Centro protezione di Microsoft Office e l'area siti con restrizioni di Internet Explorer. Le sezioni seguenti descrivono il funzionamento delle diverse funzionalità di sicurezza:

- [Concedere l'attendibilità alle soluzioni Office](#GrantingTrustToSolutions)

- [Concedere l'attendibilità ai documenti](#GrantingTrustToDocuments)

- [Concedere l'attendibilità quando si usa Windows Installer](#GrantingTrustWindowsInstaller)

- [Considerazioni sulla sicurezza specifiche per le soluzioni Office](#Security)

- [Sicurezza durante lo sviluppo](#SecurityDuringDeployment)

- [Visual Studio Tools per Office runtime](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="GrantingTrustToSolutions"></a> Concedere l'attendibilità alle soluzioni Office
 La concessione dell'attendibilità alle soluzioni Office prevede la modifica dei criteri di sicurezza di tutti gli utenti finali in modo che la soluzione Office venga considerata attendibile in base alla seguente evidenza:

- Il certificato usato per firmare il manifesto della distribuzione.

- L'URL del manifesto della distribuzione.

  Per altre informazioni, vedere [concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md).

## <a name="GrantingTrustToDocuments"></a> Concedere l'attendibilità ai documenti
 Una personalizzazione a livello di documento richiede che il documento si trovi in una directory progettata come percorso attendibile. Per altre informazioni, vedere [concedere l'attendibilità a documenti](../vsto/granting-trust-to-documents.md).

## <a name="GrantingTrustWindowsInstaller"></a> Concedere l'attendibilità quando si usa Windows Installer
 È possibile usare Windows Installer per creare un file MSI per installare le soluzioni Office nella directory Programmi, che richiede diritti di amministratore. Per le soluzioni Office nella directory Programmi, Visual Studio 2010 Tools per Office runtime considera le soluzioni di Office siano attendibili e non include la richiesta di attendibilità di ClickOnce.

## <a name="Security"></a> Considerazioni sulla sicurezza specifiche per le soluzioni Office
 Le funzionalità di sicurezza fornite da [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] e Microsoft Office possono contribuire alla protezione contro diverse possibili minacce alla sicurezza nelle soluzioni Office. Per altre informazioni, vedere [considerazioni specifiche sulla sicurezza per le soluzioni Office](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="SecurityDuringDeployment"></a> Sicurezza durante lo sviluppo
 Per semplificare il processo di sviluppo, Visual Studio imposta i criteri di sicurezza necessari per eseguire ed eseguire il debug della soluzione nel computer ogni volta che si compila un progetto. In alcuni scenari, è necessario aggiungere altri passaggi di sicurezza per sviluppare il progetto.

### <a name="document-level-solutions"></a>Soluzioni a livello di documento
 Il percorso completo di un documento deve essere aggiunto all'elenco di percorsi attendibili nell'applicazione Microsoft Office se si stanno sviluppando i tipi di progetti seguenti:

- Le soluzioni presenti in una condivisione file di rete, ad esempio a livello di documento  *\\\servername\sharename*.

- A livello di documento soluzioni per Word che usano *doc* oppure *docm* file.

  Includere le sottodirectory quando si aggiunge il percorso del documento all'elenco di percorsi attendibili oppure includere le cartelle di debug e di compilazione specifiche. Per altre informazioni, vedere l'articolo della Guida Online di Microsoft Office [creazione, rimozione o modifica di un percorso attendibile per i file](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Certificati temporanei
 Se non è disponibile un certificato di firma, Visual Studio crea un certificato temporaneo. Usare questo certificato temporaneo solo durante lo sviluppo e acquistare un certificato ufficiale per la distribuzione.

 Il certificato temporaneo viene generato dopo la prima compilazione di un progetto Office. La volta successiva che si preme **F5**, il progetto viene ricompilato perché il progetto viene contrassegnato come modificato quando viene aggiunto il certificato.

 Cancellare regolarmente i certificati temporanei poiché potrebbero accumularsi nel tempo.

## <a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools per Office runtime
 Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dispone di funzionalità per verificare l'identità del server di pubblicazione e le autorizzazioni concesse a una personalizzazione. Verifica le autorizzazioni mediante una sequenza di controlli di sicurezza.

### <a name="security-during-customization-loading"></a>Sicurezza durante il caricamento di personalizzazione
 Quando viene caricata una personalizzazione a livello di documento, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sempre controlla se il documento è nell'elenco di percorsi attendibili. Inoltre, il runtime controlla se la soluzione richiede FullTrust nel manifesto dell'applicazione. Non esegue controlli di sicurezza aggiuntivi durante il caricamento della personalizzazione.

### <a name="sequence-of-security-checks-during-installation"></a>Sequenza di controlli di sicurezza durante l'installazione
 Quando una soluzione Office viene installata o aggiornata, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] esegue un set di controlli di sicurezza in una sequenza specifica per prendere una decisione di attendibilità. Una soluzione viene installata o aggiornata solo se il runtime ne determina l'attendibilità.

 È possibile avviare il processo di installazione in uno dei quattro modi: eseguendo il programma di installazione, aprendo il manifesto di distribuzione, aprendo l'host dell'applicazione Microsoft Office o eseguendo *VSTOInstaller.exe*.

 Il primo controllo di sicurezza si applica solo alle soluzioni a livello di documento. Il documento di una soluzione a livello di documento deve trovarsi in un percorso attendibile. Se il documento si trova in una condivisione file di rete remota oppure ha un *doc* oppure *docm* estensione nome file, il percorso del documento deve essere aggiunto all'elenco di percorsi attendibili. Per altre informazioni, vedere [concedere l'attendibilità a documenti](../vsto/granting-trust-to-documents.md).

 ![Sicurezza VSTO: installazione da Microsoft Office](../vsto/media/host-install.png "sicurezza VSTO: installazione da Microsoft Office")

 Il set di controlli di sicurezza successivo è quello di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e ClickOnce. Per superare questi controlli, le soluzioni Office devono richiedere le autorizzazioni FullTrust, essere firmate con un certificato che non è elencato nell'elenco editori non attendibili e trovarsi in una posizione che non è presente nell'area con restrizioni di Internet Explorer. Se il certificato si trova nell'elenco degli editori attendibili, la soluzione viene installata immediatamente. In caso contrario, se ha superato i controlli, la soluzione continua con l'ultimo set di controlli.

 ![Sicurezza VSTO per l'installazione di soluzioni](../vsto/media/installing.png "sicurezza VSTO per l'installazione di soluzioni")

 Se il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiesta di attendibilità è consentito e la soluzione non è ancora stata concessa attendibilità, il runtime consentirà all'utente finale di prendere la decisione di attendibilità. Se l'utente concede l'attendibilità alla soluzione, viene aggiunta una voce all'elenco di inclusione dell'utente. Tutte le soluzioni nell'elenco di inclusione dell'utente hanno l'attendibilità totale e possono essere installate ed eseguite.

 A partire da Visual Studio 2010, l'elenco di inclusione viene ignorato se la soluzione Office viene installata usando Windows Installer (MSI) nella directory Programmi. Per altre informazioni, vedere [soluzioni di Office Trust usando gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![Sicurezza VSTO: utilizzo del programma di installazione per installare](../vsto/media/setup-vstoinstaller.png "sicurezza VSTO: utilizzo del programma di installazione per installare")

## <a name="see-also"></a>Vedere anche

- [Concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)
- [Concedere l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md)
- [Trust di soluzioni Office mediante elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Procedura: Configurare la sicurezza di elenco di inclusione](../vsto/how-to-configure-inclusion-list-security.md)
- [Procedura: Firmare soluzioni Office](../vsto/how-to-sign-office-solutions.md)
- [Risolvere i problemi di sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)
- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Riferimenti di ClickOnce](../deployment/clickonce-reference.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
