---
title: Codice misto e informazioni mancanti nella finestra Stack di chiamate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 025591ffea4d6746f87e5f1240cd226fa291d116
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905509"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Codice misto e informazioni mancanti nella finestra Stack di chiamate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A causa delle differenze tra gli stack di chiamate per il codice gestito e il codice nativo, il debugger non è sempre in grado di visualizzare lo stack di chiamate completo in caso di tipi di codice misti. Quando codice nativo chiama codice gestito, nella finestra **Stack di chiamate** potrebbero osservarsi le seguenti discrepanze:  
  
- Il frame nativo situato immediatamente al di sopra del codice gestito potrebbe non essere visualizzato nella finestra **Stack di chiamate**. Per altre informazioni, vedere [Procedura: Uscire dal codice gestito quando nella finestra Stack di chiamate non sono visualizzati frame nativi](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- Per le applicazioni in modalità mista avviate all'esterno del debugger, nella finestra **Stack di chiamate** potrebbe essere visualizzato solo il codice gestito ma nessuno dei frame nativi.  
  
  Entrambi i casi sono piuttosto rari. Nella maggior parte delle chiamate native a codice gestito gli stack di chiamate verranno visualizzati in modo corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md)
