---
title: -LCID (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: deb2ce5eba108127dce82bab77fe7ed4fb78fb14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970127"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Imposta la lingua predefinita usata per testo, valuta e altri valori all'interno dell'IDE.

## <a name="syntax"></a>Sintassi

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argomenti

- *LocaleID*

  Obbligatorio. Identificatore delle impostazioni locali (LCID) della lingua specificata.

## <a name="remarks"></a>Osservazioni

Carica l'IDE e imposta la lingua naturale predefinita per l'ambiente. Questa modifica viene salvata tra le sessioni e l'IDE mostra la modifica nella casella **Strumenti** > **Opzioni** > **Ambiente** > **Impostazioni internazionali** > **Lingua**.

Se la lingua specificata non è disponibile nel sistema in uso, l'opzione `/LCID` viene ignorata.

Nella tabella seguente vengono elencati gli LCID delle lingue supportate da Visual Studio.

|Linguaggio|LCID|
|--------------|----------|
|Cinese (semplificato)|2052|
|Cinese (tradizionale)|1028|
|Inglese|1040|
|Francese|1036|
|Tedesco|1031|
|Italiano|1040|
|Giapponese|1041|
|Coreano|1042|
|Spagnolo|3082|

## <a name="example"></a>Esempio

In questo esempio viene caricato l'IDE con le stringhe delle risorse in lingua inglese.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)