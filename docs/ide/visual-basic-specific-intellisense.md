---
title: IntelliSense per Visual Basic
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc0897f3b2964996b18a40cc8dda16068ff772f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582511"
---
# <a name="intellisense-for-visual-basic-code-files"></a>IntelliSense per i file di codice di Visual Basic

L'editor del codice sorgente di Visual Basic offre le seguenti funzionalità di IntelliSense:

## <a name="syntax-tips"></a>Suggerimenti per la sintassi

I suggerimenti per la sintassi visualizzano la sintassi dell'istruzione che si sta digitando. La funzionalità è utile per istruzioni come [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Completamento automatico

- Completamento di diverse parole chiave

     Ad esempio, se si digita `goto` e uno spazio, IntelliSense visualizza l'elenco delle etichette definite in un menu a discesa. Altre parole chiave supportate sono `Exit`, `Implements`, `Option` e `Declare`.

- Completamento per `Enum` e `Boolean`

    Quando un'istruzione fa riferimento a un membro di enumerazione, IntelliSense visualizza l'elenco dei membri dell'oggetto `Enum`. Quando un'istruzione fa riferimento a un oggetto `Boolean`, IntelliSense visualizza un menu a discesa di valori true e false.

Il completamento può essere disattivato per impostazione predefinita deselezionando **Elenco membri automatico** dalla pagina **Generale** delle proprietà nella cartella **Visual Basic**.

È possibile richiamare manualmente il completamento richiamando Elenca membri, Completa parola o **ALT**+**Freccia DESTRA**. Per altre informazioni, vedere [Utilizzo di IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>IntelliSense sensibile all'area

IntelliSense sensibile all'area offre un supporto agli sviluppatori di Visual Basic che devono distribuire applicazioni con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e sono vincolati a impostazioni di attendibilità parziale. Questa funzionalità:

- Consente di scegliere le autorizzazioni con cui verrà eseguita l'applicazione.

- Visualizza le API dell'area prescelta come disponibili in Elenca membri e le API che richiedono autorizzazioni aggiuntive come non disponibili.

Per altre informazioni, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Elenchi di completamento filtrati

In Visual Basic gli elenchi di completamento IntelliSense includono due controlli Struttura a schede posizionati a fine elenco. Nella scheda **Comune**, selezionata per impostazione predefinita, sono visualizzati gli elementi usati più di frequente per completare l'istruzione che si sta scrivendo. Nella scheda **Tutti** sono visualizzati tutti gli elementi disponibili per il completamento automatico, inclusi quelli presenti anche nella scheda **Comune**.

## <a name="see-also"></a>Vedere anche

- [Usare IntelliSense](../ide/using-intellisense.md)