---
title: Discendenti (proprietà dinamica XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8c89e04346a4b08d6ee7bbc0012ef52f3b648512
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54789352"
---
# <a name="descendants-xelement-dynamic-property"></a>Discendenti (proprietà dinamica XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ottiene un indicizzatore usato per recuperare tutti gli elementi discendente dell'elemento corrente che corrispondono al nome espanso specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Indicizzatore del tipo `IEnumerable<XElement> Item(String expandedName)`. Questo indicizzatore accetta il nome espanso degli elementi discendente specificati e restituisce gli elementi figlio corrispondenti in una raccolta <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## <a name="remarks"></a>Note  
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> della classe <xref:System.Xml.Linq.XContainer>.  
  
 Gli elementi della raccolta restituita sono in ordine del documento dell'origine XML.  
  
 Questa proprietà usa l'esecuzione posticipata.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elementi](../designers/elements-xelement-dynamic-property.md)
