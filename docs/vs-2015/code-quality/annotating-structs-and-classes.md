---
title: Annotazioni di struct e classi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: df2e75bb3dd01d051d8fed29748e499f8f620128
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075389"
---
# <a name="annotating-structs-and-classes"></a>Annotazioni di struct e classi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile annotare i membri struct e di classe utilizzando le annotazioni che operano come invarianti, si presume che siano true per qualsiasi chiamata di funzione o entrata/uscita di funzione che include la struttura contenitore come parametro o valore restituito.  
  
## <a name="struct-and-class-annotations"></a>Annotazioni di classi e struct  
  
- `_Field_range_(low, high)`  
  
     Il campo è compreso nell'intervallo (inclusivo) dal `low` a `high`.  Equivalente ad applicare `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` all'oggetto annotato utilizzando le pre/postcondizioni appropriate.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Campo con una dimensione scrivibile in elementi (o byte) come specificato da `size`.  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Campo con una dimensione scrivibile in elementi (o byte) come specificato da `size` e `count` degli elementi (byte) che sono leggibili.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Campo che contiene sia dimensione leggibile che modificabile in elementi (o byte) come specificato da `size`.  
  
- `_Struct_size_bytes_(size)`  
  
     Campo che contiene sia dimensione leggibile che modificabile in elementi (o byte) come specificato da `size`.  
  
     Si applica alla dichiarazione di classe o struct.  Indica che un oggetto valido di tale tipo può essere maggiore rispetto al tipo dichiarato, con il numero di byte specificati da `size`.  Ad esempio:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     Le dimensioni del buffer in byte di un parametro `pM` di tipo `MyStruct *` viene quindi considerato:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle annotazioni SAL per ridurre i difetti del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento (funzione)](../code-quality/annotating-function-behavior.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare quando e dove applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funzioni intrinseche](../code-quality/intrinsic-functions.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)
