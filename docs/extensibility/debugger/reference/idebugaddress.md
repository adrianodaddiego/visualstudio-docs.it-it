---
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653d2424d21a18e7053f66e0a74214ecc25d97da
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317926"
---
# <a name="idebugaddress"></a>IDebugAddress
Questa interfaccia rappresenta l'indirizzo di un elemento. Viene restituito dal gestore di simboli.

## <a name="syntax"></a>Sintassi

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia per rappresentare un indirizzo di un oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Molti metodi sul numero di interfacce restituiscono questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera una [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura che descrive un oggetto e il relativo percorso.|

## <a name="remarks"></a>Note
 Il provider di simboli restituisce questa interfaccia per rappresentare un oggetto e la relativa posizione all'interno di un particolare ambito (ad esempio, funzione, metodo o classe). Questa interfaccia viene restituita dal e passata ai vari metodi del provider di simboli di espressione dell'analizzatore di espressioni. In genere, il provider di simboli è l'unica entità che è necessario interpretare il contenuto di questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)