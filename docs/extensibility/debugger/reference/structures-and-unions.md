---
title: Strutture e unioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2da39e0327f9a0be2cf0f61227de5ea51af03285
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329122"
---
# <a name="structures-and-unions"></a>Strutture e unioni
Di seguito sono strutture e unioni in Visual Studio Debugging SDK.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) specifica l'ID di processo, che può essere un ID di sistema o un GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) vengono descritte le condizioni in cui viene attivato un punto di interruzione.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) descrive la risoluzione di un punto di interruzione errore, tra cui percorso programma e thread.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) specifica il tipo di struttura utilizzata per descrivere la posizione del punto di interruzione.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) definisce i componenti che descrivono la posizione di un punto di interruzione in un indirizzo nel codice.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) descrive la posizione di un punto di interruzione che è associato direttamente a un indirizzo nel programma sottoposto a debug.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) descrive la posizione di un punto di interruzione alla riga in un file di codice sorgente.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) descrive la posizione di offset di un punto di interruzione in una funzione nel codice.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) utilizzata per impostare i punti di interruzione di codice basati su una stringa che l'utente può immettere dall'IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) utilizzata per impostare i punti di interruzione dei dati che si basano su una stringa che l'utente può immettere dall'IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) descrive la risoluzione di un punto di interruzione in una posizione specifica.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) descrive il numero e le condizioni in cui verrà attivato un punto di interruzione dopo aver visto in precedenza è stata passata.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) contiene le informazioni necessarie per implementare un punto di interruzione.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) contiene le informazioni necessarie per implementare un punto di interruzione (stesso come il [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struttura ma include informazioni sul GUID, vincoli e punto di analisi di fornitore).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) descrive la posizione di un punto di interruzione del codice.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) descrive il risultato dell'associazione di un punto di interruzione dei dati.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) descrive le informazioni di punto di interruzione associato per un punto di interruzione del codice o un punto di interruzione dei dati.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) specifica la struttura del percorso di risoluzione dei punti di interruzione.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) descrive una matrice di stringhe.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) specifica informazioni su un tipo di campo impiegato dai metadati.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) descrive una chiamata a una funzione o metodo.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) descrive il computer in cui il debugger è in esecuzione.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) descrive un elenco di GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) descrive un contesto in memoria o il contesto del codice.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) descrive un indirizzo in un programma in fase di debug.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) rappresenta uno dei numerosi tipi diversi di indirizzi.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) identifica un visualizzatore personalizzato o Visualizzatore di tipi.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) descrive una proprietà di debug che a sua volta descrive un oggetto di natura gerarchica con nome, tipo e valore.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) descrive un riferimento.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) descrive disassembly all'IDE per la visualizzazione.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) descrive un errore di eccezione o di run-time generato dal programma in fase di debug.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) descrive una variabile locale, parametro o altri campi.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) descrive uno stack frame.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) descrive una matrice di identificatori univoci per i motori di debug disponibili.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) utilizzato per impostare le informazioni di JustMyCode per un modulo.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) descrive uno specifico computer.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) descrive un elemento della matrice all'interno di una matrice.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) descrive l'indirizzo di un campo di una classe o struttura.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) descrive l'indirizzo di una variabile locale all'interno di un ambito (in genere una funzione o metodo).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) descrive l'indirizzo di un metodo di una classe.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) descrive un parametro di un metodo o funzione.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) descrive un valore restituito da un metodo o funzione.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) descrive un tipo di campo impiegato dai metadati.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) descrive un particolare modulo (DLL, EXE o assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) vengono fornite informazioni di stato su percorsi di ricerca dei simboli che sono stati cercati.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) descrive un indirizzo nativo.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) descrive un tipo di campo impiegato da un simbolo PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) descrive lo stato di un punto di interruzione che è pronto per l'associazione in un percorso di codice.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) descrive un processo.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) contiene un elenco delle [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) gli oggetti che rappresentano i nodi di programma.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) descrive i processi in esecuzione in un computer.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) descrive la posizione di riga e colonna in testo specificato.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) vengono descritte le proprietà di un thread.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) descrive un tipo di campo.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) descrive un indirizzo fisico.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) descrive un indirizzo che fa riferimento a un `this` puntatore (`Me` in Visual Basic).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h sh.h o ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)