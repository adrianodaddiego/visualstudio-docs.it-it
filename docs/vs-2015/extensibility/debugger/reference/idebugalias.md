---
title: IDebugAlias | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6c05b6987804681176abdde0e8c94a7463a9163c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442311"
---
# <a name="idebugalias"></a>IDebugAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Rappresenta un alias per una variabile numerico. Un alias è semplicemente un nome diverso per una variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni (EE) implementa questa interfaccia per supportare gli alias di numerici per le variabili.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) crea un alias per un particolare oggetto. Per cercare gli alias, usare [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) oppure [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 I metodi seguenti sono definiti nel `IDebugAlias` interfaccia.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Ottiene l'oggetto a cui fa riferimento l'alias.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Ottiene il nome dell'alias.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Recupera un `ICorDebugValue` interfaccia che fornisce l'accesso a managed informazioni codice su questo oggetto (solo codice gestito).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Contrassegna questo alias come non più in uso.|  
  
## <a name="remarks"></a>Note  
 Un alias è un numero decimale in formato stringa seguita dal carattere #, ad esempio, & 1001.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
