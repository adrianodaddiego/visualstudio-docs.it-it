---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6321433b506d41df57150b5a135a800a16cef0ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689674"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rimuove i comandi e l'interfaccia utente dei comandi associata al componente aggiuntivo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argomenti  
 `AddIn`  
 Facoltativo. Nome del comando del componente aggiuntivo.  
  
## <a name="remarks"></a>Osservazioni  
 Per impostazione predefinita, il nome del comando del componente aggiuntivo è uguale a *\<NomeSoluzioneComponenteAggiuntivo>*.Connect<em>.\<NomeSoluzioneComponenteAggiuntivo></em> e viene visualizzato in Connect.cs come parametro `commandName` del metodo `Exec`. È anche possibile verificare il nome del comando digitando l'inizio del nome del componente aggiuntivo nella finestra dei comandi in Visual Studio e usando Intellisense per completarlo.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente avvia Visual Studio e impedisce l'esecuzione all'avvio del componente aggiuntivo `MyAddin`.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
