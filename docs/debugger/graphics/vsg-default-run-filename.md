---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb56f7ef08241aed2e109e6845af8fb596cb42e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895385"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Definisce il nome file predefinito del file di log di grafica.

## <a name="syntax"></a>Sintassi

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parametri
 `filename` Nome file assegnato per impostazione predefinita al file di log di grafica quando le informazioni grafiche vengono acquisite a livello di codice.

## <a name="value"></a>Value
 Valore letterale stringa che rappresenta il nome del file di log di grafica. Per impostazione predefinita, L"default.vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Note
 Se viene definito il simbolo del preprocessore `DONT_SAVE_VSGLOG_TO_TEMP`, il nome del file è relativo alla directory corrente dell'applicazione acquisita o è un percorso assoluto; in caso contrario, è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.

 Per modificare il nome file definito, è necessario ridefinirlo prima di includere `vsgcapture.h` nel programma.

## <a name="example"></a>Esempio
 In questo esempio viene illustrato come modificare il nome file predefinito del file di acquisizione:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Vedere anche
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)