---
title: Comando Sostituisci nei file
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a87b4dcff0bd626947a0d98822150d03fc7c7059
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945568"
---
# <a name="replace-in-files-command"></a>Comando Sostituisci nei file
Sostituisce il testo nei file usando un subset delle opzioni disponibili nella scheda **Sostituisci nei file** della finestra **Trova e sostituisci**.

## <a name="syntax"></a>Sintassi

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Argomenti
 `findwhat`

 Obbligatorio. Testo da cercare.

 `replacewith`

 Obbligatorio. Il testo di sostituzione per il testo corrispondente.

## <a name="switches"></a>Opzioni
 /all o /a

 Facoltativo. Sostituisce tutte le occorrenze del testo di ricerca con il testo di sostituzione.

 /case o /c

 Facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.

 /ext: `extensions`

 Facoltativo. Specifica l'estensione dei file nei quali eseguire la ricerca.

 /keep o /k

 Facoltativo. Indica che tutti i file modificati vengono lasciati aperti.

 /lookin: `searchpath`

 Facoltativo. Directory in cui eseguire la ricerca. Se il percorso contiene spazi, racchiudere l'intero percorso tra virgolette.

 /options o /t

 Facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.

 /regex o /r

 Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset o /e

 Facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.

 /stop

 Facoltativo. Se è in corso un'operazione di ricerca, la interrompe. Quando viene specificato `/stop` la sostituzione ignora tutti gli altri argomenti. Ad esempio, per interrompere la sostituzione corrente immettere quanto segue:

```
>Edit.ReplaceinFiles /stop
```

 /sub o /s

 Facoltativo. Effettua la ricerca nelle sottocartelle incluse nella directory specificata nell'argomento /lookin:`searchpath`.

 /text2 o /2

 Facoltativo. Visualizza i risultati della sostituzione nella finestra **Risultati ricerca 2**.

 /wild o /l

 Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.

 /word o /w

 Facoltativo. Cerca solo parole intere.

## <a name="example"></a>Esempio
 In questo esempio `btnCancel` viene cercato e sostituito con `btnReset` in tutti i file CLS presenti nella cartella "my visual studio projects" e le informazioni relative alle sostituzioni vengono visualizzate nella finestra **Risultati ricerca 2**.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Vedere anche

- [Ricerca e sostituzione di testo](../../ide/finding-and-replacing-text.md)
- [Sostituisci nei file](../../ide/replace-in-files.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)