---
title: Comando Registra output finestra di comando
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24c72b0c5aeb510186728d66e51935c337547adf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946843"
---
# <a name="log-command-window-output-command"></a>Comando Registra output finestra di comando
Copia interamente l'input e l'output della finestra di **comando** in un file.

## <a name="syntax"></a>Sintassi

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argomenti
 `filename`

 Facoltativo. Nome del file di log. Per impostazione predefinita, il file viene creato nella cartella del profilo dell'utente. Se il nome del file specificato esiste già, il log viene accodato alla fine del file esistente. Se non viene specificato alcun file, viene usato l'ultimo file specificato. Se non esiste alcun file precedente, viene creato un file di log predefinito, denominato cmdline.log.

> [!TIP]
> Per modificare il percorso in cui viene salvato il file di log, immettere il percorso completo del file, racchiuso tra virgolette se il percorso contiene spazi.

## <a name="switches"></a>Opzioni
 /on

 Facoltativo. Avvia la registrazione per la finestra di **comando** nel file specificato e accoda il file con le nuove informazioni.

 /off

 Facoltativo. Interrompe la registrazione per la finestra di **comando**.

 /overwrite

 Facoltativo. Se il file specificato nell'argomento `filename` corrisponde a un file esistente, il file viene sovrascritto.

## <a name="remarks"></a>Osservazioni
 Se non viene specificato alcun file, viene creato per impostazione predefinita il file cmdline.log. Per impostazione predefinita, l'alias per questo comando è Log.

## <a name="examples"></a>Esempi
 In questo esempio viene creato un nuovo file di log, cmdlog, e viene avviata la registrazione dei comandi.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

 Questo esempio arresta la registrazione dei comandi.

```cmd
>Tools.LogCommandWindowOutput /off
```

 Questo esempio consente di riprendere la registrazione dei comandi nel file di log usato in precedenza.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)