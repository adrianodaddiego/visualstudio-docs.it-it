---
title: Debug in modalità mista è supportato solo quando si usa Microsoft .NET Framework 2.0 o 3.0 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc45927ad6cc1189ed1d08328b4dd362821cdcb6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696461"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Supporto del debug in modalità mista solo quando si utilizza Microsoft .NET Framework 2.0 o 3.0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le versioni di Microsoft .NET Framework precedenti alla 2.0 non forniscono alcun supporto per il debug in modalità mista di processi a 64 bit. Ciò significa che non è possibile passare dal codice gestito al codice nativo o viceversa durante l'esecuzione del debug.  
  
 Per aggirare il problema è possibile:  
  
- Aggiornare il progetto per utilizzare Microsoft .NET Framework 2.0 o 3.0.  
  
- Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.  
  
- Eseguire il debug del codice misto come processo a 32 bit, come descritto nelle procedure che seguono.  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Per modificare il sistema operativo a 32 bit (Visual Basic o C#)  
  
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi fare clic su **Proprietà** nel menu di scelta rapida.  
  
2. Nella pagina delle proprietà fare clic sulla scheda **Compilazione** o **Debug**.  
  
3. Fare clic su **Piattaforma**, quindi selezionare **x86** dall'elenco delle piattaforme.  
  
     Per impostazione predefinita, i compilatori di Visual Basic e C# producono codice eseguibile in qualsiasi CPU. In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit. Per l'esecuzione in un processo a 32 bit, è necessario scegliere **Win32** anziché **AnyCPU**.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Per modificare il sistema operativo a 32 bit (C/C++)  
  
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi fare clic su **Proprietà** nel menu di scelta rapida.  
  
     Nella pagina delle proprietà fare clic su **Piattaforma**, quindi selezionare **Win32** dall'elenco delle piattaforme.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Visualizzare [impostazione del debug SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni a 64 Bit](../debugger/debug-64-bit-applications.md)
