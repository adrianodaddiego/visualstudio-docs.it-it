---
title: T4 Direttiva di Output | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9262ec994ec847c38ec8d5c1ad95010a929cc4ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62549529"
---
# <a name="t4-output-directive"></a>Direttiva output T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nei modelli di testo di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la direttiva `output` viene usata per definire l'estensione di file e la codifica del file trasformato.  
  
 Ad esempio, se il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetto include un file di modello denominato **MyTemplate.tt** che contiene la direttiva seguente:  
  
 `<#@output extension=".cs"#>`  
  
 quindi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genererà un file denominato **MyTemplate.cs**  
  
 La direttiva `output` in un modello di testo (pre-elaborato) della fase di esecuzione non è necessaria. L'applicazione otterrà la stringa generata con una chiamata a `TextTransform()`. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Uso della direttiva output  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 In ogni modello di testo non deve essere presente più di una direttiva `output`.  
  
## <a name="extension-attribute"></a>attributo di estensione  
 Specifica l'estensione di file del file di output di testo generato.  
  
 Il valore predefinito è **. cs**  
  
 Esempi:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Valori accettabili:  
 Qualsiasi estensione di file valida.  
  
## <a name="encoding-attribute"></a>attributo di codifica  
 Specifica la codifica da usare quando viene generato il file di output. Ad esempio:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Il valore predefinito è la codifica usata dal file di modello di testo.  
  
 Valori accettabili:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (valore predefinito del sistema)  
  
 In generale, è possibile usare la stringa WebName o il numero CodePage di tutte le codifiche restituite da <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
