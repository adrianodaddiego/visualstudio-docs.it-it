---
title: Accesso alle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 05/14/2019
ms.topic: conceptual
description: Come accedere alla sottoscrizione di Visual Studio
searchscope: VS Subscription
ms.openlocfilehash: d010a908d28fd6f7be86cee27fa86f0ac24471d6
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805289"
---
# <a name="signing-in-to-your-visual-studio-subscription"></a>Accesso alla sottoscrizione di Visual Studio

La procedura per accedere alla sottoscrizione di Visual Studio dipende dal tipo di account usato.  Ad esempio, si potrebbe usare un account Microsoft (MSA) o un indirizzo di posta elettronica fornito dal datore di lavoro o dell'istituto di istruzione.  A partire da gennaio 2019 è possibile usare anche il proprio account GitHub per accedere ad alcune sottoscrizioni. 

In questo articolo sono illustrati quattro diversi metodi di accesso:  Usare i collegamenti a destra per passare a una qualsiasi di queste sezioni.
1. Accesso con l'account Microsoft
2. Accesso con l'account aziendale o dell'istituto di istruzione
3. Uso dell'account Microsoft per accedere a un account aziendale o dell'istituto di istruzione
4. Accesso con l'account GitHub

## <a name="signing-in-with-your-microsoft-account-msa"></a>Accesso con l'account Microsoft
1. Visitare [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
2. Immettere l'indirizzo di posta elettronica fornito al momento della configurazione o dell'acquisto della sottoscrizione di Visual Studio.

   > [!NOTE]
   > Questo indirizzo viene anche identificato nel messaggio di posta elettronica di benvenuto del sottoscrittore ricevuto al momento dell'acquisto della sottoscrizione o dell'iscrizione per Visual Studio Dev Essentials. In caso di problemi a individuare il messaggio di benvenuto, controllare le cartelle della posta indesiderata.

3. Immettere la password.
4. Fai clic su **Accedi**.
5. A questo punto, dovrebbe essere visualizzata la pagina "Vantaggi".

### <a name="for-visual-studio-dev-essentials-users"></a>Per gli utenti di Visual Studio Dev Essentials:
Quando si accede alla sottoscrizione Visual Studio Dev Essentials per la prima volta, verrà visualizzata una finestra di dialogo di benvenuto.  Fare clic su **Conferma** per accettare i termini e le condizioni del programma.

## <a name="signing-in-with-your-work-or-school-account"></a>Accesso con l'account aziendale o dell'istituto di istruzione

1. Visitare [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
2. Immettere l'indirizzo di posta elettronica al quale è stata assegnata la nuova sottoscrizione di Visual Studio.

   > [!NOTE]
   > Questo indirizzo viene anche indicato nel messaggio di posta elettronica di benvenuto al sottoscrittore ricevuto. In caso di problemi a individuare il messaggio di benvenuto, controllare le cartelle della posta indesiderata.

3. Scegliere **Continua**.
4. Si verrà reindirizzati alla pagina di accesso aziendale.
5. Immettere la password.
6. Fai clic su **Accedi**
7. A questo punto, dovrebbe essere visualizzata la pagina "Vantaggi".

È ora possibile visualizzare il tipo di sottoscrizione in uso, indicato nella barra blu nella parte superiore del portale.

È anche possibile visualizzare la sottoscrizione attualmente selezionata in alto a destra, sotto il nome utente.  Compare la dicitura "In fase di visualizzazione:", seguita dalla sottoscrizione.  Se sono disponibili più sottoscrizioni, è possibile fare clic sulla freccia a discesa e selezionare la sottoscrizione che si vuole usare.

## <a name="using-your-microsoft-account-to-sign-in-to-a-work-or-school-account"></a>Uso dell'account Microsoft per accedere a un account aziendale o dell'istituto di istruzione

1. Passare a [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
2. Immettere l'indirizzo di posta elettronica al quale è stata assegnata la nuova sottoscrizione di Visual Studio.

   > [!NOTE]
   > Questo indirizzo è anche indicato nella Lettera di benvenuto al sottoscrittore. Se la Lettera di benvenuto non è stata ricevuta, controllare nelle cartelle di posta indesiderata.

3. Scegliere **Continua**.
4. Si verrà reindirizzati a una pagina di decisione.
    - Selezionare **Account aziendale o dell'istituto di istruzione** se la sottoscrizione è associata a un account aziendale o dell'istituto di istruzione associato a un tenant di Azure Active Directory (AAD).
    - Selezionare **Personale** se la sottoscrizione è associata a un indirizzo di posta elettronica aziendale ma è stata anche convertita in un account Microsoft personale.

        > [!NOTE]
        > Ciò sarà vero per molti sottoscrittori che hanno usato sottoscrizioni di Visual Studio (in precedenza MSDN) in passato.

    - Se un percorso non riesce, provare l'altro.  Gli amministratori delle sottoscrizioni potrebbero aver modificato la sottoscrizione.

5. Immettere la password.
6. Fai clic su **Accedi**.
7. A questo punto, dovrebbe essere visualizzata la pagina "Vantaggi".

## <a name="signing-in-with-your-github-account"></a>Accesso con l'account GitHub

Il supporto delle identità GitHub consente di usare un account di GitHub esistente come credenziali per un account Microsoft nuovo o esistente, collegando l'account GitHub con l'account Microsoft. 

Quando si esegue l'accesso con GitHub, Microsoft verifica se un indirizzo e-mail associato all'account GitHub corrisponde a un account Microsoft personale o aziendale. Se l'indirizzo corrisponde all'account aziendale dell'utente, verrà richiesto di accedere a tale account. Se l'indirizzo corrisponde a un account personale, l'account GitHub verrà aggiunto come metodo di accesso all'account personale.

Dopo che le credenziali dell'account GitHub e dell'account Microsoft sono state collegate, è possibile usare questo accesso Single Sign-On ovunque è consentito l'accesso con un account Microsoft personale ad esempio nei siti di Azure, nelle app di Office e in Xbox. Questi account possono essere usati anche per gli accessi come ospite di Azure Active Directory con un account Microsoft, a condizione che l'indirizzo di posta elettronica corrisponda a quello presente nell'invito.

> [!NOTE]
> Il collegamento di un'identità di GitHub a un account Microsoft non consente a Microsoft nessun accesso al codice. Quando le app come Azure DevOps e Visual Studio richiedono l'accesso ai repository di codice, verrà richiesto all'utente il consenso specifico per tale accesso. 

### <a name="frequently-asked-questions"></a>Domande frequenti
Le domande frequenti che seguono riguardano aspetti relativi all'uso delle credenziali dell'account GitHub per l'accesso alle sottoscrizioni di Visual Studio.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>D: Ho dimenticato la password di GitHub.  Come posso accedere al mio account?
R:  È possibile recuperare l'account GitHub accedendo [Reimposta password](https://github.com/password_reset). In alternativa è possibile recuperare l'account Microsoft collegato a GitHub immettendo l'indirizzo di posta elettronica dell'account GitHub in [Recupera il tuo account](https://account.live.com/password/reset).

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>D: Ho eliminato il mio account GitHub.  Come posso accedere al mio account Microsoft (account del servizio gestito)?
R: Se non sono presenti altre credenziali nell'account del servizio gestito (ad esempio una password, l'app Authenticator o una chiave di sicurezza), è possibile ripristinare l'account Microsoft usando l'indirizzo di posta elettronica collegato a tale account. Per iniziare, passare a [Recupera il tuo account](https://account.live.com/password/reset). È necessario aggiungere una password per l'account, che potrà essere usata per gli accessi successivi. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>D: Non è disponibile alcuna opzione "Accedi con GitHub" nella pagina di accesso.  Come è possibile usare le credenziali di GitHub per l'accesso?
R:  Digitare l'indirizzo di posta elettronica dell'account GitHub selezionato durante la creazione dell'account Microsoft collegato a GitHub. Si verrà trasferiti a GitHub per l'accesso. In alternativa, se nella pagina è presente un collegamento Opzioni di accesso usare il pulsante **Accedi con GitHub** visualizzato dopo aver fatto clic su tale collegamento. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>D: Non riesco ad accedere ad alcune app e prodotti con GitHub.  Perché?
R:  Non tutti i prodotti Microsoft supportano l'accesso a GitHub.com dalla loro pagina di accesso, ad esempio la console Xbox. Quando si digita l'indirizzo e-mail dell'account GitHub collegato, Microsoft invia un codice a tale indirizzo per verificare l'identità del mittente. L'utente continua ad accedere allo stesso account, ma con un altro metodo di accesso. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>D:  Ho aggiunto una password per l'account Microsoft collegato al mio account GitHub.  Può rappresentare un problema?
R:  Assolutamente no. Questo non modifica la password di GitHub, è semplicemente disponibile un altro modo per accedere all'account Microsoft. Ogni volta che si accede usando l'indirizzo e-mail, sarà possibile scegliere se accedere con la password dell'account Microsoft o andare a GitHub per l'accesso. Se è necessario aggiungere una password, è consigliabile che sia diversa dalla password per l'account GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>D: Voglio aggiungere l'app Authenticator all'account creato tramite GitHub.  È possibile?
R:  Sì. È sufficiente scaricare l'app e accedere usando il proprio indirizzo di posta elettronica. Quando si accede con l'indirizzo di posta elettronica viene richiesto di scegliere come credenziali l'[app Authenticator](https://go.microsoft.com/fwlink/?linkid=2090219) o GitHub.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>D: Ho abilitato l'autenticazione a due fattori sia nell'account GitHub sia nell'account Microsoft (account del servizio gestito), ma quando accedo all'account del servizio gestito, mi viene comunque chiesto di eseguire l'autenticazione due volte.  Perché?
R: A causa di restrizioni di sicurezza, Microsoft considera l'accesso a GitHub come verifica a fattore singolo, anche se di fatto si tratta di una verifica in due passaggi. Pertanto, è necessario eseguire nuovamente l'autenticazione per l'account Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>D:  Come è possibile stabilire se l'account Microsoft e l'account GitHub sono collegati?
R:  Ogni volta che si accede tramite l'alias dell'account (indirizzo di posta elettronica, numero di telefono, nome Skype), vengono visualizzati tutti i metodi di accesso per l'account. Se GitHub non è visualizzato fra tali metodi, non è stato ancora configurato.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>D:  Come scollegare gli account Microsoft e GitHub? 
R:  Andare alla [scheda Sicurezza](https://account.microsoft.com/security) di account.microsoft.com e fare clic su **Altre opzioni di sicurezza** per scollegare l'account GitHub. Quando viene scollegato, l'account GitHub viene rimosso come metodo di accesso e viene anche rimosso l'accesso a qualsiasi repository GitHub in Visual Studio. Altri prodotti Microsoft potrebbero avere richiesto l'accesso all'account GitHub separatamente. Pertanto la rimozione dell'accesso in questa posizione non rimuoverà l'accesso in tutti i prodotti. Andare alla pagina delle [autorizzazioni applicazione](https://github.com/settings/applications) del profilo GitHub per revocare il consenso alle app elencate in tale pagina.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>D:  Quando tento di usare l'account GitHub per l'accesso, mi viene segnalato che ho già un'identità Microsoft e devo usare tale identità.  Qual è il problema?
R:  Se si ha un indirizzo di posta elettronica di Azure Active Directory nell'account GitHub, si ha già un'identità Microsoft che può accedere ad Azure ed eseguire pipeline di integrazione continua tramite il codice GitHub. L'uso di tale account garantisce che le risorse di Azure e le pipeline di compilazione restino entro i limiti dell'organizzazione. Se tuttavia si stanno eseguendo attività a titolo personale, è consigliabile inserire un indirizzo di posta elettronica personale nell'account GitHub, in modo da potere sempre accedere all'account stesso. Dopo aver eseguito questa operazione, provare a eseguire nuovamente l'accesso e scegliere **Usa un indirizzo e-mail diverso** quando viene chiesto di accedere al proprio account aziendale o dell'istituto di istruzione. In questo modo è possibile creare un nuovo account Microsoft con tale indirizzo di posta elettronica personale.
