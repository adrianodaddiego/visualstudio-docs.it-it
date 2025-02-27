---
title: 'Procedura: Aggiungere un metodo Updater | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8204b13aa0405d01590e4aeb0fe43a92b41c226f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431255"
---
# <a name="how-to-add-an-updater-method"></a>Procedura: Aggiungere un metodo Updater
  È possibile abilitare gli utenti aggiornare i dati di business in un elenco di SharePoint esterno tramite la creazione di un' *Updater* (metodo). Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Per creare un metodo Updater

1. Nella finestra di progettazione integrazione applicativa dei dati, scegliere un'entità.

2. Nella barra dei menu, scegliere **View** > **Other Windows** > **Dettagli metodo BDC**.

    Verrà visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati. Per altre informazioni su questa finestra, vedere [Cenni preliminari sugli strumenti di progettazione di modelli di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).

3. Nel **aggiungere un metodo** casella di riepilogo **Crea metodo Updater**.

    Visual Studio aggiunge i seguenti elementi al modello. Questi elementi vengono visualizzati nella finestra Dettagli metodo di integrazione applicativa dei dati.

   - Un metodo denominato **Update**.

   - Un parametro di input per il metodo.

   - Un descrittore di tipo per il parametro. Per impostazione predefinita, Visual Studio Usa il descrittore di tipo di entità definiti per il metodo Finder (ad esempio: Contatto).

   - Un'istanza del metodo per il metodo.

     Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Se l'identificatore del tipo di entità rappresenta un campo in una tabella di database che viene generato automaticamente, impostare il **campo pre-Updater** proprietà **True**.

4. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida del servizio file di codice che è stato generato per l'entità e quindi scegliere **Visualizza codice**.

    Aprire il file di codice servizio entità nel **Editor di codice**. Per altre informazioni su tale file, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Aggiungere codice al metodo Update di aggiornare i dati. Nell'esempio seguente aggiorna le informazioni per un contatto nel database di esempio AdventureWorks per SQL Server.

   > [!NOTE]
   > Sostituire il valore del `ServerName` campo con il nome del server.

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>Vedere anche
- [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
