---
title: Pagina pubblica, creazione progetti (sviluppo per Office in Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 84a62fc796243172c9130c8113c4e6d289ed3092
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447009"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Pagina pubblica, creazione progetti (sviluppo per Office in Visual Studio)
  La pagina **Pubblica** di **Creazione progetti** viene usata per configurare le proprietà per la distribuzione.

 Per accedere a questa pagina, selezionare il progetto in **Esplora soluzioni**, quindi, nel menu **Progetto** , scegliere *NomeProgetto* **Proprietà**. Se la pagina **Pubblica** non viene visualizzata, scegliere la scheda **Pubblica** .

> [!NOTE]
> È anche possibile impostare il percorso di pubblicazione nella **Pubblicazione guidata**. Per altre informazioni, vedere [Procedura: Distribuire una soluzione Office usando ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).

## <a name="uielement-list"></a>Elenco UIElement
 **Posizione cartella di pubblicazione (sito web, server ftp o percorso file)** necessari.

 La posizione della cartella di pubblicazione è la directory in cui Visual Studio copia i file della soluzione, ad esempio i manifesti, gli assembly e altri file della compilazione. È necessario l'accesso in scrittura a questa directory.

 Le opzioni includono il computer locale, una condivisione file UNC o un sito Web HTTP/HTTPS. Il percorso può essere locale (*c:\foldername\publishfolder*), relativo (*pubblicare\\* ), o un percorso completo ( *\\\servername\foldername* o http://<em>servername/foldername</em>).

 Per impostazione predefinita, è il percorso di pubblicazione *http://localhost/projectname/* se è stato installato, IIS o il *pubblicare\\*  directory se non è installato IIS.

 **URL cartella di installazione** facoltativo.

 L'URL della cartella di installazione è la directory dalla quale l'utente finale installa la personalizzazione. È anche il percorso usato dalla soluzione per controllare la disponibilità di aggiornamenti. Il percorso può essere uguale a quello della cartella di pubblicazione, ma non è obbligatorio.

 Le opzioni includono il computer locale, una condivisione file UNC o un sito Web HTTP/HTTPS. Il percorso può essere locale (*c:\foldername\publishfolder*), relativo (*pubblicare\\* ), o un percorso completo ( *\\\servername\foldername* o http://<em>servername/foldername</em>). Tutti i percorsi HTTP/HTTPS devono essere creati con caratteri US-ASCII. I caratteri Unicode non sono supportati.

 Se il percorso di installazione è impostato, i file di personalizzazione devono trovarsi nel percorso in cui gli utenti installano la personalizzazione. Il percorso deve essere impostato solo se si conosce il percorso di distribuzione finale.

 Se i file di installazione si trovano in un percorso relativo al documento o al programma di installazione, ad esempio l'opzione CD, lasciare vuota questa casella.

 Questo valore può essere assegnato successivamente da un amministratore. Per altre informazioni, vedere [Procedura: Modificare il percorso di installazione di una soluzione Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 **Prerequisiti** i prerequisiti possono essere inclusi nel programma di installazione o scaricati su richiesta durante l'installazione.

- **Scarica prerequisiti dal sito web del fornitore del componente**: Usare questa opzione per scaricare questi prerequisiti da Microsoft.

- **Scarica prerequisiti dallo stesso percorso dell'applicazione**: Usare questa opzione per incorporare i prerequisiti nel programma di installazione. Se i file dei prerequisiti vengono inclusi nel programma di installazione, le dimensioni della soluzione aumentano.

- **Scarica prerequisiti dal seguente percorso**: Usare questa opzione per rendere i prerequisiti disponibili agli utenti finali separatamente tramite un altro programma di installazione in una pagina web o una condivisione di rete.

  **Gli aggiornamenti** l'intervallo di aggiornamento determina la frequenza con cui la soluzione Controlla disponibilità di aggiornamenti. L'impostazione predefinita è ogni sette giorni.

  Il controllo della disponibilità di aggiornamenti ogni volta che viene caricata una personalizzazione a livello di documento o un componente aggiuntivo VSTO manterrebbe aggiornati i componenti, ma influirebbe sulle prestazioni di avvio.

  Se si esegue la distribuzione tramite CD o unità rimovibile, selezionare l'impostazione **Non controllare mai**.

  **Opzioni (descrizione)** impostare le opzioni di pubblicazione per le proprietà seguenti:

- Lingua di pubblicazione: le impostazioni locali della soluzione Office.

- Nome editore: il nome della società o dello sviluppatore, come visualizzato in **Installazione applicazioni** o **Programmi e funzionalità**.

- Nome prodotto: il nome della soluzione Office, come visualizzato in **Installazione applicazioni** o **Programmi e funzionalità**.

- URL supporto tecnico: la posizione che gli utenti finali possono usare per contattare il supporto tecnico per la soluzione Office.

  **Opzioni (impostazioni Office)** impostare le opzioni di pubblicazione per le proprietà seguenti:

- Nome soluzione: il nome della soluzione Office, come visualizzato nell'applicazione di Office.

- Descrizione: la descrizione della soluzione Office, come visualizzata nell'applicazione di Office.

- Comportamento di caricamento del componente aggiuntivo VSTO.

  - Carica all'avvio: specifica che il componente aggiuntivo VSTO viene caricato all'avvio dell'applicazione di Office.

  - Carica su richiesta: specifica che il componente aggiuntivo VSTO viene caricato quando lo richiede l'applicazione, ad esempio quando un utente fa clic su un elemento dell'interfaccia utente che usa la funzionalità nel componente aggiuntivo VSTO.

  **Lingua di pubblicazione** questa opzione imposta la lingua delle condizioni di licenza Software Microsoft e include i language pack nell'elenco dei prerequisiti. Non influisce sulla lingua della personalizzazione. La lingua del programma di installazione viene determinata dalle lingue installate di Visual Studio.

  Per altre informazioni su come modificare la **lingua di pubblicazione**, vedere [come: Modificare la lingua di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Pubblica versione** imposta il numero di versione per la personalizzazione. Quando il numero di versione viene modificato, l'applicazione viene pubblicata come aggiornamento. Viene creata una nuova cartella per ogni versione durante il processo di compilazione per evitare la sovrascrittura della versione precedentemente pubblicata. Ogni parte della versione di pubblicazione (**Principale**, **Secondaria**, **Compilazione**, **Revisione**) può contenere fino a cinque cifre.

  **Incrementa automaticamente revisione a ogni versione** facoltativo. Quando è selezionata (impostazione predefinita), la parte **Revisione** del numero di versione viene incrementata di un'unità ogni volta che viene pubblicata la personalizzazione. In questo modo la personalizzazione viene pubblicata come aggiornamento.

  **Publikovat** pubblica l'applicazione usando le impostazioni correnti. Equivale al pulsante **Fine** nella **Pubblicazione guidata**.

## <a name="see-also"></a>Vedere anche

- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Prerequisiti per la distribuzione di soluzioni Office](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)
