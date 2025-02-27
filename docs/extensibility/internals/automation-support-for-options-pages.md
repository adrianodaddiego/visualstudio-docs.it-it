---
title: Supporto di automazione per le pagine di opzioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bf997205979cdfbb9c9f03492a5943f458e2d9c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342267"
---
# <a name="automation-support-for-options-pages"></a>Supporto di automazione per le pagine di opzioni
I VSPackage possono fornire personalizzata **opzioni** alle finestre di dialogo per il **Tools** menu (**opzioni del menu Strumenti** pagine) in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e può renderli disponibili per l'automazione modello.

## <a name="tools-options-pages"></a>Opzioni del menu Strumenti (pagine)
 Per creare un **ToolsOptions** pagina, un pacchetto VSPackage deve fornire un'implementazione del controllo utente restituita all'ambiente tramite l'implementazione di VSPackage del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (metodo). (Oppure, per codice gestito, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (metodo).)

 È facoltativo, ma fortemente consigliato, per consentire l'accesso a questa nuova pagina tramite il modello di automazione. È possibile farlo con i passaggi seguenti:

1. Estendere il <xref:EnvDTE._DTE.Properties%2A> oggetto tramite l'implementazione di un oggetto derivato IDispatch.

2. Restituiscono un'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo (o per il codice gestito il <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> (metodo)) per l'oggetto derivato IDispatch.

3. Quando un consumer di automazione chiama il <xref:EnvDTE._DTE.Properties%2A> metodo su un oggetto personalizzato **opzione** pagina delle proprietà, l'ambiente Usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo per ottenere un oggetto personalizzato **opzioni del menu Strumenti** automazione della pagina implementazione.

4. L'oggetto di automazione del pacchetto VSPackage viene quindi usato per fornire a ogni <xref:EnvDTE.Property> restituito da <xref:EnvDTE._DTE.Properties%2A>.

   Per un esempio di implementazione di una classe personalizzata **ToolsOptions** pagina, vedere [esempi di VSSDK](https://aka.ms/vs2015sdksamples).

## <a name="see-also"></a>Vedere anche
- [Esporre oggetti del progetto](../../extensibility/internals/exposing-project-objects.md)