---
title: Automazione per il codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e4d47a72adf787f5d560374e1c44743004d25f9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954790"
---
# <a name="providing-automation-for-code"></a>Automazione per il codice
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Creazione di un modello di automazione per il codice non è obbligatorio. il SDK di ambiente non è incluso un esempio per questa operazione. Per informazioni su modelli di codice, vedere il <xref:EnvDTE.CodeModel> oggetto.  
  
 Per implementare un modello di codice, è necessario implementare le interfacce che sono determinate dalla struttura dei dati interna. Gli oggetti devono essere derivati dal `IDispatch` classe.  
  
 Gli oggetti che si estendono, <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel>, sono disponibili le <xref:EnvDTE.Project> dell'oggetto e simile al seguente:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 È possibile scegliere di implementare solo il `CodeModel` o il `FileCodeModel` interfaccia nell'oggetto di cui si esce dalle `Project` e <xref:EnvDTE.ProjectItem> oggetti. Fornire qualsiasi funzionalità da questa interfaccia appropriata per il sistema di progetto.  
  
 Se si desidera aggiungere le funzionalità, ad esempio metodi o proprietà, che non sono disponibili dallo standard `CodeModel` e `FileCodeModel` interfacce, creare un'interfaccia che eredita da standard. Assicurarsi di documentare con il sistema di progetto in modo che gli utenti finali sarà in grado di cercare l'elemento. Restituire l'interfaccia standard, ma l'utente può chiamare il `QueryInterface` metodo o il cast all'interfaccia se è noto a esistere.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)
