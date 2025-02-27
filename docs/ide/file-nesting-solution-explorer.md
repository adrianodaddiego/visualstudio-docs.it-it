---
title: Regole di annidamento in Esplora soluzioni
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jillfra
ms.openlocfilehash: 58e727c6335dd391abab4f50a110d361a658e00a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548953"
---
# <a name="customize-file-nesting-in-solution-explorer"></a>Personalizzare l'annidamento file in Esplora soluzioni

L'annidamento di file correlati in **Esplora soluzioni** non è una funzione nuova. Finora, tuttavia, l'utente non aveva il controllo sulle regole di annidamento. È possibile scegliere tra i set di impostazioni **Disattivato**, **Predefinito** e **Web**, ma è anche possibile personalizzare l'annidamento esattamente in base alle proprie esigenze. È anche possibile creare impostazioni specifiche per una soluzione e un progetto. Altre informazioni in merito sono disponibili più avanti. Prima di tutto verranno illustrate le funzioni predefinite.

> [!NOTE]
> La funzionalità è attualmente supportata solo per i progetti ASP.NET Core.

## <a name="file-nesting-options"></a>Opzioni di annidamento file

![Pulsante per l'attivazione e la disattivazione dell'annidamento file](media/filenesting_onoff.png)

Le opzioni disponibili per l'annidamento file non personalizzato sono:

* **Disattivato**: questa opzione presenta un semplice elenco dei file, senza alcun annidamento.

* **Predefinito**: questa opzione attiva il comportamento di annidamento file predefinito in **Esplora soluzioni**. Se per il tipo di progetto specificato non è presente alcuna impostazione, nel progetto non viene eseguito alcun annidamento di file. Se sono presenti impostazioni, ad esempio, per un progetto Web, l'annidamento viene applicato.

* **Web**: questa opzione applica il comportamento di annidamento file **Web** a tutti i progetti nella soluzione corrente. Sono presenti numerose regole. Gli utenti sono invitati a esaminarle e a inviare commenti e suggerimenti. Lo screenshot seguente evidenzia solo alcuni esempi del comportamento di annidamento file che è possibile ottenere con questa opzione:

   ![Annidamento file in Esplora soluzioni](media/filenesting.png)

## <a name="customize-file-nesting"></a>Personalizzare l'annidamento file

Se le impostazioni predefinite non sono utili, è possibile creare impostazioni di annidamento file personalizzate per **Esplora soluzioni**. È possibile aggiungere un numero illimitato di impostazioni di annidamento file personalizzate ed è possibile passare dall'una all'altra secondo le proprie esigenze. Per creare una nuova impostazione personalizzata, è possibile iniziare con un file vuoto o usare le impostazioni **Web** come punto iniziale:

![Aggiungere regole di annidamento file personalizzate](media/filenesting_addcustom.png)

Come punto iniziale è consigliabile usare le impostazioni **Web**, perché è più facile usare qualcosa che funziona già. Se si usano le impostazioni **Web** come punto iniziale, il file con estensione *.filenesting.json* avrà un aspetto simile al seguente:

![Usare le regole di annidamento di un file esistente come base per le impostazioni personalizzate](media/filenesting_editcustom.png)

Si esamineranno ora il nodo **dependentFileProviders** e i suoi nodi figlio. Ogni nodo figlio corrisponde a un tipo di regola che Visual Studio può usare per annidare file. Ad esempio, **stesso nome file ma estensione diversa** è un tipo di regola. Le regole disponibili sono:

* **extensionToExtension**: usare questo tipo di regola per annidare *file.js* in *file.ts*

* **fileSuffixToExtension**: usare questo tipo di regola per annidare *file-vsdoc.js* in *file.ts*

* **addedExtension**: usare questo tipo di regola per annidare *file.html.css* in *file.html*

* **pathSegment**: usare questo tipo di regola per annidare *jquery.min.js* in *jquery.js*

* **allExtensions**: usare questo tipo di regola per annidare *file.** in *file.js*

* **fileToFile**: usare questo tipo di regola per annidare *bower.json* in *.bowerrc*

### <a name="the-extensiontoextension-provider"></a>Provider extensionToExtension

Questo provider consente di definire regole di annidamento file usando estensioni file specifiche. Si consideri l'esempio seguente:

![Regole dell'esempio extentionToExtension](media/filenesting_extensiontoextension.png) ![Effetto dell'esempio extentionToExtension](media/filenesting_extensiontoextension_effect.png)

* *cart.js* viene annidato in *cart.ts* per la prima regola di **extensionToExtension**

* *cart.js* non viene annidato in *cart.tsx* perché l'estensione **ts** precede l'estensione **tsx** nelle regole e può esistere un unico elemento padre

* *light.css* viene annidato in *light.sass* per la seconda regola di **extensionToExtension**

* *home.html* viene annidato in *home.md* per la terza regola di **extensionToExtension**

### <a name="the-filesuffixtoextension-provider"></a>Provider fileSuffixToExtension

Questo provider ha lo stesso funzionamento di **extensionToExtension**, con l'unica differenza che la regola esamina il suffisso del file anziché la sola l'estensione. Si consideri l'esempio seguente:

