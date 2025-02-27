---
title: Pagina Firma, Creazione progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ba55795e1f1b5f54b2a863ec0163a796111d9800
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689474"
---
# <a name="signing-page-project-designer"></a>Pagina Firma, Progettazione progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usare la pagina **Firma** di **Creazione progetti** per firmare i manifesti dell'applicazione e di distribuzione, nonché l'assembly (firma con nome sicuro).  
  
 La firma dei manifesti dell'applicazione e di distribuzione è un processo distinto dalla firma di un assembly, anche se entrambe le attività vengono eseguite nella pagina **Firma**.  
  
 L'archiviazione delle informazioni relative al file di chiave, poi, è diversa per la firma dei manifesti e per la firma degli assembly. Per la firma dei manifesti, le informazioni sulla chiave vengono archiviate nel database dell'archivio di crittografia del computer e nell'archivio dei certificati di Windows dell'utente corrente. Per la firma degli assembly, le informazioni sulla chiave vengono archiviate esclusivamente nel database dell'archivio di crittografia del computer.  
  
 Per accedere alla pagina **Firma**, selezionare un nodo di progetto in **Esplora soluzioni** e quindi scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra **Creazione progetti**, fare clic sulla scheda **Firma**.  
  
## <a name="application-and-deployment-manifest-signing"></a>Firma del manifesto di applicazione e distribuzione  
 Casella di controllo **Firma i manifesti ClickOnce**  
 Selezionare questa casella di controllo per firmare i manifesti dell'applicazione e di distribuzione con una coppia di chiavi pubblica/privata. Per altre informazioni su come eseguire questa operazione, vedere [Procedura: Firmare manifesti dell'applicazione e di distribuzione](../../ide/how-to-sign-application-and-deployment-manifests.md).  
  
 Pulsante **Seleziona dall'archivio**  
 Consente di selezionare un certificato esistente dall'archivio dei certificati personali dell'utente corrente. È possibile selezionare uno dei certificati disponibili per firmare i manifesti di distribuzione e dell'applicazione.  
  
 Se si fa clic su **Seleziona dall'archivio**, viene aperta la finestra di dialogo **Seleziona un certificato**, che elenca i certificati validi (non scaduti) presenti nell'archivio personale che dispongono di chiavi private. Lo scopo del certificato selezionato deve prevedere la firma di codice.  
  
 Se si fa clic su **view certificate properties** (Fare clic qui per visualizzare le proprietà del certificato), viene visualizzata la finestra di dialogo **Dettagli del certificato**. Questa finestra di dialogo contiene informazioni dettagliate sul certificato e opzioni aggiuntive. È possibile fare clic su **Altre informazioni sui certificati** per visualizzare altre informazioni della Guida.  
  
 Pulsante **Seleziona da un file**  
 Consente di selezionare un certificato da un file di chiave esistente.  
  
 Se si fa clic su **Seleziona da un file**, si apre la finestra di dialogo **Seleziona file**, che consente di selezionare un file della chiave del certificato (con estensione pfx). Il file deve essere protetto da password e non può essere già presente nell'archivio dei certificati personali.  
  
 Nella finestra di dialogo **Immettere la password per aprire il file** immettere la password per aprire il file della chiave del certificato (con estensione pfx). Le informazioni sulla password vengono archiviate nell'elenco dei contenitori di chiavi personali e nell'archivio certificati personale.  
  
 Pulsante **Crea certificato di prova**  
 Consente di creare un certificato per il test. Questo certificato viene usato per firmare l'applicazione ClickOnce e i manifesti di distribuzione.  
  
 Se si fa clic su **Crea certificato di prova**, si apre la finestra di dialogo **Crea certificato di prova**, in cui è possibile digitare una password per il file di chiave con nome sicuro relativo al certificato di prova. Al file viene assegnato il nome *NomeProgetto*_TemporaryKey. pfx. Se si fa clic su **OK** senza digitare alcuna password, il file con estensione pfx non è protetto da password.  
  
 Casella **URL server di timestamp**  
 Specifica l'indirizzo di un server che genera il timestamp della firma. Quando si fornisce un certificato, questo sito esterno verifica l'ora in cui l'applicazione viene firmata.  
  
## <a name="assembly-signing"></a>Firma degli assembly  
 Casella di controllo **Firma assembly**  
 Selezionare questa casella di controllo per firmare l'assembly e creare un file di chiave con nome sicuro. Per altre informazioni sulla firma dell'assembly tramite **Creazione progetti**, vedere [Procedura: Firmare un assembly (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 Per firmare l'assembly, questa opzione usa lo strumento Al.exe fornito da [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]. Per altre informazioni su Al.exe, vedere [Procedura: Firmare un assembly con un nome sicuro](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 Elenco **Scegliere un file di chiave con nome sicuro**  
 Consente di specificare un file di chiave nuovo o esistente con nome sicuro da usare per firmare l'assembly. Selezionare **\<Sfoglia...>** per selezionare un file di chiave esistente.  
  
 Selezionare **\<Nuovo...>** per creare un nuovo file di chiave con cui firmare l'assembly. Verrà visualizzata la finestra di dialogo **Crea chiave con nome sicuro**, che è possibile usare per specificare il nome di un file di chiave e proteggere il file con una password. La password deve avere una lunghezza di almeno 6 caratteri. Se si specifica una password, viene creato un file di scambio di informazioni personali (con estensione pfx, Personal inFormation eXchange). Se non si specifica una password, viene creato un file di chiave con nome sicuro (con estensione snk).  
  
 Pulsante **Cambia password**  
 Consente di modificare la password del file di chiave con estensione pfx usato per firmare l'assembly.  
  
 Se si fa clic su **Cambia password** si apre la finestra di dialogo **Modifica password chiave**. In questa finestra di dialogo il campo **Vecchia password** contiene la password corrente per il file di chiave. La **Nuova password** deve avere una lunghezza di almeno 6 caratteri. Le informazioni relative alla password vengono archiviate nell'archivio certificati Windows dell'utente corrente.  
  
 Casella di controllo **Solo firma ritardata**  
 Selezionare questa casella di controllo per abilitare la firma ritardata.  
  
 Si tenga presente che un progetto con firma ritardata non può essere eseguito e non può essere sottoposto a debug. È tuttavia possibile evitare la verifica durante lo sviluppo usando [Sn.exe (strumento Nome sicuro)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) con l'opzione `-Vr`.  
  
> [!NOTE]
> Quando si firma un assembly, non sempre è possibile accedere a una chiave privata. Un'organizzazione, ad esempio, può avere una coppia di chiavi ben protetta a cui gli sviluppatori non hanno accesso su base giornaliera. La chiave pubblica è disponibile ma l'accesso alla chiave privata è limitato a poche persone. In un caso del genere, è possibile usare una firma *ritardata* o *parziale*. Questa funzione consente di fornire la chiave pubblica, rimandando l'aggiunta della chiave privata al momento della consegna dell'assembly.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle proprietà di progetto](../../ide/reference/project-properties-reference.md)   
 [Gestione delle firme di assembly e manifesti](../../ide/managing-assembly-and-manifest-signing.md)   
 [Firma con nome sicuro per applicazioni gestite](https://msdn.microsoft.com/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [Procedura: Sign Application and manifesti di distribuzione](../../ide/how-to-sign-application-and-deployment-manifests.md)   
 [Procedura: Firmare un Assembly (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Procedura: Firmare un Assembly con nome sicuro](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)   
 [Assembly con nomi sicuri](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)
