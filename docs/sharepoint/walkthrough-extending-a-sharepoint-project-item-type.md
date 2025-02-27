---
title: 'Procedura dettagliata: Estensione di un tipo di elemento di progetto SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4922b791ea3ad7ab58c231342e11b5c175d4895
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430349"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Procedura dettagliata: Estendere un tipo di elemento di progetto SharePoint
  È possibile usare la **Business Data Connectivity Model** elemento del progetto per creare un modello per il servizio di integrazione applicativa dei dati (BDC) in SharePoint. Per impostazione predefinita, quando si crea un modello utilizzando questo elemento del progetto, i dati nel modello non vengono visualizzati agli utenti. È anche necessario creare un elenco esterno in SharePoint per consentire agli utenti di visualizzare i dati.

 In questa procedura dettagliata, si creerà un'estensione per il **Business Data Connectivity Model** elemento del progetto. Gli sviluppatori possono usare l'estensione per creare un elenco esterno nel progetto che consente di visualizzare i dati nel modello di integrazione applicativa dei dati. In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un'estensione di Visual Studio che esegue due attività principali:

    - Genera un elenco esterno che consente di visualizzare i dati in un modello di integrazione applicativa dei dati. L'estensione utilizza il modello a oggetti per il sistema di progetto SharePoint per generare una *Elements* file che definisce l'elenco. Aggiunge anche il file al progetto in modo che venga distribuito insieme al modello di integrazione applicativa dei dati.

    - Aggiunge una voce di menu di scelta rapida per il **Business Data Connectivity Model** gli elementi nei **Esplora soluzioni**. Gli sviluppatori possono fare clic su questa voce di menu per generare un elenco esterno per il modello di integrazione applicativa dei dati.

- Creazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire l'assembly dell'estensione.

- L'estensione per il testing.

## <a name="prerequisites"></a>Prerequisiti
 Sono necessari i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:

- Le edizioni di Visual Studio, SharePoint e Microsoft Windows.

