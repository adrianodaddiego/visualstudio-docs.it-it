---
title: Panoramica del modello di automazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699499"
---
# <a name="automation-model-overview"></a>Panoramica del modello di automazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il modello di automazione è costituito da un set di oggetti su cui è possibile scrivere un componente aggiuntivo di Visual Studio o estensione. Un componente aggiuntivo è un'applicazione che è possibile modificare l'ambiente di Visual Studio e automatizzare le attività comuni. Un'estensione di Visual Studio possa creare componenti personalizzati di Visual Studio o aggiungere la funzionalità dei componenti standard, ad esempio l'editor di testo.  
  
## <a name="objects-in-the-automation-model"></a>Oggetti nel modello di automazione  
 Il modello di automazione è costituito da gruppi di oggetti che consentono di controllare aspetti principali dell'ambiente comune correlati. Di seguito è riportato un diagramma che mostra il vasto set di oggetti che compongono il modello di automazione.  
  
 ![Oggetto grafico automazione di Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Oggetti di automazione di Visual Studio  
  
 Per altre informazioni, vedere [estendendo l'ambiente di Visual Studio](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 L'ambiente fornisce un modello per aree funzionali diverse. Ad esempio, vi è un modello di codice per diversi elementi che potrebbero risultare nel codice. È disponibile un modello di documento per vari elementi del documento. Un'area, l'area di progetto, è di particolare interesse per i provider di VSPackage. I nuovi tipi di progetto per contribuire al modello di automazione in modo analogo a come probabilmente si desidererà [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] contribuiscono al modello di automazione. Che procedura [che fornisce un'automazione per i pacchetti VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Posizioni in cui è possibile considerare l'estensione del modello di automazione dell'ambiente:  
  
- Progetto  
  
- Document  
  
- Codice  
  
- Compilazione  
  
  Per altre informazioni sull'automazione, vedere [automazione ed estendibilità in Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Questo documento e i documenti vengono forniti collegamenti per poter prendere decisioni relative a come si deve fornire l'automazione per il pacchetto VSPackage.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare un componente aggiuntivo](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
