---
title: La registrazione di un oggetto personalizzato di motore di Debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90400a9bf750eb80e40d6558fed382e18e7824ef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316050"
---
# <a name="register-a-custom-debug-engine"></a>Registrare un motore di debug personalizzato
Il motore di debug deve registrarsi come una class factory e le convenzioni COM seguenti, nonché registrare con Visual Studio tramite la sottochiave del Registro di sistema di Visual Studio.

> [!NOTE]
> È possibile trovare un esempio di come registrare l'esempio TextInterpreter, che viene compilato come parte di un motore di debug di [esercitazione: Creazione di un motore di debug tramite ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>Processo server DLL
 Un motore di debug è in genere configurato in un proprio DLL come un server COM. Di conseguenza, il motore di debug prima necessario registrare il CLSID della relativa class factory con COM Visual Studio possono accedervi. Quindi, il motore di debug deve eseguire la registrazione con Visual Studio per stabilire le proprietà, in caso contrario, noti come le metriche, il debug supporta del motore. La scelta delle metriche scritte nella sottochiave del Registro di sistema di Visual Studio dipende dalle funzionalità che supporta il motore di debug.

 [Helper SDK per eseguire il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descrive non solo le posizioni del Registro di sistema necessarie per registrare un motore di debug; vengono inoltre descritte le *dbgmetric.lib* libreria, che contiene un numero di funzioni utili e dichiarazioni per gli sviluppatori C++ che rendono la modifica del Registro di sistema più semplice.

### <a name="example"></a>Esempio
 Nell'esempio seguente (dall'esempio TextInterpreter) illustra come usare il `SetMetric` funzione (da *dbgmetric.lib*) per registrare un motore di debug con Visual Studio. Le metriche vengono passate sono definite anche nel *dbgmetric.lib*.

> [!NOTE]
> TextInterpreter è un motore di debug di base; non configurato e pertanto non registra, ovvero qualsiasi altra funzionalità. Un motore di debug più completato potrebbe avere un elenco di `SetMetric` supporta le chiamate o i rispettivi equivalenti, uno per ogni funzionalità motore di debug.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Vedere anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Helper SDK per eseguire il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Esercitazione: Creazione di un motore di debug tramite COM ATL](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)