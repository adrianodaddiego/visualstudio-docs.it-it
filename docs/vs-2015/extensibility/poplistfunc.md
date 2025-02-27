---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c3ae2ce451f076c33ea5613b71c6d262c1d7a0e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430830"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo callback viene fornito per il [SccPopulateList](../extensibility/sccpopulatelist-function.md) dall'IDE e viene usato per il plug-in del controllo del codice sorgente per aggiornare un elenco di file o directory (anche fornito al `SccPopulateList` (funzione)).  
  
 Quando un utente sceglie il **ottenere** comando nell'IDE, l'IDE visualizza una casella di riepilogo di tutti i file che l'utente può ottenere. Sfortunatamente, l'IDE non conosce l'elenco esatto di tutti i file che è possibile che venga visualizzato all'utente; solo il plug-in dispone di questo elenco. Se altri utenti aggiunti file al progetto di controllo del codice sorgente, questi file dovrebbero essere visualizzati nell'elenco, ma l'IDE non saperlo. L'IDE compila un elenco dei file che ritiene che l'utente può ottenere. Prima di visualizzare l'elenco all'utente, chiama il [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` offrendo il plug-in del controllo del codice sorgente possibilità di aggiungere ed eliminare i file dall'elenco.  
  
## <a name="signature"></a>Signature  
 Il plug-in del controllo del codice sorgente consente di modificare l'elenco chiamando una funzione dell'IDE implementate con il seguente prototipo:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parametri  
 pvCallerData  
 Il `pvCallerData` parametro passato dal chiamante (IDE) per il [SccPopulateList](../extensibility/sccpopulatelist-function.md). Il plug-in del controllo del codice sorgente deve presupporre niente sul contenuto di questo parametro.  
  
 fAddRemove  
 Se `TRUE`, `lpFileName` è un file che deve essere aggiunti all'elenco dei file. Se `FALSE`, `lpFileName` è un file che deve essere eliminato dall'elenco dei file.  
  
 nStatus  
 Stato del `lpFileName` (una combinazione del `SCC_STATUS` bits, vedere [codice di stato File](../extensibility/file-status-code-enumerator.md) per informazioni dettagliate).  
  
 lpFileName  
 Percorso completo della directory il nome del file per aggiungere o eliminare dall'elenco.  
  
## <a name="return-value"></a>Valore restituito  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`TRUE`|Il plug-in possono continuare a chiamare questa funzione.|  
|`FALSE`|Si è verificato un problema sul lato dell'IDE (ad esempio di situazione di memoria insufficiente). Il plug-in deve arrestare l'operazione.|  
  
## <a name="remarks"></a>Note  
 Per ogni file che deve essere il plug-in del controllo del codice sorgente da aggiungere o eliminare dall'elenco dei file, chiama questa funzione, passando il `lpFileName`. Il `fAddRemove` flag indica un nuovo file da aggiungere all'elenco o un vecchio file da eliminare. Il `nStatus` parametro fornisce lo stato del file. Quando il plug-in del controllo del codice sorgente ha terminato l'aggiunta ed eliminazione di file, restituisce il [SccPopulateList](../extensibility/sccpopulatelist-function.md) chiamare.  
  
> [!NOTE]
> Il `SCC_CAP_POPULATELIST` bit funzionalità è necessaria per Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Codice di stato dei file](../extensibility/file-status-code-enumerator.md)
