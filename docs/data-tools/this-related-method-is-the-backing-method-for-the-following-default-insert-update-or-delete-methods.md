---
title: Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a5ae70462079589ba2b63ee50cf0b7a0570e056a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457835"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione

Questo metodo correlato è il metodo sottostante per l'impostazione predefinita seguente `Insert`, `Update`, o `Delete` metodi. Se viene eliminato, verranno eliminati anche questi metodi. Continuare?

Selezionato `DataContext` metodo viene usato attualmente come uno dei `Insert`, `Update`, o `Delete` metodi per una delle classi di entità nel **O/R Designer**. Il metodo selezionato provoca l'eliminazione della classe di entità che lo stava usando questo metodo per ripristinare il comportamento in fase di esecuzione predefinito per l'esecuzione di inserimento, aggiornare o eliminare durante un aggiornamento.

## <a name="selected-method-options"></a>Opzioni per il metodo selezionato

- Per eliminare il metodo selezionato, causando la classe di entità da utilizzare aggiornamenti al runtime, fare clic su **Sì**.

   Il metodo selezionato viene eliminato e per tutte le classi che utilizzavano tale metodo per l'override del comportamento di aggiornamento viene ripristinato l'uso del comportamento in fase di esecuzione LINQ to SQL predefinito.

- Per chiudere la finestra di messaggio, lasciando il metodo selezionato non modificato, fare clic su **No**.

   La finestra di messaggio viene chiusa e non vengono apportate modifiche.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)