---
title: Operatore di contesto (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6351dd9db7e6f8f29bdd15f376f84511c64bfe7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116615"
---
# <a name="context-operator-c"></a>Operatore di contesto (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'operatore di contesto in C++ può essere usato per qualificare la posizione di un punto di interruzione, il nome di una variabile o un'espressione. L'operatore di contesto è utile per specificare un nome da un ambito esterno che altrimenti sarebbe nascosto da un nome locale.  
  
## <a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Sintassi  
 Il contesto può essere specificato in due modi:  
  
1. {,,[*module*] } *expression*  
  
     Le parentesi graffe devono contenere due virgole e il nome o il percorso completo del modulo (file eseguibile o DLL).  
  
     Ad esempio, per impostare un punto di interruzione nella funzione `SomeFunction` di EXAMPLE.dll:  
  
    ```cpp  
    {,,EXAMPLE.dll}SomeFunction  
    ```  
  
2. *module*!*expression*  
  
    ```cpp  
    EXAMPLE.dll!SomeFunction  
    ```  
  
- *module* è il nome di un modulo. È possibile usare un percorso completo per distinguere i moduli che hanno lo stesso nome.  
  
   Se il percorso di *module* include una virgola, uno spazio incorporato o una parentesi graffa, è necessario racchiudere il percorso tra virgolette in modo che il parser del contesto possa riconoscere correttamente la stringa. Poiché le virgolette singole vengono considerate parte di un nome di file di Windows, è necessario usare le virgolette doppie. Ad esempio,  
  
  ```cpp  
  {,,"a long, long, library name.dll"} g_Var  
  ```  
  
- *expression* è una qualsiasi espressione C++ valida che viene risolta in una destinazione valida, ad esempio un nome di funzione, un nome di variabile o un indirizzo del puntatore in *module*.  
  
  Quando l'analizzatore di espressioni rileva un simbolo in un'espressione, ne esegue la ricerca nel seguente ordine:  
  
1. Ambito lessicale verso l'esterno, a partire dal blocco corrente, serie di istruzioni racchiuse tra parentesi graffe, verso il blocco di inclusione. Il blocco corrente è il codice contenente la posizione corrente, ovvero l'indirizzo del puntatore all'istruzione.  
  
2. Ambito della funzione. Funzione corrente.  
  
3. Ambito della classe, se la posizione corrente si trova all'interno di una funzione membro C++. Nell'ambito della classe sono incluse tutte le classi base. L'analizzatore di espressioni usa le regole di dominanza normali.  
  
4. Simboli globali nel modulo corrente.  
  
5. Simboli pubblici nel programma corrente.
