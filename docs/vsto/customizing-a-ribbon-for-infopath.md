---
title: Personalizzare una barra multifunzione per InfoPath
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6ec01b49ca61fcf295884deafa280c8ee33a2b4c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437449"
---
# <a name="customize-a-ribbon-for-infopath"></a>Personalizzare una barra multifunzione per InfoPath
  Quando si personalizza la barra multifunzione in Microsoft Office InfoPath, è necessario considerare la posizione in cui la barra multifunzione personalizzata verrà visualizzata nell'applicazione. In[!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] è possibile visualizzare la barra multifunzione nei tre tipi seguenti di finestre dell'applicazione InfoPath:

- Finestre in cui viene visualizzato un modello di form aperto in modalità di progettazione.

- Finestre in cui è visualizzato un form basato su un modello di form.

- Finestra Anteprima di stampa.

  **Si applica a:** Le informazioni contenute in questo argomento si applicano ai progetti di componente aggiuntivo VSTO per InfoPath 2010. Per altre informazioni, vedere [funzionalità disponibili in base al tipo di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).

  Utenti e progettisti aprono un modello di form in modalità di progettazione per modificarne l'aspetto e il layout. Gli utenti aprono i form basati su un modello di form per aggiungere contenuto.

  La finestra Anteprima di stampa consente ai progettisti e agli utenti di visualizzare in anteprima le pagine di un form o di un modello di form prima della stampa.

> [!NOTE]
> La scheda **AddIns** non è presente nella finestra Anteprima di stampa. Se si vuole visualizzare una scheda personalizzata nella finestra Anteprima di stampa, verificare che la proprietà **OfficeId** della scheda non sia impostata su **TabAddIns**.

 È necessario specificare il tipo di barra multifunzione di ogni finestra in cui si vuole visualizzare la barra multifunzione.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Specificare il tipo della barra multifunzione nella finestra di progettazione della barra multifunzione
 Se si usa la **della barra multifunzione (finestra di progettazione visiva)** fare clic sui **RibbonType** proprietà della barra multifunzione nel **proprietà** finestra e quindi selezionare uno degli ID della barra multifunzione descritte nella tabella seguente.

|ID della barra multifunzione|Finestra in cui verrà visualizzata la barra multifunzione all'esecuzione del progetto|
|---------------|---------------------------------------------------------------------|
|**Microsoft.InfoPath.Designer**|Finestre in cui viene visualizzato un modello di form aperto in modalità di progettazione.|
|**Microsoft.InfoPath.Editor**|Finestre in cui è visualizzato un form basato su un modello di form.|
|**Microsoft.InfoPath.PrintPreview**|Finestra Anteprima di stampa.|

 È possibile aggiungere più barre multifunzione a un progetto. Se più barre multifunzione condividono uno stesso ID di barra, eseguire l'override del metodo `CreateRibbonExtensibilityObject` nella classe `ThisAddin` del progetto per specificare la barra multifunzione da visualizzare in fase di esecuzione. Per altre informazioni, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Specificare il tipo di barra multifunzione utilizzando XML della barra multifunzione
 Se si usa l'elemento **Barra multifunzione (XML)** , controllare il valore del parametro *ribbonID* nel metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> e restituire la barra multifunzione appropriata.

 Il metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> viene generato automaticamente da Visual Studio nel file di codice della barra multifunzione. Il parametro *ribbonID* è una stringa che identifica il tipo di finestra di InfoPath che viene aperto.

 Nell'esempio di codice seguente viene illustrato come visualizzare una barra multifunzione personalizzata solo in una finestra che visualizza un modello di form in modalità di progettazione. La barra multifunzione da visualizzare viene specificata nel metodo `GetResourceText()` , generato nella classe Ribbon. Per altre informazioni sulla classe Ribbon, vedere [Ribbon XML](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]

## <a name="see-also"></a>Vedere anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
