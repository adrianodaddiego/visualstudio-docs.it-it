---
title: Passare al file, passare al simbolo, passare alla riga
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 588bc57dc2cda1030e9e1b8d1f989b2cc2d31662
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62549984"
---
# <a name="find-code-using-go-to-commands"></a>Trovare codice con i comandi Vai a

I comandi **Vai a** di Visual Studio consentono di eseguire una ricerca mirata nel codice allo scopo di individuare rapidamente elementi specifici. Da una semplice interfaccia unificata è possibile passare a una riga, a un tipo, a un simbolo o a un file specifico e ad altro ancora.

## <a name="how-to-use-it"></a>Come usare la funzionalità

Input | Funzione
------------ | ---
**Tastiera** | Premere **CTRL**+**T** oppure **CTRL**+ **,**
**Mouse** | Selezionare **Modifica** > **Vai a** > **Vai a tutti**

Viene visualizzata una piccola finestra nella parte superiore destra dell'editor del codice.

![Finestra Vai a tutti](media/go-to-all.png)

Durante la digitazione nella casella di testo i risultati vengono visualizzati in un elenco a discesa sotto la casella di testo stessa. Per passare a un elemento, selezionarlo nell'elenco.

![Finestra Passa a](../ide/media/vside_navigatetowindow.png)

È anche possibile immettere un punto interrogativo ( **?** ) per ottenere informazioni aggiuntive.

![Guida di Vai a tutti](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Ricerche con filtri

Per impostazione predefinita, l'elemento specificato viene cercato in tutti gli elementi della soluzione. È però possibile limitare la ricerca nel codice a tipi di elementi specifici anteponendo determinati caratteri di prefisso ai termini di ricerca. È anche possibile modificare rapidamente il filtro di ricerca scegliendo i pulsanti sulla barra degli strumenti della finestra di dialogo **Vai a**. I pulsanti per la modifica dei filtri relativi al tipo si trovano sul lato sinistro, mentre quelli per la modifica dell'ambito della ricerca sono sul lato destro.

![Passare a membri](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrare in base a un tipo specifico di elemento di codice

Per limitare la ricerca a un tipo specifico di elemento di codice, è possibile specificare un prefisso nella casella di ricerca o selezionare una delle cinque icone di filtro:

Prefisso | Icona | Metodo rapido | Description
:-: | - | - | -
:| ![Icona Riga](media/gotoall-line-icon.png) | **CTRL**+**G** | Consente di passare al numero di riga specificato
f| ![Icona File](media/gotoall-files-icon.png) | **CTRL**+**1**, **CTRL**+**F** | Consente di passare al file specificato
r| ![Icona File recenti](media/gotoall-recent-files-icon.png) | **CTRL**+**1**, **CTRL**+**R** | Consente di passare al file specificato, visitato di recente
u| ![Icona Tipi](media/gotoall-types-icon.png) | **CTRL**+**1**, **CTRL**+**T** | Consente di passare al tipo specificato
m| ![Icona Membri](media/gotoall-members-icon.png) | **CTRL**+**1**, **CTRL**+**M** | Consente di passare al membro specificato
\#| ![Icona Simboli](media/gotoall-symbols-icon.png) | **CTRL**+**1**, **CTRL**+**S** | Consente di passare al simbolo specificato

### <a name="filter-to-a-specific-location"></a>Filtrare in base a una posizione specifica

Per limitare la ricerca a una posizione specifica, selezionare una delle due icone documento:

Icona | Description
---- | ---
![Documento corrente](media/gotoall_currentdocument.png) | Cerca solo il documento corrente
![Documenti esterni](media/gotoall_external.png) | Cerca i documenti esterni oltre a quelli presenti nel progetto e/o nella soluzione

## <a name="camel-casing"></a>Notazione Camel

Se si usa la [notazione Camel](https://en.wikipedia.org/wiki/Camel_case) nel codice, è possibile trovare gli elementi di codice più rapidamente immettendo solo le lettere maiuscole dei nomi degli elementi di codice. Ad esempio, se nel codice è presente un tipo denominato `CredentialViewModel`, è possibile restringere la ricerca scegliendo il filtro **Tipo** (**t**) e quindi immettendo solo le lettere maiuscole del nome (`CVM`) nella finestra di dialogo Vai a. Questa funzionalità può essere utile se il codice contiene nomi lunghi.

![Finestra Passa a - ricerca con lettere maiuscole](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Impostazioni

Se si seleziona l'icona a forma di ingranaggio ![Icona Ingranaggio](media/gotoall_gear.png) è possibile modificare il comportamento di questa funzionalità:

Impostazione | Description
------- | ---
Utilizza scheda anteprima | Visualizza immediatamente l'elemento selezionato nella scheda anteprima dell'IDE
Mostra dettagli | Visualizza informazioni relative a progetto, file, riga e riepilogo recuperando i commenti della documentazione nella finestra
Centra la finestra | Sposta la finestra al centro della parte superiore dell'editor di codice anziché in alto a destra

## <a name="see-also"></a>Vedere anche

- [Spostarsi all'interno del codice](../ide/navigating-code.md)
- [Finestra di dialogo Vai alla riga](../ide/reference/go-to-line.md)
- [Vai a definizione e Visualizza definizione](../ide/go-to-and-peek-definition.md)