---
title: Comando Shell | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9a85b8ef5dd99da6c82c9f63da31bec783a7c9a7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438024"
---
# <a name="shell-command"></a>Comando Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avvia programmi eseguibili da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## <a name="arguments"></a>Argomenti  
 `path`  
 Obbligatorio. Percorso e nome del file da eseguire o del documento da aprire. È necessario specificare un percorso completo se il file specificato non si trova in una delle directory incluse nella variabile di ambiente PATH.  
  
 `args`  
 Facoltativo. Argomenti da passare al programma richiamato.  
  
## <a name="switches"></a>Opzioni  
 /commandwindow [oppure] /command [oppure] /c [oppure] /cmd  
 Facoltativo. Specifica che l'output per il file eseguibile verrà visualizzato nella finestra di **comando**.  
  
 /dir:`folder` [oppure] /d: `folder`  
 Facoltativo. Specifica la cartella di lavoro da impostare all'esecuzione del programma.  
  
 /outputwindow [oppure] /output [oppure] /out [oppure] /o  
 Facoltativo. Specifica che l'output per il file eseguibile verrà visualizzato nella finestra di **output**.  
  
## <a name="remarks"></a>Osservazioni  
 Le opzioni /dir /o /c devono essere specificate immediatamente dopo `Tools.Shell`. Tutto ciò che viene specificato dopo il nome del file eseguibile viene passato all'eseguibile come argomento della riga di comando.  
  
 È possibile usare l'alias predefinito `Shell` invece di `Tools.Shell`.  
  
> [!CAUTION]
> Se l'argomento `path` include sia il percorso della directory sia il nome del file, è consigliabile racchiudere l'intero percorso tra virgolette doppie adiacenti ("""), come nell'esempio seguente:  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 Ogni gruppo di tre virgolette doppie (""") viene interpretato dal processore `Shell` come un'unica virgoletta doppia. Nell'esempio precedente, pertanto, al comando `Shell` viene passata la stringa di percorso seguente:  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
> Se la stringa di percorso non viene racchiusa tra virgolette doppie adiacenti ("""), Windows userà solo la porzione di stringa che precede il primo spazio. Se ad esempio la stringa di percorso usata nell'esempio precedente non fosse racchiusa tra virgolette in modo corretto, Windows cercherebbe un file denominato "Program" nella directory radice C:\. Qualora un file eseguibile C:\Program.exe fosse disponibile, anche se si trattasse di un file installato tramite una manomissione non autorizzata, Windows tenterebbe di eseguire quel programma anziché il programma desiderato "C:\Programmi\NomeFile.exe".  
  
## <a name="example"></a>Esempio  
 Il comando seguente usa xcopy.exe per copiare il file `MyText.txt` nella cartella `Text`. L'output di xcopy.exe viene visualizzato nella **finestra di comando** e nella **finestra di output**.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Finestra di output](../../ide/reference/output-window.md)   
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
