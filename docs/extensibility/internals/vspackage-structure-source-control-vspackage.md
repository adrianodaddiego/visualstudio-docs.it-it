---
title: Struttura VSPackage (VSPackage di controllo codice sorgente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d609efe52955dba53b8c8890a6fcb44bb7f3f352
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332747"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struttura VSPackage (VSPackage di controllo del codice sorgente)

il SDK di pacchetto di controllo di origine fornisce indicazioni per la creazione di un pacchetto VSPackage che consentono a un implementatore di controllo di origine per integrare la propria funzionalità di controllo di origine con l'ambiente di Visual Studio. Un pacchetto VSPackage è un componente COM che in genere viene caricato su richiesta dall'ambiente di sviluppo integrato (IDE) di Visual Studio in base ai servizi che vengono annunciati dal pacchetto in relative voci del Registro di sistema. Ogni pacchetto VSPackage deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Un pacchetto VSPackage in genere vengono utilizzati i servizi offerti dall'IDE di Visual Studio e offre alcuni servizi specifici.

Un pacchetto VSPackage dichiara le voci di menu e viene stabilito uno stato dell'elemento predefinito tramite il file con estensione vsct. IDE di Visual Studio consente di visualizzare le voci di menu in questo stato fino a quando non viene caricato il pacchetto VSPackage. Successivamente, l'implementazione di VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> viene chiamato per abilitare o disabilitare le voci di menu.

## <a name="source-control-package-characteristics"></a>Caratteristiche di pacchetto di origine controllo

Un pacchetto VSPackage di controllo di origine è integrato in Visual Studio. La semantica di VSPackage include:

- Interfaccia da implementare poiché è un pacchetto VSPackage (il `IVsPackage` interfaccia)

- Implementazione dei comandi dell'interfaccia utente (file con estensione vsct e l'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia)

- Registrazione del pacchetto VSPackage con Visual Studio.

Il controllo del codice sorgente VSPackage deve comunicare con queste altre entità di Visual Studio:

- Progetti

- Editor

- Soluzioni

- WINDOWS

- La tabella documenti in esecuzione

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Servizi dell'ambiente Visual Studio che possono essere usati

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Servizio SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP interfacce implementate e chiamato

Un pacchetto controllo del codice sorgente è un pacchetto VSPackage e pertanto può interagire direttamente con gli altri pacchetti VSPackage registrati con Visual Studio. Per garantire l'ampia gamma di controllo del codice sorgente, un controllo del codice sorgente VSPackage può gestire le interfacce fornite dai progetti o la shell.

Tutti i progetti di Visual Studio devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> venga riconosciuta come un progetto nell'IDE di Visual Studio. Tuttavia, questa interfaccia non specializzata sufficiente per controllo del codice sorgente. I progetti che dovrebbero essere nel gruppo origine controllano implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Questa interfaccia viene utilizzata dal pacchetto VSPackage di controllo del codice sorgente per eseguire query di un progetto del relativo contenuto e fornire i glifi e informazioni di associazione (le informazioni necessarie per stabilire una connessione tra il percorso del server e il percorso del disco di un progetto che si trova sotto controllo del codice sorgente).

Il controllo del codice sorgente pacchetto VSPackage implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, che a sua volta consente ai progetti di registrarsi per il controllo di origine e recuperare le icone di stato.

Per un elenco completo di interfacce che debba prendere in considerazione un pacchetto VSPackage di controllo di origine, vedere [interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Vedere anche

- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)