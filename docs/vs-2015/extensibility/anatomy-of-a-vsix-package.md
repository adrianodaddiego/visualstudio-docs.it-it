---
title: Anatomia di un pacchetto VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86c2beeab5fba0224fbdfb104d01ee5c28bba158
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699149"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia di un pacchetto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un pacchetto VSIX non è un file con estensione VSIX che contiene uno o più estensioni di Visual Studio, insieme a Visual Studio Usa per classificare e installare le estensioni dei metadati. Tali metadati sono contenuti nel manifesto VSIX e il file [Content_Types] XML. Un pacchetto VSIX può anche contenere uno o più file vsixlangpack per fornire il testo di programma di installazione localizzata e può contenere pacchetti VSIX aggiuntivi per installare le dipendenze.  
  
 Il formato di pacchetto VSIX conforme allo standard Open Packaging Conventions (OPC). Il pacchetto contiene file binari e i file di supporto, insieme a un file [Content_Types] XML e un'estensione VSIX file manifesto. Un pacchetto VSIX può contenere l'output di più progetti, o anche più pacchetti che hanno i propri manifesti.  
  
> [!NOTE]
> I nomi dei file inclusi nei pacchetti VSIX non devono includere spazi, né caratteri riservati in identificatori URI (Uniform Resource), come definito in [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Il manifesto VSIX  
 Il manifesto VSIX contiene informazioni sulle estensioni da installare e segue lo Schema VSX. Per altre informazioni, vedere [riferimenti su VSIX Extension Schema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Per un esempio di manifesto VSIX, vedere [elemento PackageManifest (elemento radice, Schema VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Il manifesto VSIX deve essere denominato `extension.vsixmanifest` quando è incluso in un file con estensione VSIX.  
  
## <a name="the-content"></a>Il contenuto  
 Un pacchetto VSIX può contenere i modelli, gli elementi della casella degli strumenti, i pacchetti VSPackage o qualsiasi altro tipo di estensione supportata da Visual Studio.  
  
## <a name="language-packs"></a>Language Pack  
 Un pacchetto VSIX può contenere uno o più file vsixlangpack per fornire il testo localizzato durante l'installazione. Per altre informazioni, vedere [localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Le dipendenze e riferimenti  
 Un pacchetto VSIX può contenere altri pacchetti VSIX come riferimenti. Ognuno di questi altri pacchetti deve includere il proprio manifesto VSIX.  
  
 Se un utente tenta di installare un'estensione con dipendenze, il programma di installazione verifica che gli assembly necessari siano installati nel sistema dell'utente. Se non sono possibile trovare gli assembly richiesti **estensioni e aggiornamenti** Visualizza un elenco degli assembly mancanti.  
  
 Se il manifesto di estensione include uno o più [riferimento](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) gli elementi **estensioni e aggiornamenti** confronta il manifesto di ogni riferimento alle estensioni installate nel sistema e viene installato il estensione di riferimento, se non è già installato. Se è installata una versione precedente di un'estensione di cui viene fatto riferimento, la versione più recente lo sostituisce.  
  
 Se un progetto in una soluzione multiprogetto include un riferimento a un altro progetto nella stessa soluzione, il pacchetto VSIX include le dipendenze del progetto. È possibile eseguire l'override di questo comportamento facendo clic sul riferimento per il progetto interno, quindi, nella **proprietà** finestra, l'impostazione di **Output i gruppi inclusi nel VSIX** proprietà `BuiltProjectOutputGroup`.  
  
 Per includere le DLL satellite da assembly di riferimento del pacchetto VSIX, aggiungere `SatelliteDllsProjectOutputGroup` per il **Output i gruppi inclusi nel VSIX** proprietà.  
  
## <a name="installation-location"></a>Percorso di installazione  
 Durante l'installazione **estensioni e aggiornamenti** Cerca il contenuto del pacchetto VSIX in una cartella in % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Per impostazione predefinita, l'installazione si applica solo all'utente corrente, perché % LocalAppData % è una directory specifiche dell'utente. Tuttavia, se si imposta la [AllUsers](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) elemento del manifesto per `True`, verrà installato l'estensione in... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions e sarà disponibile a tutti gli utenti del computer.  
  
## <a name="contenttypesxml"></a>[Content_Types] XML  
 Il file [Content_Types] XML identifica i tipi di file nel file. VSIX espansa. Visual Studio Usa questo file durante l'installazione del pacchetto, ma non viene installato il file stesso. Per altre informazioni su questo file, vedere [struttura del Content_types\]File con estensione XML](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Un file [Content_Types] XML è necessario per la standard Open Packaging Conventions (OPC). Per altre informazioni su OPC, vedere [OPC: Un nuovo Standard per la creazione di pacchetti dati](http://go.microsoft.com/fwlink/?LinkID=148207) sul sito Web MSDN.
