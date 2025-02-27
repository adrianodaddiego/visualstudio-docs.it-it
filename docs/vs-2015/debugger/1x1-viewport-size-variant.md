---
title: Variante delle dimensioni del Viewport 1x1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 74e3bc706cb2df12aacddf9fbb77dec598bfc17a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955151"
---
# <a name="1x1-viewport-size-variant"></a>Variante delle dimensioni del viewport 1x1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Riduce a 1x1 pixel le dimensioni del riquadro di visualizzazione in tutte le destinazioni di rendering.  
  
## <a name="interpretation"></a>Interpretazione  
 In un riquadro di visualizzazione più piccolo il numero di pixel che devono essere ombreggiati è ridotto, ma non viene ridotto il numero di vertici che devono essere elaborati. L'impostazione delle dimensioni del riquadro di visualizzazione su 1x1 pixel consente di eliminare l'ombreggiatura dei pixel dall'app.  
  
 Se questa variante mostra un miglioramento notevole delle prestazioni, questo potrebbe indicare un utilizzo eccessivo della velocità di riempimento, a significare che la risoluzione scelta è troppo elevata per la piattaforma di destinazione o che l'app impiega troppo tempo per l'ombreggiatura di pixel che in seguito vengono sovrascritti (caricamento). Il risultato suggerisce che la riduzione delle dimensioni del buffer frame o della quantità di caricamento determina un miglioramento delle prestazioni dell'app.  
  
## <a name="remarks"></a>Note  
 Le dimensioni del riquadro di visualizzazione vengono reimpostate su 1x1 pixel dopo ogni chiamata a `ID3D11DeviceContext::OMSetRenderTargets` o `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Esempio  
 Questa variante può essere riprodotta usando codice simile al seguente:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
