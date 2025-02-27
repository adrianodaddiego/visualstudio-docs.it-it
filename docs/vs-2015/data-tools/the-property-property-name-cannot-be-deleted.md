---
title: La proprietà &lt;nome della proprietà&gt; non può essere eliminato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 50e91c47ef848eda51fe71c9dce09cd1ea4893a8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106455"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La proprietà &lt;nome della proprietà&gt; non può essere eliminato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La proprietà \<nome proprietà > non può essere eliminato perché è impostato come proprietà Discriminator per l'ereditarietà tra \<nome classe > e \<nome classe >  
  
 La proprietà selezionata è impostata come **Proprietà Discriminator** per l'ereditarietà tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano alla configurazione dell'ereditarietà tra le classi di dati.  
  
 Impostare **Proprietà Discriminator** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. In Progettazione relazionale oggetti selezionare la linea di ereditarietà che connette le classi di dati indicate nel messaggio di errore.  
  
2. Impostare **Proprietà Discriminator** su una diversa proprietà.  
  
3. Provare a eliminare nuovamente la proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Ereditarietà della classe di dati (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
