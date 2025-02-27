---
title: Comando CodeIndex
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d472ec7d35b886dbc2294d2c3172b61d3b1e7702
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974956"
---
# <a name="codeindex-command"></a>Comando CodeIndex

Usare il comando **CodeIndex** per gestire l'indicizzazione del codice in Team Foundation Server. Ad esempio, è possibile che si desideri reimpostare l'indice per correggere le informazioni di CodeLens o disabilitare l'indicizzazione per esaminare eventuali problemi di prestazioni del server.

## <a name="required-permissions"></a>Autorizzazioni necessarie

Per usare il comando **CodeIndex**, è necessario essere membro del gruppo di sicurezza **Team Foundation Administrators** . Vedere [Permissions and groups in Azure DevOps and TFS](/azure/devops/organizations/security/permissions?view=vsts) (Autorizzazioni e gruppi in Azure DevOps e TFS).

> [!NOTE]
> Anche se si accede con le credenziali amministrative, per eseguire questo comando, è necessario aprire una finestra del prompt dei comandi con privilegi elevati. È inoltre necessario eseguire questo comando dal livello applicazione di Team Foundation.

## <a name="syntax"></a>Sintassi

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parametri

|**Argomento**|**Descrizione**|
|------------------| - |
|`CollectionName`|Specifica il nome della raccolta di progetti. Se il nome contiene spazi, racchiuderlo tra virgolette, ad esempio, "Sito Web di Fabrikam".|
|`CollectionId`|Specifica il numero di identificazione della raccolta di progetti.|
|`ServerPath`|Specifica il percorso di un file di codice.|

|**Opzione**|**Descrizione**|
|----------------| - |
|**/indexingStatus**|Mostrare lo stato e la configurazione del servizio di indicizzazione del codice.|
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on**: avviare l'indicizzazione di tutti gli insiemi di modifiche.<br />-   **off**: arrestare l'indicizzazione di tutti gli insiemi di modifiche.<br />-   **keepupOnly**: arrestare l'indicizzazione degli insiemi di modifiche creati in precedenza e avviare l'indicizzazione solo dei nuovi insiemi di modifiche.|
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> È possibile usare il carattere jolly (*) all'inizio, alla fine, oppure a entrambe le estremità del percorso server.|Specifica l'elenco di file di codice e i rispettivi percorsi da non indicizzare.<br /><br /> -   **add**: aggiungere il file da non indicizzare all'elenco di file ignorati.<br />-   **remove**: rimuovere il file da indicizzare dall'elenco di file ignorati.<br />-   **removeAll**: cancellare l'elenco dei file ignorati e avviare l'indicizzazione di tutti i file.<br />-   **view**: visualizzare tutti i file non sottoposti a indicizzazione.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Mostra il numero specificato di file che supera la dimensione specificata in KB. È quindi possibile usare l'opzione **/ignoreList** per escludere questi file dall'indicizzazione.|
|**/reindexAll**|Cancellare i dati indicizzati in precedenza e riavviare l'indicizzazione.|
|**/destroyCodeIndex [/noPrompt]**|Eliminare l'indice del codice e rimuovere tutti i dati indicizzati. Non è richiesta conferma se si usa l'opzione **/noPrompt**.|
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|Controllare la quantità di dati temporanei creati da CodeLens durante l'elaborazione degli insiemi di modifiche. Il limite predefinito è 2 GB.<br /><br /> -   **view**: mostrare il limite di dimensioni attuale.<br />-   `SizeInGBs`: modificare il limite di dimensioni.<br />-   **disable**: rimuovere il limite di dimensioni.<br /><br /> Questo limite viene verificato prima dell'elaborazione di un nuovo insieme di modifiche con CodeLens. Se i dati temporanei superano questo limite, CodeLens sospende l'elaborazione degli insiemi di modifiche precedenti, non di quelli nuovi. CodeLens riavvia l'elaborazione dopo che i dati sono stati puliti e sono tornati sotto il limite. La pulizia viene eseguita automaticamente una volta al giorno. Questo implica che i dati temporanei potrebbero superare questo limite prima dell'esecuzione del processo di pulizia.|
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|Controllare la lunghezza dell'intervallo di indicizzazione della cronologia delle modifiche. Ciò incide sulla quantità di cronologia che CodeLens mostra all'utente. Il limite predefinito è di 12 mesi. Questo significa che CodeLens mostra la cronologia delle modifiche solo degli ultimi 12 mesi.<br /><br /> -   **view**: mostrare il numero di mesi corrente.<br />-   **all**: indicizzare tutta la cronologia modifiche.<br />-   `NumberOfMonths`: modificare il numero di mesi usato per la cronologia modifiche di indice.|
|**/collectionName:** `CollectionName`|Specifica il nome dell'insieme di progetti sulla quale eseguire il comando **CodeIndex**. Obbligatoria se non si usa **/CollectionId**.|
|**/collectionId:** `CollectionId`|Specifica il numero di identificazione dell'insieme di progetti sulla quale eseguire il comando **CodeIndex**. Obbligatoria se non si usa **/CollectionName**.|

## <a name="examples"></a>Esempi

> [!NOTE]
> Ogni riferimento a società, organizzazioni, prodotti, nomi di dominio, indirizzi di posta elettronica, logo, persone, luoghi ed eventi è puramente casuale.  Nessuna associazione con nessuna società, organizzazione, prodotto, nome di dominio, indirizzo di posta elettronica, logo, persona, luogo o evento è intenzionale o può essere presupposta.

 Per vedere la configurazione e lo stato di indicizzazione del codice:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

 Per avviare l'indicizzazione di tutti gli insiemi di modifiche:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

 Per arrestare l'indicizzazione dei set di modifiche creati in precedenza e avviare l'indicizzazione solo dei nuovi insiemi di modifiche:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

 Per trovare fino a 50 file con dimensioni superiori a 10 KB:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

 Per escludere un file specifico dall'indicizzazione e aggiungerlo all'elenco di file ignorati:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

 Per visualizzare tutti i file non sottoposti a indicizzazione:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

 Per cancellare i dati precedentemente indicizzati e riavviare l'indicizzazione:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

 Per salvare tutta la cronologia dell'insieme di modifiche:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

 Per rimuovere il limite di dimensioni nei dati temporanei di CodeLens e continuare l'indicizzazione indipendentemente dalle dimensioni dei dati temporanei:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

 Per eliminare l'indice di codice con conferma:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Vedere anche

- [Trovare le modifiche apportate al codice e altri elementi della cronologia con CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)
- [Managing server configuration with TFSConfig](/tfs/server/ref/command-line/tfsconfig-cmd) (Gestione della configurazione del server con TFSConfig)