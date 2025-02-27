---
title: Conversione tra tipi di sistema di progetto SharePoint e altri tipi di progetto di Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 553d6a4dfb60079aa16487f276d6f392926bb089
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952022"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Eseguire la conversione tra tipi di sistema di progetto SharePoint e altri tipi di progetto di Visual Studio
  In alcuni casi potrebbe essere un oggetto nel sistema del progetto SharePoint e si desidera usare le funzionalità di un oggetto corrispondente nel modello oggetto di automazione di Visual Studio o nel modello oggetto di integrazione, o viceversa. In questi casi, è possibile usare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo del servizio di progetto SharePoint per convertire l'oggetto in un modello a oggetti diversi.

 Ad esempio, potrebbe essere un' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetti, ma si desidera utilizzare i metodi che sono disponibili solo in un <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> oggetto. In questo caso, è possibile usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo per convertire le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> a un <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.

 Per altre informazioni sul modello oggetto di automazione di Visual Studio e il modello a oggetti integrazione Visual Studio, vedere [estensioni degli strumenti Panoramica del modello di programmazione di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Tipi di conversioni
 La tabella seguente elenca i tipi di questo metodo può eseguire la conversione tra il sistema di progetto SharePoint e gli altri modelli di oggetto di Visual Studio.

|Tipo di sistema di progetto SharePoint|Tipi corrispondenti in modelli a oggetti di automazione e integrazione|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> oppure<br /><br /> Qualsiasi interfaccia nel modello a oggetti integrazione Visual Studio che viene implementato dall'oggetto COM sottostante per il progetto. Tali interfacce includono <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (o un'interfaccia derivata), e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Per un elenco delle interfacce principali che vengono implementate dai progetti, vedere [componenti di base del modello di progetto](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> oppure<br /><br /> Oggetto<xref:System.UInt32> valore (detto anche un VSITEMID) che identifica il membro del progetto nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> che lo contiene. Questo valore può essere passato per il *itemid* parametri di alcuni <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metodi.|

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo per convertire un' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> dell'oggetto a un <xref:EnvDTE.Project>.

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 L'esempio presenta i requisiti seguenti:

- Un'estensione del sistema del progetto SharePoint che contiene un riferimento per la *EnvDTE* assembly. Per altre informazioni, vedere [estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Codice che registra il `projectService_ProjectAdded` metodo per gestire i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> eventi di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto. Per un esempio, vedere [Procedura: Creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Vedere anche

- [Usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Procedura: Recuperare il servizio di progetto SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Estensioni degli strumenti Panoramica del modello di programmazione di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
