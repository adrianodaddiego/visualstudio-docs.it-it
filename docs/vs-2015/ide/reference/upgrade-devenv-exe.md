---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2ba3caf7931449e2c1657270838a45505fd5d92
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657285"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aggiorna il file della soluzione e tutti i relativi file di progetto oppure il file di progetto specificato ai formati di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] correnti dei file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>Argomenti  
 `SolutionFile`  
 Obbligatorio se si aggiorna un'intera soluzione e i relativi progetti. Il percorso e il nome di un file di soluzione. È possibile immettere solo il nome del file di soluzione oppure il percorso completo e il nome del file di soluzione. Se non esistono, la cartella o il nome file verranno creati.  
  
 `ProjectFile`  
 Obbligatorio se si esegue l'aggiornamento di un singolo progetto. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere solo il nome del file di progetto oppure il percorso completo e il nome del file di progetto. Se non esistono, la cartella o il nome file verranno creati.  
  
## <a name="remarks"></a>Osservazioni  
 I backup vengono creati e copiati automaticamente in una directory denominata Backup creata nella directory corrente.  
  
 Per consentire l'aggiornamento di soluzioni o progetti inclusi nel controllo del codice sorgente è necessario estrarli.  
  
 Se si usa l'opzione `/upgrade`, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non viene avviato. È possibile visualizzare i risultati dell'aggiornamento nel report di aggiornamento relativo al linguaggio di sviluppo della soluzione o del progetto. Non vengono restituiti messaggi di errore o informazioni sull'utilizzo. Per altre informazioni sull'aggiornamento di progetti in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vedere [Procedura: Risolvere i problemi relativi agli aggiornamenti di progetti Visual Studio con esito negativo](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## <a name="example"></a>Esempio  
 Questo esempio aggiorna un file di soluzione denominato "MyProject.sln" nella cartella predefinita per le soluzioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Risolvere i problemi relativi agli aggiornamenti di progetti Visual Studio con esito negativo](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
