---
title: SDK di modellazione per Visual Studio (linguaggi specifici di dominio)
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b955dc6f79c689ca30d8d9876d0888b14127490
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476523"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>SDK di modellazione per Visual Studio (linguaggi specifici di dominio)

Usando il SDK di modellazione per Visual Studio, è possibile creare strumenti di sviluppo avanzato basato su modello che è possibile integrare in Visual Studio. Analogamente, è possibile creare una o più definizioni di modello e integrarle in un set di strumenti.

MSDK è basato sulla definizione di un modello creato per rappresentare i concetti nella propria area aziendale. È possibile racchiudere il modello con un'ampia gamma di strumenti, ad esempio una vista basata su diagramma, la possibilità di generare codice e altri artefatti, i comandi per trasformare il modello e la possibilità di interagire con il codice e altri oggetti in Visual Studio. Quando si sviluppa il modello, è possibile combinarlo con altri modelli e strumenti per formare un potente set di strumenti avanzati incentrati sulla propria attività di sviluppo.

MSDK consente di compilare rapidamente un modello nel formato di linguaggio specifico di dominio (DSL). Iniziare utilizzando un editor specifico per definire uno schema o una sintassi astratta insieme a una notazione grafica. Utilizzando questa definizione, VMSDK genera:

- Implementazione di modello con un'API fortemente tipizzata eseguita in un archivio basato sulle transazioni.

- Finestra di esplorazione ad albero.

- Editor grafico in cui gli utenti possono visualizzare il modello o parti definite.

- Metodi di serializzazione che salvano i modelli in XML leggibile.

- Funzionalità per generare codice di programma e altri elementi utilizzando il modello di testo.

Tutte queste funzionalità possono essere personalizzate ed estese. Le estensioni sono integrate in modo che sia comunque possibile aggiornare la definizione DSL e rigenerare le funzionalità senza perdere le estensioni.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Post di blog correlati](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)