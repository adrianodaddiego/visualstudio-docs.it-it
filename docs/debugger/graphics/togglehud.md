---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848472"
---
# <a name="togglehud"></a>ToggleHUD
Attiva/Disattiva diagnostica della grafica *HUD* (Head-Up Display) sovrapporre attiva o disattiva.

## <a name="syntax"></a>Sintassi

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Note
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Visualizza le informazioni di runtime relativi all'app e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando il [AddMessage](addmessage.md) funzione membro.

 Per attivare o disattivare l'HUD, non è necessario acquisire attivamente informazioni grafiche, vale a dire, può essere modificato tramite un'istanza del `VsgDbg` (classe), ma la [Init](init.md) funzione membro non deve essere chiamato per primo.