---
title: Impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 79ed1bd03e90a92d8246c5f51a6ad64d52758167
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260962"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati

È possibile creare controlli associati a dati trascinando elementi dal **Zdroje dat** finestra in Progettazione Windows Form o WPF designer. Ogni elemento di **Zdroje dat** finestra dispone di un controllo predefinito che viene creato quando viene trascinato nella finestra di progettazione. Tuttavia, è possibile scegliere di creare un altro controllo.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Impostare i controlli da creare per le tabelle di dati o oggetti

Prima di trascinare gli elementi che rappresentano le tabelle di dati o oggetti di **Zdroje dat** finestra, è possibile scegliere di visualizzare tutti i dati in un controllo o per visualizzare ogni colonna o proprietà in un controllo separato.

In questo contesto il termine *oggetto* fa riferimento a un oggetto business personalizzato, un'entità (in un Entity Data Model) o un oggetto restituito da un servizio.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Per impostare i controlli da creare per le tabelle di dati o oggetti

1. Verificare che il **WPF** finestra di progettazione o il **Windows Forms** progettazione è aperto.

2. Nel **Zdroje dat** finestra, selezionare l'elemento che rappresenta la tabella di dati o dell'oggetto che si desidera impostare.

   > [!TIP]
   > Se il **Zdroje dat** finestra non è aperta, è possibile aprirlo selezionando **View** > **Other Windows** > **Zdroje dat**.

3. Fare clic sul menu a discesa per l'elemento e quindi fare clic su uno dei seguenti elementi nel menu di scelta:

    - Per visualizzare ogni campo dati in un controllo separato, fare clic su **dettagli**. Quando si trascina l'elemento di dati nella finestra di progettazione, questa azione consente di creare un controllo con associazione a dati diversi per ogni colonna o proprietà della tabella di dati padre o dell'oggetto, insieme alle etichette per ogni controllo.

    - Per visualizzare tutti i dati in un singolo controllo, selezionare un altro controllo nell'elenco, ad esempio **DataGrid** oppure **elenco** in un'applicazione WPF, o **DataGridView** in un controllo Windows Form applicazione.

    L'elenco dei controlli disponibili dipende dalla progettazione aperta, la versione di .NET Framework le destinazioni del progetto e se aggiunta di controlli personalizzati che supportano l'associazione a dati di **casella degli strumenti**. Se il controllo che si desidera creare non è presente nell'elenco dei controlli disponibili, è possibile aggiungere il controllo all'elenco. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dei dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Per informazioni su come creare un controllo Windows Form personalizzato che può essere aggiunto all'elenco di controlli per le tabelle di dati o oggetti nel **Zdroje dat** finestra, vedere [creare un controllo utente Windows Form che supporta dati complessi associazione](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Impostare i controlli da creare per le colonne di dati o le proprietà

Prima di trascinare un elemento che rappresenta una colonna o una proprietà di un oggetto dal **Zdroje dat** finestra di progettazione, è possibile impostare il controllo da creare.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Per impostare i controlli da creare per le colonne o proprietà

1. Verificare che il **WPF** finestra di progettazione o il **Windows Forms** progettazione è aperto.

2. Nel **Zdroje dat** finestra, espandere la tabella desiderata o per visualizzare le colonne o proprietà dell'oggetto.

3. Selezionare ogni colonna o proprietà per il quale si desidera impostare il controllo da creare.

4. Fare clic sul menu a discesa per la colonna o proprietà e quindi selezionare il controllo da creare quando l'elemento viene trascinato nella finestra di progettazione.

     L'elenco dei controlli disponibili dipende dalla progettazione aperta, la versione di .NET Framework le destinazioni del progetto e dai controlli personalizzati che supportano i dati di associazione si sono aggiunte alle **casella degli strumenti**. Se il controllo da creare è nell'elenco dei controlli disponibili, è possibile aggiungere il controllo all'elenco. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dei dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Per informazioni su come creare un controllo personalizzato che può essere aggiunto all'elenco di controlli per le colonne di dati o le proprietà nel **Zdroje dat** finestra, vedere [creare un controllo utente Windows Form che supporta il data binding semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Se non si desidera creare un controllo per la colonna o proprietà, selezionare **None** nel menu a discesa. Ciò è utile se si vuole trascinare la tabella padre o l'oggetto nella finestra di progettazione, ma non da includere la colonna o specifica proprietà.

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)