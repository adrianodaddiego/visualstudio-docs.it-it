---
title: Interfaccia IWefDebuggingSupport
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a71adf5371275fbbdc19cdf09be96ef900ec073d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583763"
---
# <a name="iwefdebuggingsupport-interface"></a>Interfaccia IWefDebuggingSupport
  Implementata da un ambiente di debug, ad esempio Visual Studio, per facilitare il debug delle App per Office. L'applicazione di Office, ad esempio Word o Excel, ottiene questa interfaccia da Visual Studio e quindi chiama i metodi sull'interfaccia in determinati momenti durante la sessione di debug.

## <a name="syntax"></a>Sintassi

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>Metodi
 Nella tabella seguente elenca i metodi che definisce l'interfaccia IWefDebuggingSupport.

|Nome|Descrizione|
|----------|-----------------|
|[Metodo GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Ottiene informazioni sulle App per Office che devono essere inseriti automaticamente durante il debug.|
|[Metodo SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornisce l'identificatore di processo che eseguirà il contenuto Web estensioni Framework (WCF).|
