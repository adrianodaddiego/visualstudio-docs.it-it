---
title: IEEVisualizerService::GetCustomViewerList | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c2ee2682b04b03b2b0bb04e0ba9ef5d9a2df8a35
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969111"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo restituisce un elenco di visualizzatori di tipi noti al servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celtSkip`  
 [in] Numero di visualizzatori di ignorare.  
  
 `celRequested`  
 [in] Numero di visualizzatori da recuperare (specifica anche dimensioni del `rgViewers` matrice).  
  
 `rgViewers`  
 [in, out] Matrice di [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) strutture da compilare.  
  
 `pceltFetched`  
 [out] Numero di visualizzatori effettivamente recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) passa la richiesta a questo metodo come parte del supporto per i visualizzatori di tipo. Se l'analizzatore di espressioni fornisce anche i visualizzatori personalizzati per lo stesso tipo, è possibile aggiungere in modo appropriato compilato [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) strutture per i visualizzatori personalizzati all'elenco. Verificare che l'opzione [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) riflette i visualizzatori aggiuntivi.  
  
 Visualizzare [Visualizzatore di tipi e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) per informazioni dettagliate sulle differenze tra i visualizzatori e visualizzatori.  
  
## <a name="see-also"></a>Vedere anche  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
