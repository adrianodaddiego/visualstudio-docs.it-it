---
title: Proprietà delle corsie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dd4435ed0930a920cd36e741ac7461e6f95ba815
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701520"
---
# <a name="properties-of-swimlanes"></a>Proprietà delle corsie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiungere le corsie a un oggetto diagram. Le corsie dividono un diagramma in aree verticale o orizzontale. È possibile definire altre forme da visualizzare all'interno di corsie. Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Le corsie hanno le proprietà elencate nella tabella seguente.  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Colore di riempimento del corpo|Il colore di riempimento per il corpo della corsia.|Bianco|  
|Colore di riempimento intestazione|Il colore di riempimento per l'intestazione della corsia.|DarkGray|  
|Colore separatore|Colore della linea di separazione.|LightGray|  
|Stile dei separatori di riga|Lo stile della linea di separazione (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, o `Custom`).|`Dash`|  
|Spessore separatore|Lo spessore della linea di separazione in pollici.|0.03125|  
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa corsia.|Nero|  
|Modificatore di accesso|Il livello di accesso della classe (`public` o `internal`).|Public|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice che viene generata da questa corsia.|\<nessuno>|  
|Genera l'errore doppia derivati|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla corsia (`none`, `abstract` o `sealed`).|none|  
|Corsia di base|Classe di base di questa corsia.|(nessuno)|  
|Nome|Il nome di questa corsia.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi che è affiliato a questa corsia.|Spazio dei nomi corrente|  
|Tipo della descrizione comando|Come viene definito la descrizione comando (`fixed`, `variable`, o `none`). Se `fixed`, quindi il valore della `Fixed Tooltip Text` proprietà viene utilizzata; se `variable`, quindi la descrizione comando è definito nel codice personalizzato.|\<nessuno>|  
|Note|Note informali associate a questa corsia.|\<nessuno>|  
|Allineamento|Allineamento orizzontale o verticale.|Vertical|  
|Altezza iniziale|Altezza iniziale della corsia, in pollici. Applicabile solo a corsie orizzontali.|0|  
|Larghezza iniziale|Larghezza iniziale della corsia, in pollici. Applicabile solo a corsie verticali.|0|  
|Espone il colore del testo|Se `True`, l'utente può impostare il colore di un oggetto swimlane nella finestra di progettazione generata. Per procedere, fare doppio clic la forma di corsia e fare clic su **Aggiungi esposta**.|False|  
|Descrizione|Consente di documentare la finestra di progettazione generata.|\<nessuno>|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per fare riferimento a questa classe di swimlane.|\<nessuno>|  
|Testo della descrizione comando fissa|Testo che viene usato per una descrizione comando fissa.|\<nessuno>|  
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida F1 per questa corsia.|\<nessuno>|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