![Regole dell'esempio fileSuffixToExtension](media/filenesting_filesuffixtoextension.png) ![Effetto dell'esempio fileSuffixToExtension](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* viene annidato in *portal.js* per la regola di **fileSuffixToExtension**

* tutti gli altri aspetti della regola funzionano allo stesso modo di **extensionToExtension**

### <a name="the-addedextension-provider"></a>Provider addedExtension

Questo provider annida i file con un'estensione aggiuntiva nel file senza l'estensione aggiuntiva. L'estensione aggiuntiva può essere visualizzata solo alla fine del nome file completo. Si consideri l'esempio seguente:

![Regole dell'esempio addedExtension](media/filenesting_addedextension.png) ![Effetto dell'esempio addedExtension](media/filenesting_addedextension_effect.png)

* *file.html.css* viene annidato in *file.html* per la regola di **addedExtension**

### <a name="the-pathsegment-provider"></a>Provider pathSegment

Questo provider annida i file con un'estensione aggiuntiva in un file senza estensione aggiuntiva. L'estensione aggiuntiva può essere visualizzata solo al centro del nome file completo. Si consideri l'esempio seguente:

![Regole dell'esempio pathSegment](media/filenesting_pathsegment.png) ![Effetto dell'esempio pathSegment](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* viene annidato in *jquery.js* per la regola di **pathSegment**

### <a name="the-allextensions-provider"></a>Provider allExtensions

Questo provider consente di definire regole di annidamento file per i file con qualsiasi estensione ma con lo stesso nome file di base. Si consideri l'esempio seguente:

![Regole dell'esempio allExtensions](media/filenesting_allextensions.png) ![Effetto dell'esempio allExtensions](media/filenesting_allextensions_effect.png)

* *template.cs* e *template.doc* vengono annidati in *template.tt* per la regola di **allExtensions**.

### <a name="the-filetofile-provider"></a>Provider fileToFile

Questo provider consente di definire regole di annidamento file in base a nomi file interi. Si consideri l'esempio seguente:

![Regole dell'esempio fileToFile](media/filenesting_filetofile.png) ![Effetto dell'esempio fileToFile](media/filenesting_filetofile_effect.png)

* *.bowerrc* viene annidato in *bower.json* a causa della regola **fileToFile**

### <a name="rule-order"></a>Ordine delle regole

L'ordine è importante in ogni parte del file di impostazioni personalizzate. È possibile modificare l'ordine di esecuzione delle regole spostandole verso l'alto o verso il basso all'interno del nodo **dependentFileProvider**. Se, ad esempio, una regola rende **file.js** elemento padre di **file.ts** e un'altra regola rende **file.coffee** elemento padre di **file.ts**, l'ordine in cui le regole compaiono nel file determina il comportamento di annidamento quando tutti e tre i file sono presenti. Poiché **file.ts** può avere un solo elemento padre, viene applicata la prima regola in ordine di esecuzione.

L'ordine è importante anche per le sezioni delle regole stesse, non solo per i file all'interno di una sezione. Non appena una coppia di file soddisfa una regola di annidamento file, le regole successive nel file vengono ignorate e viene elaborata la coppia di file successiva.

### <a name="file-nesting-button"></a>Pulsante di annidamento file

È possibile gestire tutte le impostazioni, incluse le impostazioni personalizzate, con lo stesso pulsante in **Esplora soluzioni**:

![Attivare regole di annidamento file personalizzate](media/filenesting_activatecustom.png)

## <a name="create-solution-specific-and-project-specific-settings"></a>Creare impostazioni specifiche di soluzione e di progetto

È possibile creare impostazioni specifiche di progetto e di soluzione tramite il menu di scelta rapida di ogni soluzione e progetto:

![Regole di annidamento specifiche di progetto e soluzione](media/filenesting_solutionprojectspecific.png)

Le impostazioni specifiche di progetto e di soluzione vengono combinate con le impostazioni di Visual Studio attive. Anche se, ad esempio, il file di impostazioni specifiche del progetto è vuoto, **Esplora soluzioni** effettua comunque l'annidamento file. Il comportamento di annidamento deriva dalle impostazioni specifiche della soluzione o dalle impostazioni di Visual Studio. L'ordine di precedenza per l'unione delle impostazioni di annidamento file è: Visual Studio > Soluzione > Progetto.

È possibile impostare Visual Studio in modo che ignori le impostazioni specifiche di progetto e di soluzione, anche se sono presenti file nel disco, abilitando l'opzione **Ignora impostazioni della soluzione e del progetto** in **Strumenti**  >  **Opzioni** > **ASP.NET Core** > **Annidamento file**.

È possibile attivare l'impostazione opposta, indicando a Visual Studio di usare *solo* le impostazioni specifiche della soluzione o del progetto, impostando il nodo **radice** su **true**. Visual Studio interromperà l'unione dei file a tale livello e non lo combinerà più con i file in posizione più alta nella gerarchia.

È possibile archiviare le impostazioni specifiche di soluzione e di progetto nel controllo del codice sorgente e condividerle con tutto il team che lavora sulla codebase.

## <a name="disable-global-file-nesting-rules-for-a-particular-solution-or-project"></a>Disabilitare regole di annidamento file globali per una soluzione o un progetto specifico

È possibile disabilitare regole di annidamento file globali esistenti per progetti o soluzioni specifiche tramite l'azione **remove** anziché l'azione **add** per un provider. Se, ad esempio, si aggiunge il codice di impostazioni seguente a un progetto, tutte le regole **pathSegment** eventualmente esistenti a livello globale vengono disabilitate per il progetto specifico:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Vedere anche

- [Personalizzare l'IDE](../ide/personalizing-the-visual-studio-ide.md)
