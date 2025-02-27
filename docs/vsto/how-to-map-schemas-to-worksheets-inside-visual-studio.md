---
title: 'Procedura: Mappare schemi a fogli di lavoro in Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80a19924aaf4fa0afe8e809006ada7fada0288f3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428108"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Procedura: Mappare schemi a fogli di lavoro in Visual Studio
  È possibile eseguire il mapping di un XML schema a un foglio di lavoro mentre il foglio di lavoro è aperta in Visual Studio. Si usano gli stessi strumenti di Microsoft Office Excel che usano quando la cartella di lavoro viene aperto all'esterno di Visual Studio. Il progetto di Office consente di creare gli stessi oggetti se lo schema è mappato al foglio di lavoro prima o dopo aver creato la soluzione di Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> È possibile usare gli schemi XML in più parti nelle soluzioni Excel.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Eseguire il mapping di un XML schema a un foglio di lavoro di Excel in Visual Studio

1. Aprire il progetto di modello o cartella di lavoro di Excel all'interno di Visual Studio.

2. Fare clic sul foglio di lavoro per spostare lo stato attivo alla finestra di progettazione.

3. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Nel **XML** gruppo, fare clic su **origine**.

     Il **origine XML** verrà visualizzata la finestra.

5. Nel **origine XML** finestra, fare clic su **XML Maps**.

     Il **esegue il mapping XML** verrà visualizzata la finestra di dialogo.

6. Nel **XML Maps** della finestra di dialogo fare clic su **Add**.

7. Passare al file di schema, selezionarlo e quindi fare clic su **aperto**.

8. Fare clic su **OK**.

     Lo schema è rappresentato nel **origine XML** finestra. Nel progetto, un oggetto tipizzato <xref:System.Data.DataSet> viene generato basato sullo schema e un <xref:System.Windows.Forms.BindingSource> viene creato.

9. Trascinare gli elementi dal **origine XML** finestra per i punti nel foglio di lavoro in cui si desidera corrispondenti controlli da creare.

     Se si trascina un elemento dello schema non ripetute, il progetto di Office genera un' <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo a cui viene associato automaticamente il <xref:System.Windows.Forms.BindingSource>.

     Se si trascina un elemento ripetuto dello schema, il progetto di Office genera un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo che non viene associato automaticamente a un'origine dati. Per altre informazioni, vedere [schemi XML e i dati in a livello di documento personalizzazioni](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Mappare schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [XML schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
