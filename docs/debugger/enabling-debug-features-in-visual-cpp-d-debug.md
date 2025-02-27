---
title: Abilitazione della funzionalità di Debug in Visual C++ (-D_DEBUG) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 295bdc7b220f8977c85dd1b359f99af2f8d5d72a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850966"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Attivazione delle funzionalità di debug in Visual C++ (/D_DEBUG)
In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] le funzionalità di debug, ad esempio le asserzioni, vengono attivate quando si compila il programma definendo il simbolo **_DEBUG**. Il simbolo **_DEBUG** può essere definito in uno dei due modi seguenti:

- Specificare **#define _DEBUG** nel codice sorgente.

- Specificare l'opzione del compilatore **/D_DEBUG**. Quando si crea un progetto mediante le procedure guidate di Visual Studio, il simbolo **/D_DEBUG** viene definito automaticamente nella configurazione di debug.

  Quando viene definito **_DEBUG**, il compilatore compila le sezioni del codice precedute e seguite da **#ifdef _DEBUG** e `#endif`.

  La configurazione di debug di un programma MFC deve essere collegata a una versione di debug della libreria MFC. I file di intestazione MFC determinano la versione corretta della libreria MFC con cui effettuare il collegamento in base ai simboli definiti, ad esempio **_DEBUG** e **_UNICODE**. Per informazioni dettagliate, vedere [Versioni delle librerie MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Vedere anche
- [Debug del codice nativo](../debugger/debugging-native-code.md)
- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)