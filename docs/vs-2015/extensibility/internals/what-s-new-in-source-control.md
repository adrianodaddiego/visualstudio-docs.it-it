---
title: Novità del controllo del codice sorgente
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087319"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Cosa&#39;s di controllo del codice sorgente in Visual Studio 2015

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] è possibile fornire una soluzione di controllo codice sorgente integrato mediante l'implementazione di un pacchetto VSPackage di controllo di origine. In questa sezione vengono descritte le funzionalità di controllo del codice sorgente pacchetti VSPackage e fornisce una panoramica dei passaggi di implementazione.  
  
## <a name="the-source-control-vspackage"></a>I VSPackage di controllo del codice sorgente  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta due tipi di soluzioni di controllo di origine. In tutte le versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], è comunque possibile integrare un API dei plug-in del controllo origine basato su plug-in. È anche possibile creare un pacchetto VSPackage di controllo del codice sorgente che offre un'avanzato-integrazione, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] percorso adatto per le soluzioni di controllo di origine che richiedono un elevato livello di complessità e autonomia.  
  
 Un VSPackage può aggiungere qualsiasi tipo di funzionalità per [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Un controllo del codice sorgente VSPackage fornisce una funzionalità di controllo sorgente completo per [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], dall'interfaccia utente presentata all'utente per le comunicazioni back-end con il controllo del codice sorgente.  
  
 Implementazione di un controllo del codice sorgente VSPackage richiede una strategia di "tutto o niente". Il creatore di un pacchetto VSPackage di controllo di origine deve investire una quantità significativa di lavoro richiesto nell'implementazione di un numero di interfacce di controllo di origine e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intero controllo del codice sorgente, nonché le interfacce di tutti i pacchetti necessari per integrare correttamente con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 La procedura seguente offre una panoramica generale degli elementi necessari per implementare un pacchetto controllo del codice sorgente. Per informazioni dettagliate, vedere [creazione di un VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Creare un pacchetto VSPackage che fornisce un servizio di controllo di origine privata.  
  
2. Implementare le interfacce dei servizi correlati al controllo origine che sono offerti dal [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (ad esempio, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interface).  
  
3. Registrare VSPackage di controllo del codice sorgente.  
  
4. Implementare tutte controllo del codice sorgente dell'interfaccia utente, tra cui le voci di menu, finestre di dialogo, barre degli strumenti e menu di scelta rapida.  
  
5. Tutti gli eventi correlati al controllo origine vengono passati al controllo del codice sorgente VSackage quando è attiva ma deve essere gestito dal pacchetto VSPackage.  
  
6. VSPackage di controllo del codice sorgente deve essere in ascolto degli eventi, ad esempio quelli implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfaccia, nonché gli eventi di traccia progetto documento (TPD) (come implementato dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaccia) e intraprendere le azioni necessarie.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Panoramica](../../extensibility/internals/source-control-integration-overview.md)   
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
