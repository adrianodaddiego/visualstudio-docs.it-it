---
title: Funzione SccGetEvents | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c8c3c08311c8dd359acaed18decc046354e7f37
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332035"
---
# <a name="sccgetevents-function"></a>Funzione SccGetEvents
Questa funzione recupera un evento di stato in coda.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Parametri
 pvContext

[in] La struttura del contesto plug-in del controllo origine.

 lpFileName

[in, out] Buffer in cui il plug-in del controllo del codice sorgente inserisce il nome del file restituito (un massimo di caratteri di MAX_PATH).

 lpStatus

[in, out] Restituisce il codice di stato (vedere [File di codice di stato](../extensibility/file-status-code-enumerator.md) per i valori possibili).

 pnEventsRemaining

[in, out] Restituisce i numero di voci lasciato nella coda dopo questa chiamata. Se questo numero è elevato, il chiamante può decidere di chiamare il [SccQueryInfo](../extensibility/sccqueryinfo-function.md) per ottenere tutte le informazioni in una sola volta.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Ottenere gli eventi ha avuto esito positivo.|
|SCC_E_OPNOTSUPPORTED|Questa funzione non è supportata.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Note
 Questa funzione viene chiamata durante l'elaborazione inattive per vedere se sono state apportate eventuali aggiornamenti di stato per i file di controllo del codice sorgente. Il plug-in del controllo del codice sorgente gestisce lo stato di tutti i file di che cui è a conoscenza e ogni volta che una modifica di stato viene segnalato tramite il plug-in, lo stato e i file associato vengono archiviati in una coda. Quando si `SccGetEvents` viene chiamato, la parte superiore dell'elemento della coda viene recuperato e restituito. Questa funzione è vincolata da restituire solo le informazioni precedentemente memorizzata nella cache e deve avere molto rapidi (vale a dire, senza la lettura del disco o che richiede il controllo del codice sorgente per lo stato); in caso contrario, le prestazioni dell'IDE potrebbero avviarsi per ridurre le prestazioni.

 Se non sono presenti aggiornamenti di stato al report, il plug-in del controllo del codice sorgente archivia una stringa vuota nel buffer a cui punta `lpFileName`. In caso contrario, il plug-in vengono archiviati il nome e percorso completo del file per cui è stato modificato le informazioni sullo stato e restituisce il codice di stato appropriato (uno dei valori descritti in dettaglio in [File di codice di stato](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di stato file](../extensibility/file-status-code-enumerator.md)