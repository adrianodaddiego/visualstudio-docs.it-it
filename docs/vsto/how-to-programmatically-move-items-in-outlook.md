---
title: 'Procedura: A livello di programmazione spostare elementi in Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3dcbfbe7b6e6ac5bacb9e8e36e43d780d3051903
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812562"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Procedura: A livello di programmazione spostare elementi in Outlook
  Questo esempio consente di spostare i messaggi di posta elettronica non letta dal **posta in arrivo** in una cartella denominata **Test**. Nell'esempio vengono spostati solo i messaggi che contengono la parola **Test** nel `Subject` campo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Una cartella di posta elettronica di Outlook denominata **Test**.

- Un messaggio di posta elettronica in arrivo con la parola **Test** nel `Subject` campo.

## <a name="see-also"></a>Vedere anche
- [Con le cartelle di lavoro](../vsto/working-with-folders.md)
- [Procedura: Recuperano una cartella in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: Eseguire la ricerca a livello di codice all'interno di una cartella specifica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Procedura: A livello di programmazione eseguire azioni quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
