---
title: Provider di simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65debb8fcb41bec1d42c82654c26bc7d19c04a67
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348511"
---
# <a name="symbol-provider"></a>Provider di simboli
Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug sui simboli generate dal compilatore del linguaggio per poter valutare variabili ed espressioni. Esegue l'operazione utilizzando le interfacce di un provider di simboli (SP), chiamato anche un gestore di simboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce stored procedure per codice gestito e codice nativo usando il formato di file di simboli di DataBase di programma (PDB). A meno che non vi è un forte necessaria al programma usare i simboli archiviati in un formato personalizzato, è consigliabile usare il Service Pack forniti da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="implementation-notes"></a>Note di implementazione
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug che prevede di comunicare con il Service Pack utilizzando le interfacce di Common Language Runtime (CLR). Di conseguenza, un Service Pack che verranno usate con i motori di debug di Visual Studio deve supportare il CLR. Un elenco completo di tutte le interfacce di debug di CLR è reperibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].

 Se il SP userà solo il motore di debug personalizzato, è possibile implementare stored procedure nel modo desiderato a seconda delle esigenze del motore di debug.

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)