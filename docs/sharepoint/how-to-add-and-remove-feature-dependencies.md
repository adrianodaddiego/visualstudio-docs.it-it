---
title: 'Procedura: Aggiungere e rimuovere le dipendenze delle funzionalità | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9373ed07ec49bd41dad343dc447b4b2026793492
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967005"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Procedura: Aggiungere e rimuovere dipendenze di funzionalità
  La funzionalità di SharePoint può dipendere da altre funzionalità per dati o funzionalità. In questi casi, è possibile contrassegnare le altre funzionalità come le dipendenze per la funzionalità. In questo modo, il server SharePoint garantisce che le funzionalità dipendenti vengono attivate prima che la funzionalità viene attivata.

## <a name="add-dependencies"></a>Aggiungere dipendenze
 È possibile aggiungere altre funzionalità nella soluzione come dipendenze. In questo modo, è possibile assicurarsi che le funzionalità necessarie vengono installate e attivate prima di installata la funzionalità.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Per aggiungere una dipendenza da una funzionalità nella soluzione

1. Aprire la finestra di progettazione di funzionalità, espandere il **dipendenze di attivazione funzionalità** nodo, quindi scegliere il **Aggiungi** pulsante.

2. Nel **aggiungere le dipendenze di attivazione funzionalità** finestra di dialogo scegliere la **aggiungere una dipendenza da funzionalità nella soluzione** pulsante di opzione, scegliere il titolo della funzionalità che si desidera aggiungere come dipendenza e quindi Scegliere il **Add** pulsante.

     È possibile aggiungere più di una funzionalità selezionando più titoli quando si sceglie la **Ctrl** chiave.

## <a name="addi-custom-dependencies"></a>Addi dipendenze personalizzate
 È possibile aggiungere le funzionalità che sono già state distribuite in un server SharePoint come dipendenza. In questo modo, il processo di attivazione SharePoint verifica per assicurarsi che tutte le funzionalità dipendenti vengono attivate prima di installata la funzionalità.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Per aggiungere una dipendenza dall'ID funzionalità

1. Aprire la finestra di progettazione di funzionalità, espandere il **dipendenze di attivazione funzionalità** nodo, quindi scegliere il **Aggiungi** pulsante.

2. Nel **aggiungere le dipendenze di attivazione funzionalità** finestra di dialogo scegliere la **Aggiungi dipendenza personalizzata** pulsante di opzione.

3. Nel **ID funzionalità** testo casella, immettere il GUID per la funzionalità che si desidera contrassegnare come una dipendenza di attivazione e quindi scegliere il **Add** pulsante.

## <a name="edit-custom-dependencies"></a>Modificare le dipendenze personalizzate
 È possibile modificare le dipendenze personalizzate aggiunto in precedenza. Tuttavia, le funzionalità dipendenti che sono nella soluzione possono solo essere rimosso, non modificato.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Per modificare una dipendenza da una funzionalità nella soluzione

1. Aprire la finestra di progettazione di funzionalità e quindi espandere la **dipendenze di attivazione funzionalità** nodo.

2. Scegliere il nome della funzionalità che si desidera modificare e quindi scegliere il **modifica** pulsante.

3. Nel **modifica di dipendenza di attivazione funzionalità personalizzata** finestra di dialogo, modificare il titolo, ID funzionalità o la descrizione e quindi scegliere il **Submit** pulsante.

## <a name="remove-dependencies"></a>Rimuovere le dipendenze

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Per rimuovere una dipendenza di una funzionalità nella soluzione

1. Nella finestra di progettazione di funzionalità, espandere la **dipendenze di attivazione funzionalità** nodo, scegliere il nome della funzionalità che si desidera rimuovere e quindi scegliere il **rimuovere** pulsante.

## <a name="see-also"></a>Vedere anche
- [Creare funzionalità di SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Procedura: Personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: Aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
