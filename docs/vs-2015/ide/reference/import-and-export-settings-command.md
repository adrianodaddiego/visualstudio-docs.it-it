---
title: Importa/Esporta impostazioni (comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 91b34183e36c86290c14e3da7d17687d45cfe180
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694655"
---
# <a name="import-and-export-settings-command"></a>Importa/Esporta impostazioni (comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Consente di importare, esportare o reimpostare le impostazioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Opzioni  
 /export:`filename`  
 Facoltativo. Esporta le impostazioni correnti nel file specificato.  
  
 /import:`filename`  
 Facoltativo. Importa le impostazioni correnti nel file specificato.  
  
 /reset  
 Facoltativo. Reimposta le impostazioni correnti.  
  
## <a name="remarks"></a>Osservazioni  
 Se si esegue questo comando senza opzioni viene visualizzata l'**Importazione/Esportazione guidata delle impostazioni**. Per altre informazioni, vedere [Procedura: Condividere le impostazioni tra computer o versioni di Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Esempio  
 Il comando seguente esporta le impostazioni correnti nel file `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
