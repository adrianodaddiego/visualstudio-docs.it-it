---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896355"
---
# <a name="addmessage"></a>AddMessage
Aggiunge un messaggio personalizzato alla diagnostica della grafica *HUD* (Head-Up Display).

## <a name="syntax"></a>Sintassi

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parametri
 `szMessage` Messaggio da aggiungere a HUD.

## <a name="remarks"></a>Note
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Vengono visualizzate le informazioni di runtime sull'applicazione e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando questa funzione.

 Per aggiungere un messaggio a HUD, non è necessario acquisire attivamente informazioni grafiche, ovvero un messaggio può essere aggiunto tramite un'istanza della classe `VsgDbg`, ma la funzione membro [Init](init.md) non deve essere chiamata per prima. I messaggi vengono visualizzati solo in HUD, non vengono registrati nei file di log di grafica.