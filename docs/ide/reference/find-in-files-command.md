---
title: Comando Cerca nei file
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5549bd0047b38ef8f0dff5fa420d4b5ce0ae4ce9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790261"
---
# <a name="find-in-files-command"></a>Comando Cerca nei file
Esegue la ricerca di testo nei file usando un subset delle opzioni disponibili nella scheda **Cerca nei file** della finestra **Trova e sostituisci**.

## <a name="syntax"></a>Sintassi

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argomenti
 `findwhat` Obbligatorio. Testo da cercare.

## <a name="switches"></a>Opzioni
 /case o /c Facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.

 /ext: `extensions` Facoltativo. Specifica l'estensione dei file nei quali eseguire la ricerca. Se non è specificato e in precedenza è stata immessa un'estensione, viene usata tale estensione.

 /lookin: `searchpath` Facoltativo. Directory in cui eseguire la ricerca. Se il percorso contiene spazi, racchiudere l'intero percorso tra virgolette.

 /names o /n Facoltativo. Visualizza l'elenco dei nomi file che contengono corrispondenze.

 /open or /o Facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.

 /regex o /r Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset o /e Facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.

 /stop Facoltativo. Se è in corso un'operazione di ricerca, la interrompe. Quando viene specificato `/stop` la ricerca ignora tutti gli altri argomenti. Ad esempio, per interrompere la ricerca corrente immettere quanto segue:

```cmd
>Edit.FindinFiles /stop
```

 /sub o /s Facoltativo. Effettua la ricerca nelle sottocartelle incluse nella directory specificata nell'argomento /lookin:`searchpath`.

 /text2 o /2 Facoltativo. Visualizza i risultati della ricerca nella finestra Risultati ricerca 2.

 /wild o /l Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.

 /word o /w Facoltativo. Cerca solo parole intere.

## <a name="example"></a>Esempio
 Nell'esempio riportato di seguito viene cercato btnCancel in tutti i file CLS presenti nella cartella "My Visual Studio Projects" e le informazioni sulle corrispondenze trovate vengono visualizzate nella finestra Risultati ricerca 2.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Vedere anche

- [Cerca nei file](../../ide/find-in-files.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)