---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699353"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica il linguaggio del codice sorgente dell'applicazione o del modulo collegato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## <a name="elements"></a>Elementi  
 CV_CFL_C  
 Lingua dell'applicazione è sufficiente.  
  
 CV_CFL_CXX  
 Lingua dell'applicazione è C++.  
  
 CV_CFL_FORTRAN  
 Lingua dell'applicazione è FORTRAN.  
  
 CV_CFL_MASM  
 Lingua dell'applicazione è Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Lingua dell'applicazione è la convenzione Pascal.  
  
 CV_CFL_BASIC  
 Lingua dell'applicazione è BASIC.  
  
 CV_CFL_COBOL  
 Lingua dell'applicazione è COBOL.  
  
 CV_CFL_LINK  
 Applicazione è un modulo generate dal linker.  
  
 CV_CFL_CVTRES  
 Applicazione è un modulo di risorse convertito con lo strumento CVTRES.  
  
 CV_CFL_CVTPGD  
 Applicazione è un modulo POGO ottimizzato generato con CVTPGD strumento.  
  
 CV_CFL_CSHARP  
 Lingua dell'applicazione è c#.  
  
 CV_CFL_VB  
 Lingua dell'applicazione è Visual Basic.  
  
 CV_CFL_ILASM  
 Lingua dell'applicazione è l'assembly del linguaggio intermedio (vale a dire assembly Common Language Runtime (CLR)).  
  
 CV_CFL_JAVA  
 Lingua dell'applicazione Java è.  
  
 CV_CFL_JSCRIPT  
 Lingua dell'applicazione è Jscript.  
  
 CV_CFL_MSIL  
 Lingua dell'applicazione è un sconosciuto linguaggio MSIL (Microsoft Intermediate), probabilmente un risultato dell'uso di [/LTCG (generazione di codice in fase di collegamento)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) passare.  
  
 CV_CFL_HLSL  
 Lingua dell'applicazione è High Level Shader Language.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono restituiti da una chiamata per il [Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
