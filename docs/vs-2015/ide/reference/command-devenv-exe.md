---
title: -Command (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a87be2f0b60b02588b5ba73e5837caca1b4bd8ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685838"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esegue il comando specificato dopo l'avvio dell'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Argomenti  
 `CommandName`  
 Obbligatorio. Nome completo di un comando di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o del relativo alias, racchiuso tra virgolette doppie. Per altre informazioni sulla sintassi dei comandi e degli alias, vedere [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Osservazioni  
 Al completamento dell'avvio, nell'IDE viene eseguito il comando specificato. Se si usa questa opzione, la pagina iniziale di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non viene visualizzata nell'IDE all'avvio.  
  
 Se un componente aggiuntivo visualizza un comando, è possibile usare questa opzione per avviare il componente aggiuntivo dalla riga di comando. Per altre informazioni, vedere [Procedura: controllare i componenti aggiuntivi tramite Gestione componenti aggiuntivi](https://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Esempio  
 Questo codice di esempio avvia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ed esegue automaticamente la macro OpenFavoriteFiles.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
