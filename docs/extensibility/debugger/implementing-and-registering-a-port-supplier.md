---
title: Implementazione e registrazione di un fornitore di porte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26767193c4489405432054ee94beb195ce8448d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344262"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementare e registrare un fornitore di porte
Il ruolo di un fornitore di porte consiste nel tenere traccia e specificare le porte, che a sua volta la gestione dei processi. Quando è necessario creare una porta, il fornitore della porta viene creata un'istanza usando CoCreate con GUID del fornitore della porta (gestore di sessione di debug [SDM] utilizzerà il fornitore della porta che l'utente ha selezionato o il fornitore della porta specificato dal sistema del progetto). Chiama quindi il modello SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) per vedere se è possono aggiungere tutte le porte. Se è possibile aggiungere una porta, viene richiesta una nuova porta chiamando [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta. `AddPort` Restituisce una nuova porta rappresentata da un' [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia.

## <a name="discussion"></a>Discussione
 Viene creata una porta da un fornitore di porte, che è associato a un server macchina o di debug. Un server enumera i suoi fornitori porta tramite il[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) metodo e un fornitore di porte enumera le relative porte tramite il [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) (metodo).

 Oltre la normale registrazione COM, un fornitore di porte deve registrarsi con Visual Studio, inserendo il CLSID e il nome in posizioni specifiche del Registro di sistema. Chiamare una funzione helper Debugging SDK `SetMetric` gestisce questo compito ingrato: viene chiamato una volta per ogni elemento da registrare, in questo modo:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Un fornitore di porte Annulla la registrazione di se stessa chiamando `RemoveMetric` (un'altra funzione di supporto Debugging SDK) una volta per ogni elemento che è stato registrato, in questo modo:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> Il [helper SDK per eseguire il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` definite nelle funzioni statiche *dbgmetric.h* e compilate in *ad2de.lib*. Il `metrictypePortSupplier`, `metricCLSID`, e `metricName` helpers sono definiti anche nel *dbgmetric.h*.

 Un fornitore di porte può fornire il nome e GUID tramite i metodi [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), rispettivamente.

## <a name="see-also"></a>Vedere anche
- [Implementare un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Helper SDK per eseguire il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)