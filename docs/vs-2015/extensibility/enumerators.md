---
title: Gli enumeratori | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65a03a8dc741ec86aca3137f49cd753722ede215
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966953"
---
# <a name="enumerators"></a>Enumeratori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa sezione elenca i tipi di dati di enumeratore nell'API dei plug-in controllo di origine che il plug-in del controllo del codice sorgente devono essere informati.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Codice di comando](../extensibility/command-code-enumerator.md)  
 Enumera le opzioni per la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) funzioni.  
  
 [Messaggio](../extensibility/message-enumerator.md)  
 Enumera i flag utilizzati per il callback, stampa [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Codice di stato dei file](../extensibility/file-status-code-enumerator.md)  
 Contiene valori costanti denominati che specificano lo stato di un file di controllo del codice sorgente.  
  
 [Codice di stato directory](../extensibility/directory-status-code-enumerator.md)  
 Contiene valori costanti denominati che specificano lo stato di una directory nel controllo del codice sorgente.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definisce il SDK dei plug-in controllo di origine e descritte le risorse incluse.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Richiede all'utente le opzioni avanzate per il comando specificato.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Esamina l'elenco dei file per il relativo stato corrente. Inoltre, utilizza il `pfnPopulate` funzione per notificare al chiamante quando un file non corrisponde ai criteri per il `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Viene descritta la funzione di callback che viene utilizzata dagli [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal controllo del codice sorgente del plug-in tramite l'IDE.  
  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)  
 Fornisce un elenco completo di tutti gli elementi nell'API dei plug-in controllo di origine.
