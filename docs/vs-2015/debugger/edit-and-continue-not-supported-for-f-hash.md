---
title: Modifica e continuazione non supportate per F# | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4fef61335679e3f82d5916726981e003bf9c332
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428464"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Modifica e continuazione non supportate per F# #
La modifica e la continuazione non sono supportate quando si esegue il debug del codice F #. Le modifiche al codice F# durante una sessione di debug sono possibili ma devono essere evitate. Le modifiche di codice non vengono applicate durante la sessione di debug. Pertanto, qualsiasi modifica apportata al codice F# durante il debug comporterà una non corrispondenza del codice sorgente con il codice in fase di debug.
