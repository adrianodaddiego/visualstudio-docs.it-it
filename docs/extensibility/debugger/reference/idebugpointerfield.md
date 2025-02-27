---
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc6939296fa2bfa59aad1824529f8b708a4cd5cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308855"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Questa interfaccia rappresenta un tipo di puntatore.

## <a name="syntax"></a>Sintassi

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il provider di simboli implementa questa interfaccia per rappresentare un puntatore.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Uso [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dalle [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce `FIELD_TYPE_POINTER`.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nel `IDebugField` e `IDebugContainerField` interfacce, questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive la destinazione dell'indicatore di misura.|

## <a name="remarks"></a>Note
 In C/C++, un puntatore può essere un contenitore, se viene usato con la notazione di matrice. Ad esempio, dato `char *pString`, `pString` dispone di un tipo di puntatore a `char`. `pString[3]` ha il tipo di un contenitore che è un puntatore a `char` che fa riferimento il quarto elemento di tale contenitore.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)