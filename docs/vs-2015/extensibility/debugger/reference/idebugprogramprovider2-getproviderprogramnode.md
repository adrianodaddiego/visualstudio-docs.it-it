---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fa9f4db6aa71e9bba1f456b13ba52abd24ab966
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966284"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera il nodo di programma per un programma specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `Flags`  
 [in] Una combinazione di flag dal [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) enumerazione. I flag seguenti sono più comuni per questa chiamata:  
  
|Flag|Descrizione|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Chiamante è in esecuzione nel computer remoto.|  
|`PFLAG_DEBUGGEE`|Chiamante è in corso il debug (verranno restituite informazioni aggiuntive sul marshalling per ogni nodo).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Chiamante è stato collegato a ma non avviare dal debugger.|  
  
 `pPort`  
 [in] La porta del processo chiamante è in corso.  
  
 `processId`  
 [in] Un' [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura che contiene l'ID del processo che contiene il programma in questione.  
  
 `guidEngine`  
 [in] GUID del motore di debug che il programma è associato (se presente).  
  
 `programId`  
 [in] ID del programma per cui ottenere il nodo di programma.  
  
 `ppProgramNode`  
 [out] Un' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto che rappresenta il nodo programma richiesto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
