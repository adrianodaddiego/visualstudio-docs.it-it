---
title: "Procedura: Creare un'associazione tra entità | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce6d0bad9da4f11b5fae1daf93657c6908cf5e95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966796"
---
# <a name="how-to-create-an-association-between-entities"></a>Procedura: Creare un'associazione tra entità
  È possibile definire relazioni tra entità nel modello di integrazione applicativa dei dati (BDC) mediante la creazione di associazioni. Visual Studio genera i metodi che forniscono i consumer del modello con informazioni su ogni associazione. Questi metodi possono essere utilizzati da elenchi, applicazioni personalizzate o web part di SharePoint per visualizzare le relazioni tra i dati in un'interfaccia utente.

 È possibile creare due tipi di associazioni nella finestra di progettazione integrazione applicativa dei dati: associazioni basate sulle chiavi esterne e associazioni senza chiave esterna. Per altre informazioni, vedere [creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Per creare un'associazione tra entità

1. Nel **BusinessDataConnectivity** scheda della finestra del **della casella degli strumenti**, scegliere il **associazione** elemento.

2. Nella finestra di progettazione dell'integrazione applicativa dei dati scegliere l'entità di origine, quindi l'entità di destinazione.

     Il **Editor di associazione** viene visualizzata.

3. Se si desidera creare un'associazione basata su chiavi esterne, selezionare la **associazione chiave esterna** casella di controllo.

    1. Nel **ID origine** della colonna della **Mapping identificatori** tabella, scegliere l'identificatore accanto a ogni descrittore di tipo corrispondente visualizzato nella **campo** colonna.

         Ad esempio, nel **ID di origine** colonna, selezionare `ContactID` accanto al `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` descrittore di tipo e il `ReadItem.salesOrder.SalesOrder.ContactID` descrittore di tipo.

4. Se si desidera creare un'associazione senza chiave esterna, deselezionare il **associazione chiave esterna** casella di controllo.

5. Fare clic sul pulsante **OK** .

6. Nella finestra di progettazione integrazione applicativa dei dati, verrà visualizzata una linea che rappresenta l'associazione tra entità di origine e l'entità di destinazione.

     Visual Studio aggiunge un metodo AssociationNavigator alla classe del servizio dell'entità di destinazione e la classe di servizio dell'entità di origine. Per altre informazioni sui metodi AssociationNavigator, vedere [operazioni supportate](http://go.microsoft.com/fwlink/?LinkId=169286).

7. Nel metodo AssociationNavigator dell'entità di origine, aggiungere il codice che restituisce una raccolta di entità di destinazione.

8. Nel metodo AssociationNavigator dell'entità di destinazione, aggiungere il codice che restituisce l'entità di origine correlati.

     Per esempi di metodi AssociationNavigator, vedere [creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Vedere anche
- [Creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)
- [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
- [Procedura: Definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Procedura dettagliata: Creare un elenco esterno in SharePoint utilizzando i dati di business](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
