---
title: Funzione SccAdd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: daac15bbb7829d510db17ba02057a2dc86c55990
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432501"
---
# <a name="sccadd-function"></a>Funzione SccAdd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione consente di aggiungere nuovi file al sistema di controllo di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 nFiles  
 [in] Numero di file selezionati da aggiungere al progetto corrente come specificato nella `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice dei nomi locali completi del file da aggiungere.  
  
 lpComment  
 [in] Il commento da applicare a tutti i file da aggiungere.  
  
 pfOptions  
 [in] Matrice di flag dei comandi, disponibile su base file per file.  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'operazione di aggiunta è riuscita.|  
|SCC_E_FILEALREADYEXISTS|Il file selezionato è già incluso nel controllo sorgente.|  
|SCC_E_TYPENOTSUPPORTED|Il tipo del file (ad esempio, binario) non è supportato dal sistema di controllo di origine.|  
|SCC_E_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. aggiungere non eseguita.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
|SCC_E_FILENOTEXIST|File locale non è stato trovato.|  
  
## <a name="remarks"></a>Note  
 Le consuete `fOptions` vengono sostituiti seguito da una matrice `pfOptions`, con uno `LONG` opzione specifica per ogni file. Questo avviene perché il tipo di file può variare da un file in un file.  
  
> [!NOTE]
> Non è consentito specificare entrambe `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` opzioni per lo stesso file, ma è consentito specificare nessuno. L'impostazione Nessuna delle due è la stessa impostazione `SCC_FILETYPE_AUTO`, nel qual caso il controllo origine plug-in rileva automaticamente il tipo di file.  
  
 Ecco l'elenco di flag utilizzati nel `pfOptions` matrice:  
  
|Opzione|Value|Significato|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Il plug-in del controllo del codice sorgente deve rilevare il tipo di file.|  
|SCC_FILETYPE_TEXT|0x01|Indica un file di testo ASCII.|  
|SCC_FILETYPE_BINARY|0x02|Indica un tipo di file diversi dal testo ASCII.|  
|SCC_ADD_STORELATEST|0x04|Archivia solo l'ultima copia del file, non i delta.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Gestisce il file come testo ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Gestisce il file come testo Unicode in formato UTF8.|  
|SCC_FILETYPE_UTF16LE|0x20|Gestisce il file come testo Unicode in formato UTF16 Little Endian formato.|  
|SCC_FILETYPE_UTF16BE|0x40|Considera formattare il file come testo Unicode in UTF16 Big Endian.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
