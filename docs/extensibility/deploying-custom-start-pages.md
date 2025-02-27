---
title: Distribuzione di pagine iniziali personalizzate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5a84ba2ff92463ebea177fc5c3b04810de7ae817
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348213"
---
# <a name="deploy-custom-start-pages"></a>Distribuire le pagine iniziali personalizzate

È possibile distribuire le pagine iniziali personalizzate tramite distribuzione VSIX oppure copiando i file nelle posizioni corrette nel computer di destinazione.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Distribuzione VSIX usando il modello di progetto di pagina iniziale

Quando si crea una pagina iniziale usando il modello di progetto di pagina iniziale e quindi compilare il progetto, Visual Studio crea una *VSIX* file che è possibile distribuire. Creazione del pacchetto di una pagina di avvio in una *VSIX* file ti offre le opzioni seguenti per la distribuzione, a seconda dei destinatari desiderati:

- È possibile inserire il *VSIX* file in una condivisione di rete o in un sito Web pubblico. Quando un utente apre il file, viene installata automaticamente nella pagina iniziale.

- È possibile caricare il *VSIX* file per il [Visual Studio Marketplace](https://marketplace.visualstudio.com/) del sito Web in modo che gli utenti possono installarla tramite **Gestione estensioni**.

Il modello di progetto di pagina iniziale Crea una copia del valore predefinito la pagina iniziale di Visual Studio in modo che è possibile modificare la copia e conservare l'originale.

È possibile ottenere il modello di progetto di pagina iniziale usando **gestore estensioni del** o scaricandolo dal sito Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Distribuzione VSIX senza usare il modello di progetto di pagina iniziale
 Una corretta distribuzione VSIX richiede un'estensione per essere installati nelle cartelle che sono riconosciute dal processo di registrazione VSIX e da **gestore estensioni del**. Poiché il modello di progetto di pagina iniziale specifica già nelle cartelle corrette, è consigliabile usarla ogni volta che si desidera creare un pacchetto di un'estensione per la distribuzione di VSIX. Tuttavia, se si dispone di un caso in cui non è possibile utilizzare il modello, è possibile creare una distribuzione VSIX senza usarlo.

 Per creare una distribuzione VSIX senza usare il modello di progetto di pagina iniziale, creare prima di tutto una *VSIX* file per la pagina di avvio in uno dei due modi:

- Aggiungendo i file della pagina iniziale personalizzati per un progetto VSIX vuoto. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

- Creando manualmente un *VSIX* file. Per creare un *VSIX* file manualmente:

   1. Creare il *Extension. vsixmanifest* file e il *[Content_Types] XML* file in una nuova cartella. Per altre informazioni, vedere [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. In Windows Explorer, fare doppio clic la cartella che contiene i due file XML, fare clic su **Invia a**e quindi fare clic sulla cartella compressa. Rinominare l'oggetto risultante *zip* del file ai *Filename.vsix*, in cui nomefile è il nome del file ridistribuibile che installa il pacchetto.

Per Visual Studio riconosca una pagina iniziale, il `Content Element` del manifesto VSIX deve contenere un `CustomExtension Element` con il `Type` attributo impostato su `"StartPage"`. Viene visualizzata un'estensione di pagina iniziale che è stata installata utilizzando la distribuzione VSIX nel **Personalizza pagina iniziale** elenco il **avvio** pagina Opzioni come **[estensione installata]** *Nome dell'estensione*.

Se il pacchetto di pagina iniziale include gli assembly, è necessario aggiungere la registrazione di percorso di associazione in modo che siano disponibili quando si avvia Visual Studio. A tale scopo, assicurarsi che il pacchetto includa un *pkgdef* file che contiene le informazioni seguenti.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Distribuzione VSIX per tutti gli utenti
 Per impostazione predefinita, le estensioni distribuite nei pacchetti VSIX installare solo per l'utente corrente. È possibile apportare un'installazione di pagina iniziale per tutti gli utenti del computer di destinazione mediante la creazione di una distribuzione di tutti gli utenti.

### <a name="to-create-an-all-users-deployment"></a>Per creare una distribuzione di tutti gli utenti

1. Aprire il *Extension. vsixmanifest* file nella visualizzazione codice.

2. Nel `Identifier` elemento del manifesto vsix, aggiungere un' `AllUsers` elemento che ha il valore `true`.

    ```
    <AllUsers>true</AllUsers>
    ```

     In questo modo, il programma di installazione vsix richiede le autorizzazioni di amministratore e quindi installare i file *\Common7\IDE\Extensions*.

3. Aprire il *pkgdef* file.

4. Modificare il *pkgdef* per impostare la pagina iniziale predefinita in HKLM aggiungendo il codice seguente, dove *MyStartPage.xaml* è il nome del *XAML* file contenente l'inizio Pagina.

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     Indica a Visual Studio per la ricerca nella nuova posizione della pagina iniziale.

## <a name="file-copy-deployment"></a>Distribuzione tramite Copia file
 Non è necessario creare un *VSIX* file per la distribuzione di una pagina iniziale personalizzata. Al contrario, è possibile copiare i file di supporto direttamente in dell'utente e il markup <em>\StartPages\* cartella. Il **Personalizza pagina iniziale</em>*  elenco il **avvio** opzioni pagina elenca ogni *XAML* file in tale cartella, con il percorso, ovvero, ad esempio, *%USERPROFILE%\My Documents\Visual Studio {version} \StartPages\\/{nome File}. XAML*. Se la pagina iniziale include i riferimenti agli assembly privato, è necessario copiarli e incollarli nel * \PrivateAssemblies\* cartella.

 Per distribuire una pagina iniziale creato senza comprimerlo in un *VSIX* , è consigliabile utilizzare una strategia di copia del file di base, ad esempio, uno script di batch, o qualsiasi altra tecnologia di distribuzione che consente di inserire i file di Directory obbligatorie.

### <a name="to-manually-install-a-custom-start-page"></a>Per installare manualmente una pagina iniziale personalizzata

1. Copia il *XAML* file che contiene il markup della pagina iniziale, insieme a eventuali file di supporto diverso da assembly e li incolliamo in dell'utente * \StartPages\* cartella.

2. Se la pagina iniziale richiede l'assembly, copiarli e incollarli nel *... \\{Cartella di installazione di visual Studio} \Common7\IDE\PrivateAssemblies.\\* .

3. Nel **Personalizza pagina iniziale** elenco le **avvio** le opzioni di pagina, selezionare la nuova pagina iniziale. Per altre informazioni, vedere [personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Vedere anche

- [personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)
- [Aggiungi controllo utente nella pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)