---
title: Operatori di ricerca avanzati nelle espressioni di ricerca | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6befa20bcda7f30896fb2b04fadefb0eb5f21f8d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408403"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operatori di ricerca avanzati nelle espressioni di ricerca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usando gli operatori di ricerca avanzata, è possibile perfezionare la ricerca di contenuto creando espressioni di ricerca più complesse partendo da quelle più semplici. Come illustrato nella tabella seguente, questi operatori limitano il contesto in cui viene eseguita una query.  
  
> [!WARNING]
> È necessario immettere gli operatori di ricerca avanzati seguiti da due punti senza spazio affinché il motore di ricerca li possa riconoscere.  
  
|Per cercare|Usa|Esempio|Risultato|  
|-------------------|---------|-------------|------------|  
|Un termine nel titolo dell'argomento|title:|title:binaryreader|Argomenti che contengono "binaryreader" nei titoli.|  
|Un termine in un esempio di codice|code:|code:readdouble|Argomenti che contengono "readdouble" in un esempio di codice.|  
|Un termine in un 'esempio di un linguaggio di programmazione specifico|code:vb:|code:vb:string|Argomenti che contengono "string" in un esempio di Visual Basic.|  
|Un argomento associato a una parola chiave di indice specifica|keyword:|keyword:readbyte|Argomenti associati alla parola chiave di indice "readbyte".|  
  
 È possibile usare l'operatore code: per trovare contenuti relativi a diversi linguaggi di programmazione. Restituisce tuttavia solo i risultati relativi al contenuto contrassegnato con un linguaggio di programmazione specifico. La tabella seguente elenca i linguaggi di programmazione supportati da questo operatore:  
  
|Linguaggio di programmazione|Usa|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> oppure<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> oppure<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> oppure<br /><br /> code:c++<br /><br /> oppure<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> oppure<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> oppure<br /><br /> code:js|  
|XAML|: xaml|  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori logici nelle espressioni di ricerca](../ide/logical-operators-in-search-expressions.md)   
 [Suggerimenti per la ricerca full-text](../ide/full-text-search-tips.md)
