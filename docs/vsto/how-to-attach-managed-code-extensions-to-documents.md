---
title: 'Procedura: Associare estensioni di codice gestito a documenti'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f56d51817491726e6011e965bfd6d68630bb0dbf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441808"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Procedura: Associare estensioni di codice gestito a documenti
  È possibile collegare un assembly di personalizzazione in un documento esistente di Microsoft Office Word o una cartella di lavoro di Microsoft Office Excel. Il documento o la cartella di lavoro può essere in qualsiasi formato di file che è supportato per i progetti di Microsoft Office e gli strumenti di sviluppo in Visual Studio. Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Per collegare una personalizzazione a un documento di Word o Excel, usare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodo di <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Poiché il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe è progettata per essere eseguito su un computer in cui è installato Microsoft Office, è possibile usare questo metodo nelle soluzioni che non sono direttamente correlate allo sviluppo di Microsoft Office (ad esempio, un'applicazione Windows Forms o console).

> [!NOTE]
> La personalizzazione non verrà caricato se il codice prevede che i controlli che non hanno il documento specificato.

 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [ricerca per categorie Collegare o scollegare un assembly VSTO da un documento di Word? ](http://go.microsoft.com/fwlink/?LinkId=136782).

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Per associare estensioni di codice gestito a un documento

1. In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto Windows Forms, aggiungere un riferimento per la *ServerDocument* e  *VisualStudio* assembly.

2. Aggiungere il codice seguente **importazioni** oppure **usando** istruzioni all'inizio del file di codice.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Chiamare il metodo statico <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> (metodo).

     Il codice seguente viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> rapporto di overload. Questo overload accetta il percorso completo del documento e una <xref:System.Uri> che specifica il percorso del manifesto della distribuzione per la personalizzazione si desidera collegare al documento. Questo esempio si presuppone che un documento di Word denominato **WordDocument1.docx** sul desktop, e che il manifesto di distribuzione si trova in una cartella denominata **Publish** che è anche sul desktop.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera collegare la personalizzazione. Il computer deve disporre di Visual Studio 2010 Tools per Office Runtime installato.

## <a name="see-also"></a>Vedere anche
- [Gestire documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Procedura: Rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifesti dell'applicazione e distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
