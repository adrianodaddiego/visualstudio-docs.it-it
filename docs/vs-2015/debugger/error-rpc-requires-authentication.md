---
title: 'Errore: RPC richiede autenticazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535736"
---
# <a name="error-rpc-requires-authentication"></a>Errore: RPC richiede autenticazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debugger di Visual Studio non può connettersi al computer remoto. I criteri RPC abilitati sul computer locale impediscono il debug remoto.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. Eseguire `\` *windir*`\system32\regedt32.exe`  
  
2. Individuare ed eliminare `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3. Riavviare il computer per rendere effettiva la modifica del Registro di sistema.  
  
4. Se il problema persiste, contattare l'amministratore di dominio sui **configurazione Computer -> modelli amministrativi - > sistema -> Remote Procedure Call -> restrizioni per i client RPC non autenticati** gruppo impostazione dei criteri.
