---
title: Introduzione (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54f83f00ed2e99d1541e15092cb3ee0ce9e08952
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955279"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Introduzione (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il Debug Interface Access (DIA) SDK fornisce un esempio che illustra come usare l'API di DIA e la documentazione didattici. Utilizzare le interfacce e metodi in DIA SDK per sviluppare applicazioni personalizzate che aprono i file DBG e PDB e cercare il contenuto per i simboli, i valori, attributi, gli indirizzi e altre informazioni di debug. Questo SDK fornisce anche le tabelle di riferimento per le proprietà associate di simboli trovati nelle applicazioni C++.  
  
 Per utilizzare al meglio il DIA SDK, è necessario avere familiarità con gli elementi seguenti:  
  
- Linguaggio di programmazione C++  
  
- Programmazione COM  
  
- Visual Studio IDE (IDE) per la compilazione degli esempi  
  
  Il DIA SDK viene normalmente installato con Visual Studio e il percorso predefinito è *[unità]* \Programmi\Microsoft 9.0\DIA Visual Studio SDK. Come parte dell'installazione, il MSDIA90, che implementa il DIA SDK, viene registrato automaticamente in modo da eseguire per usarla è sufficiente includere `dia2.h` nel programma e collegamento a `diaguids.lib`.  
  
  Intestazione: include\dia2.h  
  
  Libreria: lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>In questa sezione  
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Esamina l'architettura di base di DIA.  
  
 [Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Vengono fornite istruzioni dettagliate su come usare l'API di DIA per eseguire query di un file con estensione pdb.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