- Oggetto [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Conoscenza dei concetti seguenti è utile, ma non obbligatorio, completare la procedura dettagliata:

- Il servizio di integrazione applicativa dei dati in [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Per altre informazioni, vedere [architettura di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkId=177798).

- XML schema per i modelli di integrazione applicativa dei dati. Per altre informazioni, vedere [infrastruttura del modello di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkId=177799).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare due progetti:

- Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione di elemento di progetto.

- Un progetto libreria di classi che implementa l'estensione di elemento di progetto.

  Avviare la procedura dettagliata mediante la creazione di progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

3. Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.

    > [!NOTE]
    > Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.

4. Nell'elenco nella parte superiore della **nuovo progetto** finestra di dialogo, scegliere **.NET Framework 4.5**.

     Le estensioni degli strumenti di SharePoint richiedono funzionalità in questa versione di .NET Framework.

5. Scegliere il **progetto VSIX** modello.

6. Nel **Name** casella, immettere **GenerateExternalDataLists**e quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **GenerateExternalDataLists** progetto al **Esplora soluzioni**.

7. Se non si apre automaticamente sul file, aprire il menu di scelta rapida nel progetto GenerateExternalDataLists e quindi scegliere **aprire**

8. Verificare che il file vsixmanifest disponga di una voce non vuote (immettere Contoso) per il campo dell'autore, salvare il file e quindi chiuderla.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni**, aprire il menu di scelta rapida per il **GenerateExternalDataLists** nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.

2. Nel **Aggiungi nuovo progetto** finestra di dialogo, espandere il **Visual c#** oppure **Visual Basic** nodi e quindi scegliere il **Windows** nodo.

3. Nell'elenco nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5**.

4. Nell'elenco dei modelli di progetto, scegliere **libreria di classi**.

5. Nel **Name** casella, immettere **BdcProjectItemExtension**e quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **BdcProjectItemExtension** progetto alla soluzione e apre il file di codice predefinita Class1.

6. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Prima di scrivere codice per creare l'estensione dell'elemento di progetto, aggiungere i file di codice e i riferimenti ad assembly al progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Nel progetto BdcProjectItemExtension, aggiungere due file di codice che includono i nomi seguenti:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. Scegliere il progetto BdcProjectItemExtension e quindi nella barra dei menu scegliere **Project** > **Aggiungi riferimento**.

3. Sotto il **gli assembly** nodo, scegliere il **Framework** nodo e quindi selezionare la casella di controllo per ognuno degli assembly seguenti:

    - System.ComponentModel.Composition

    - WindowsBase

4. Sotto il **gli assembly** nodo, scegliere il **estensioni** nodo e quindi selezionare la casella di controllo per l'assembly seguente:

    - Microsoft.VisualStudio.SharePoint

5. Fare clic sul pulsante **OK** .

## <a name="define-the-project-item-extension"></a>Definire l'estensione dell'elemento di progetto
 Creare una classe che definisce l'estensione per il **Business Data Connectivity Model** elemento del progetto. Per definire l'estensione, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaccia. Implementare questa interfaccia ogni volta che si vuole estendere un tipo di elemento di progetto esistente.

#### <a name="to-define-the-project-item-extension"></a>Per definire l'estensione dell'elemento di progetto

1. Incollare il codice seguente nel file di codice ProjectItemExtension.

    > [!NOTE]
    > Dopo aver aggiunto questo codice, il progetto avrà alcuni errori di compilazione. Questi errori scompare quando si aggiunge codice nei passaggi successivi.

     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]

## <a name="create-the-external-data-lists"></a>Creare gli elenchi di dati esterni
 Aggiungere una definizione parziale del `GenerateExternalDataListsExtension` classe che crea un elenco di dati esterni per ogni entità nel modello di integrazione applicativa dei dati. Per creare l'elenco di dati esterni, questo codice legge prima di tutto i dati di entità nel modello di integrazione applicativa dei dati per analizzare i dati XML nel file del modello di integrazione applicativa dei dati. Quindi, crea un'istanza di elenco che si basa sul modello di integrazione applicativa dei dati e aggiunge questa istanza di elenco per il progetto.

#### <a name="to-create-the-external-data-lists"></a>Per creare elenchi di dati esterni

1. Incollare il codice seguente nel file di codice GenerateExternalDataLists.

     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per l'estensione dell'elemento di progetto è ora nel progetto. Compilare la soluzione per assicurarsi che il progetto venga compilato senza errori.

#### <a name="to-build-the-solution"></a>Per compilare la soluzione

1. Nella barra dei menu scegliere **Compila** > **Compila soluzione**.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione di elemento di progetto
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare innanzitutto il pacchetto VSIX, modificando il file vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX per la compilazione della soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il file vsixmanifest nel progetto GenerateExternalDataLists e quindi scegliere **aprire**.

     Visual Studio apre il file nell'editor del manifesto. Il file vsixmanifest è che la base per il file extension vsixmanifest richiesto da tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere [riferimenti su VSIX Extension Schema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Nel **Product Name** immettere **External Data elenco Generator**.

3. Nel **Author** casella, immettere **Contoso**.

4. Nel **Description** casella, immettere **un'estensione per gli elementi di progetto Business Data Connectivity Model che può essere utilizzato per creare un elenco di dati esterni**.

5. Nel **asset** della scheda dell'editor, scegliere il **New** pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

6. Nel **tipo** casella di riepilogo **MEFComponent**.

    > [!NOTE]
    > Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione del pacchetto VSIX. Per altre informazioni, vedere [MEFComponent Element (Schema di VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.

8. Nel **progetto** scegliere **BdcProjectItemExtension**, quindi scegliere il **OK** pulsante.

9. Nella barra dei menu scegliere **Compila** > **Compila soluzione**.

10. Assicurarsi che il progetto viene compilato e venga compilato senza errori.

11. Assicurarsi che la cartella di output di compilazione per il progetto GenerateExternalDataLists contiene ora il file GenerateExternalDataLists.

     Per impostazione predefinita, la cartella di output di compilazione è di... nella cartella \bin\Debug sotto la cartella che contiene il file di progetto.

## <a name="test-the-project-item-extension"></a>Testare l'estensione di elemento di progetto
 A questo punto si è pronti testare l'estensione dell'elemento di progetto. Innanzitutto, avviare il debug del progetto di estensione nell'istanza sperimentale di Visual Studio. Quindi, usare l'estensione nell'istanza sperimentale di Visual Studio per generare un elenco esterno per un modello di integrazione applicativa dei dati. Infine, aprire l'elenco esterno nel sito di SharePoint per verificare che funzioni come previsto.

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Se necessario, riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione GenerateExternalDataLists.

2. Nel progetto BdcProjectItemExtension, aprire il file di codice ProjectItemExtension e quindi aggiungere un punto di interruzione alla riga di codice nel `Initialize` (metodo).

3. Aprire il file di codice GenerateExternalDataLists e quindi aggiungere un punto di interruzione per la prima riga del codice nel `GenerateExternalDataLists_Execute` (metodo).

4. Avviare il debug scegliendo il **F5** chiave o, nella barra dei menu, scegliendo **Debug** > **Avvia debug**.

     Visual Studio installa l'estensione %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Generator\1.0 elenco dati e viene avviata un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-extension"></a>Per testare l'estensione

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File** > **New** > **progetto**.

2. Nel **nuovo progetto** finestra di dialogo espandere il **modelli** nodo, espandere il **Visual c#** nodo, espandere il **SharePoint** nodo e quindi Scegli **2010**.

3. Nell'elenco nella parte superiore della finestra di dialogo, verificare che **.NET Framework 3.5** sia selezionata. I progetti di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] necessaria questa versione di .NET Framework.

4. Nell'elenco dei modelli di progetto, scegliere **progetto SharePoint 2010**.

5. Nel **Name** casella, immettere **SharePointProjectTestBDC**e quindi scegliere il **OK** pulsante.

6. Nella personalizzazione guidata SharePoint, immettere l'URL del sito che si desidera utilizzare per il debug, scegliere **Distribuisci come soluzione farm**, quindi scegliere il **fine** pulsante.

7. Aprire il menu di scelta rapida per il progetto SharePointProjectTestBDC, scegliere **Add**, quindi scegliere **nuovo elemento**.

8. Nel **NewItem aggiungere - SharePointProjectTestBDC** finestra di dialogo casella, espandere il nodo lingua installata la **SharePoint** nodo.

9. Scegliere il **2010** nodo, quindi scegliere il **Business Data Connectivity Model (solo soluzione Farm)** modello.

10. Nel **Name** casella, immettere **TestBDCModel**e quindi scegliere il **Aggiungi** pulsante.

11. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostati nella `Initialize` metodo del file di codice ProjectItemExtension.

12. Nell'istanza interrotta di Visual Studio, scegliere il **F5** importanti o sulla barra dei menu, scegliere **Debug** > **continua** per continuare il debug del progetto.

13. Nell'istanza sperimentale di Visual Studio, scegliere il **F5** chiave o nella barra dei menu, scegliere **Debug** > **Avvia debug** per compilare, distribuire ed eseguire il **TestBDCModel** progetto.

     Il browser viene visualizzata la pagina predefinita del sito di SharePoint che viene specificato per il debug.

14. Verificare che il **Elenca** sezione nell'area avvio veloce ancora non contiene un elenco che si basa sul modello di integrazione applicativa dei dati predefinito nel progetto. È prima di tutto necessario creare un elenco di dati esterni, usando l'interfaccia utente di SharePoint o tramite l'estensione di elemento di progetto.

15. Chiudere il Web browser.

16. Nell'istanza di Visual Studio con il progetto aperto TestBDCModel, aprire il menu di scelta rapida per il **TestBDCModel** nodo nel **Esplora soluzioni**, quindi scegliere **generare dati esterni Elenco**.

17. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostati nella `GenerateExternalDataLists_Execute` (metodo). Scegliere il **F5** chiave o nella barra dei menu, scegliere **Debug** > **continua** per continuare il debug del progetto.

18. L'istanza sperimentale di Visual Studio aggiunge un'istanza di elenco denominato **Entity1DataList** per il TestBDCModel progetto e l'istanza genera anche una funzionalità denominata **funzionalità2** per un elenco istanza.

19. Scegliere il **F5** chiave o nella barra dei menu, scegliere **Debug** > **Avvia debug** per compilare, distribuire ed eseguire il progetto TestBDCModel.

     Il browser viene visualizzata la pagina predefinita del sito di SharePoint che viene usato per eseguire il debug.

20. Nel **sono elencati** sezione nell'area avvio veloce, scegliere il **Entity1DataList** elenco.

21. Verificare che l'elenco contiene le colonne sono denominate Identifier1 e messaggio, oltre a un unico elemento che ha un valore Identifier1 pari a 0 e un valore del messaggio di Hello World.

     Il **Business Data Connectivity Model** progetto modello genera il modello di integrazione applicativa dei dati predefinito che fornisce tutti i dati.

22. Chiudere il Web browser.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Al termine del test dell'estensione dell'elemento di progetto, rimuovere il modello di integrazione applicativa dei dati e un elenco esterno dal sito di SharePoint e rimuovere l'estensione dell'elemento di progetto da Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Per rimuovere l'elenco di dati esterni al sito di SharePoint

1. Nell'area avvio veloce del sito di SharePoint, scegliere il **Entity1DataList** elenco.

2. Nella barra multifunzione nel sito di SharePoint, scegliere il **elenco** scheda.

3. Nel **elenco** nella scheda il **impostazioni** gruppo, scegliere **impostazioni elenco**.

4. Sotto **autorizzazioni e gestione**, scegliere **eliminare questo elenco**, quindi scegliere **OK** per confermare che si desidera inviare l'elenco nel Cestino.

5. Chiudere il Web browser.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Per rimuovere il modello di integrazione applicativa dei dati dal sito di SharePoint

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **compilare** > **Retract**.

     Visual Studio rimuove il modello di integrazione applicativa dei dati dal sito di SharePoint.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Per rimuovere l'estensione di elemento di progetto da Visual Studio

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **degli strumenti** > **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni, scegliere **generatore di elenco di dati esterni**, quindi scegliere il **Disinstalla** pulsante.

3. Nella finestra di dialogo visualizzata, scegliere **Sì** per confermare che si desidera disinstallare l'estensione.

4. Scegli **Riavvia ora** per completare la disinstallazione.

5. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza in cui la soluzione GenerateExternalDataLists è aperta).

## <a name="see-also"></a>Vedere anche
- [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)
