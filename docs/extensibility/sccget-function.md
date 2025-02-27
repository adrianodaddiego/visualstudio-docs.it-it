---
title: Funzione SccGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ad087af24723c6ccbf901280c7db748e2af461a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332130"
---
# <a name="sccget-function"></a>Funzione SccGet
Questa funzione recupera una copia di uno o più file per la visualizzazione e la compilazione ma non per la modifica. Nella maggior parte dei sistemi, i file vengono contrassegnati come di sola lettura.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura scelta del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.

 nFiles

[in] Numero di file specificato per il `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi completi di file da recuperare.

 fOptions

[in] Flag di comando (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).

 pvOptions

[in] Opzioni specifiche plug-in controllo sorgente.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Esito positivo dell'operazione get.|
|SCC_E_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|
|SCC_E_FILEISCHECKEDOUT|Impossibile ottenere il file che l'utente attualmente è estratto.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|
|SCC_E_NOSPECIFIEDVERSION|Versione non valida o data/ora specificati.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. file non è stata sincronizzata.|
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|

## <a name="remarks"></a>Note
 Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da recuperare. Se l'IDE passa il flag `SCC_GET_ALL`, questo significa che gli elementi in `lpFileNames` non sono file, ma le directory e che tutti i file in controllo del codice sorgente nella directory specificata devono essere recuperate.

 Il `SCC_GET_ALL` flag può essere combinato con il `SCC_GET_RECURSIVE` flag per recuperare tutti i file nella directory specificata e anche tutte le sottodirectory.

> [!NOTE]
> `SCC_GET_RECURSIVE` non deve mai essere passato senza `SCC_GET_ALL`. Si noti inoltre che se le directory *C:\A* e *C:\A\B* vengono passati in una richiesta get ricorsiva, *C:\A\B* e tutte le relative sottodirectory verranno effettivamente recuperate due volte. È responsabilità dell'IDE, e non l'origine di controllo del plug-in, ovvero per assicurarsi che i duplicati di questo vengono mantenuti all'esterno della matrice.

 Infine, anche se i plug-in del controllo del codice sorgente specificato il `SCC_CAP_GET_NOUI` flag durante l'inizializzazione, che indica che non dispone di un'interfaccia utente per un comando Get, questa funzione può comunque essere chiamata dall'IDE per recuperare i file. Il flag indica semplicemente che l'IDE non viene visualizzata una voce di menu Get e che il plug-in non è previsto fornire qualsiasi interfaccia utente.

## <a name="rename-files-and-sccget"></a>Rinominare file e SccGet
 Situazione: un utente estrae un file, ad esempio, *txt*e lo modifica. Prima di *txt* può essere controllato in un secondo utente Rinomina *txt* al *b. txt* nel database di controllo di origine, viene estratto *b. txt*, rende alcune modifiche al file e archivia il file. Il primo utente richiede le modifiche apportate dall'utente secondo, in modo che il primo utente rinomina la versione locale di *txt* del file ai *b. txt* ed esegue un'operazione get sul file. Tuttavia, la cache locale che tiene traccia dei numeri di versione continua a ritenere la prima versione di *txt* vengono archiviati in locale e in modo da controllo del codice sorgente non è possibile risolvere le differenze.

 Esistono due modi per risolvere questa situazione in cui la cache locale delle versioni di controllo di origine diventa sincronizzata con il database del controllo del codice sorgente:

1. Non consentire la ridenominazione di un file nel database di controllo di origine che è attualmente estratto.

2. È l'equivalente di "eliminazione precedente" seguita da "Aggiungi nuovo". L'algoritmo seguente è un modo per eseguire questa operazione.

    1. Chiamare il [SccQueryChanges](../extensibility/sccquerychanges-function.md) funzione per apprendere la ridenominazione dei *txt* al *b. txt* nel database di controllo di origine.

    2. Rinominare locale *txt* al *b. txt*.

    3. Chiamare il `SccGet` funzione per entrambe *txt* e *b. txt*.

    4. In quanto *txt* non esiste nel database di controllo di origine, viene eliminata la cache della versione locale di parametro mancante *txt* informazioni sulla versione.

    5. Il *b. txt* file venga estratto viene unito con il contenuto dell'elemento locale *b. txt* file.

    6. Aggiornato *b. txt* file può ora essere archiviati.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
