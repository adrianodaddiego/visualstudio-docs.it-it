---
title: Funzione SccWillCreateSccFile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb0df475098a0fb0675327cece6dd9c643a0c4d7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967671"
---
# <a name="sccwillcreatesccfile-function"></a>Funzione SccWillCreateSccFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione determina se il controllo del codice sorgente del plug-in supporta la creazione del MSSCCPRJ. File di controllo del codice sorgente per ogni file specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto del plug-in controllo di origine.  
  
 nFiles  
 [in] Il numero di nomi di file inclusi nel `lpFileNames` matrice, nonché la lunghezza del `pbSccFiles` matrice.  
  
 lpFileNames  
 [in] Una matrice di nomi di file completo per verificare (matrice deve essere allocata dal chiamante).  
  
 pbSccFiles  
 [in, out] Matrice in cui archiviare i risultati.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata.|  
|SCC_E_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene chiamata con un elenco di file per determinare se il plug-in del controllo del codice sorgente fornisce il supporto nel MSSCCPRJ. File di controllo del codice sorgente per ogni file specifici (per ulteriori informazioni sul MSSCCPRJ. File di controllo del codice sorgente, vedere [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md)). Plug-in controllo codice sorgente può dichiarare se hanno la possibilità di creare MSSCCPRJ. File SCC dichiarando `SCC_CAP_SCCFILE` durante l'inizializzazione. Il plug-in restituisce `TRUE` oppure `FALSE` per ogni file nei `pbSccFiles` matrice per indicare che il file specificato hanno MSSCCPRJ. Supporto di SCC. Se il plug-in restituisce un codice di riuscita dalla funzione, vengono rispettati i valori nella matrice restituita. In caso di errore, la matrice viene ignorata.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
