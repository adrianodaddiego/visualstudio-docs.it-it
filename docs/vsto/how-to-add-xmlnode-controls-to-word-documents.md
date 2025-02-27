---
title: 'Procedura: Aggiungere controlli XMLNode ai documenti di Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f0f849088a2c3cc726adc6054aef1ff7a7c1c52f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427413"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Procedura: Aggiungere controlli XMLNode ai documenti di Word
  **Importante** le informazioni definite in questo argomento relative a Microsoft Word sono presentati in modo esclusivo per il vantaggio e uso di singoli utenti e le organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che usano o lo sviluppo i programmi eseguiti su, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio del 2010 quando Microsoft ha rimosso un'implementazione di una funzionalità specifica correlato a XML personalizzata da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli singoli individui o organizzazioni negli Stati Uniti o relativo territori che usano o lo sviluppo di programmi in esecuzione in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti concessi in licenza prima di tale data o acquistati e concesso in licenza per l'utilizzo di fuori degli Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Quando si esegue il mapping di un elemento di schema non ripetuto XML a un documento di Microsoft Office Word, Visual Studio aggiunge automaticamente un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo al documento. Per informazioni sul mapping di elementi ripetuti di XML schema, vedere [come: Aggiungere controlli XMLNodes ai documenti Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).

> [!NOTE]
> Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo non è disponibile il **della casella degli strumenti** o il **Zdroje dat** finestra che non è possibile creare a livello di codice.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>Per aggiungere un controllo XMLNode a un documento

1. Nel documento nella finestra di progettazione di Visual Studio, sulla barra multifunzione, fare clic sui **sviluppatore** scheda.

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. Nel **XML** gruppo, fare clic su **Schema**.

     Il **modelli e componenti aggiuntivi** verrà visualizzata la finestra di dialogo.

3. Scegliere il **XML Schema** scheda.

4. Fare clic su **aggiungere lo Schema**.

     Il **Aggiungi Schema** verrà visualizzata la finestra di dialogo.

5. Selezionare uno schema XML che contiene gli elementi dello schema non ripetuto dal **Aggiungi Schema** finestra di dialogo e fare clic su **Open**.

     Il **le impostazioni dello Schema** verrà visualizzata la finestra di dialogo.

6. Assegnare un alias o fare clic su **OK** aggiungere lo schema senza un alias.

     Lo schema viene aggiunto per il **Aggiungi Schema** nella finestra di dialogo.

7. Nel **Aggiungi Schema** finestra di dialogo, fare clic su **OK**.

8. Il **struttura XML** Visualizza il riquadro attività.

9. Fare clic sull'elemento di schema non ripetuto nel **struttura XML** riquadro attività per aggiungerlo al documento.

     Un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo viene creato e aggiunto al progetto.

## <a name="see-also"></a>Vedere anche
- [Controllo XMLNode](../vsto/xmlnode-control.md)
- [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
