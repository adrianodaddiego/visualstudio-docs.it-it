---
title: 'Procedura: Includere un Assembly personalizzato in una funzionalità di integrazione applicativa dei dati | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6de3313dad06c009244a8b784e81bf7d2a768c3b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443120"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Procedura: Includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati
  Il progetto può fare riferimento agli assembly da altri progetti nella stessa soluzione. Tuttavia, è necessario aggiungere questi assembly nel file di funzionalità del progetto usando il **assegnazione fa riferimento agli assembly di oggetti LobSystem** nella finestra di dialogo.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Per includere un assembly personalizzato in una funzionalità di connettività (BDC) dei dati di business

1. Nelle **Esplora soluzioni**, scegliere la cartella che contiene il modello di integrazione applicativa dei dati.

2. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

3. Nel **delle proprietà** finestra, scegliere il **assembly** proprietà e quindi sui puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET per dispositivi mobili Ellisse progettazione")).

     Il **Assign fare riferimento agli assembly di oggetti LobSystem** verrà visualizzata la finestra di dialogo.

4. Nel **selezionare un Assembly** scegliere l'assembly personalizzato.

    > [!NOTE]
    > Gli assembly vengono visualizzati solo nel **Assign fare riferimento agli assembly di oggetti LobSystem** finestra di dialogo se è stato aggiunto un riferimento al progetto che contiene l'assembly. Per altre informazioni, vedere [Procedura: Aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

5. Nel **le proprietà di riferimento** gruppo, aprire l'elenco visualizzato per il **ambito LobSystem** proprietà, scegliere il sistema LOB dei metodi che usano l'assembly personalizzato e quindi scegliere il **OK**  pulsante.

    > [!NOTE]
    > Per eseguire il debug di codice nell'assembly personalizzato, è necessario aggiungere l'assembly al pacchetto della soluzione. Per altre informazioni, vedere [Procedura: Aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Procedura: Aggiungere un file di modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: Creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)
- [Dati di business Integragte in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
