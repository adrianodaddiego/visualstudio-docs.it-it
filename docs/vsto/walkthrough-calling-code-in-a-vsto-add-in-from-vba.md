---
title: 'Procedura dettagliata: Chiamare il codice in un componente aggiuntivo VSTO da VBA'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cc268136e898b7ef348b2910e080323347eb5716
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438630"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Procedura dettagliata: Chiamare il codice in un componente aggiuntivo VSTO da VBA
  Questa procedura dettagliata descrive come esporre un oggetto in un componente aggiuntivo VSTO ad altre soluzioni Microsoft Office, tra cui Visual Basic, Applications Edition (VBA) e i componenti aggiuntivi VSTO COM.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Benché la procedura dettagliata usi in particolare Excel, i concetti illustrati sono applicabili a qualsiasi modello di progetto di componente aggiuntivo VSTO disponibile in Visual Studio.

 Questa procedura dettagliata illustra le attività seguenti:

- Definizione di una classe che può essere esposta ad altre soluzioni Office.

- Esposizione della classe ad altre soluzioni Office.

- Chiamata di un metodo della classe dal codice VBA.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>Creare il progetto di componente aggiuntivo VSTO
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Excel.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di componente aggiuntivo VSTO per Excel con il nome **ExcelImportData**, usando il modello di progetto di componente aggiuntivo VSTO per Excel. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file di codice **ThisAddIn.cs** o **ThisAddIn.vb** e aggiunge il progetto **ExcelImportData** a **Esplora soluzioni**.

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definire una classe che può essere esposta ad altre soluzioni Office
 Lo scopo di questa procedura dettagliata è chiamare il metodo `ImportData` di una classe denominata `AddInUtilities` nel componente aggiuntivo VSTO dal codice VBA. Il metodo consente di scrivere una stringa nella cella A1 del foglio di lavoro attuale.

 Per esporre la classe `AddInUtilities` ad altre soluzioni Office, è necessario rendere pubblica e visibile la classe a COM. Inoltre, è necessario esporre l'interfaccia [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) nella classe. Il codice riportato nella procedura illustra uno dei modi in cui è possibile soddisfare tali requisiti. Per altre informazioni, vedere [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definire una classe che può essere esposta ad altre soluzioni Office

1. Dal menu **Progetto** , fare clic su **Aggiungi classe**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** , modificare il nome della nuova classe in **AddInUtilities**, quindi selezionare **Aggiungi**.

     Il file **AddInUtilities.cs** o **AddInUtilities.vb** viene aperto nell'editor del codice.

3. Aggiungere le seguenti istruzioni nella parte iniziale del file.

     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]

4. Sostituire la classe `AddInUtilities` con il codice seguente.

     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]

     Questo codice rende visibile la classe `AddInUtilities` a COM e aggiunge il metodo `ImportData` alla classe. Al fine di esporre l'interfaccia [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) , la classe `AddInUtilities` dispone anche dell'attributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> e implementa un'interfaccia che può essere visualizzata da COM.

## <a name="expose-the-class-to-other-office-solutions"></a>Esporre la classe ad altre soluzioni Office
 Per esporre la `AddInUtilities` classe alle altre soluzioni Office, eseguire l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> nella classe `ThisAddIn` . Nell'override, restituire un'istanza della classe `AddInUtilities` .

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Per esporre la classe AddInUtilities ad altre soluzioni Office

1. In **Esplora soluzioni**, espandere **Excel**.

2. Fare clic con il pulsante destro del mouse su **ThisAddIn.cs** o **ThisAddIn.vb**, quindi selezionare **Visualizza codice**.

3. Aggiungere il codice seguente alla classe `ThisAddIn` .

     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]

4. Scegliere **Compila soluzione** dal menu **Compila**.

     Verificare che la soluzione venga compilata senza errori.

## <a name="test-the-vsto-add-in"></a>Testare il componente aggiuntivo VSTO
 È possibile chiamare la classe `AddInUtilities` da numerose tipologie di soluzioni Office. In questa procedura dettagliata, il codice VBA verrà usato in una cartella di lavoro di Excel. Per altre informazioni sugli altri tipi di soluzioni Office, è anche possibile usare, vedere [chiamare il codice nei componenti aggiuntivi VSTO da altre soluzioni Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-test-your-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO

1. Premere **F5** per eseguire il progetto.

2. In Excel, salvare la cartella di lavoro attiva come cartella di lavoro con attivazione macro di Excel (*.xlsm). Salvarla in un percorso a propria scelta, ad esempio, il desktop.

3. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Nel gruppo **Codice** , selezionare **Visual Basic**.

     Viene aperto Microsoft Visual Basic Editor.

5. Nella finestra, **Progetto** , fare doppio clic su **ThisWorkbook**.

     Viene aperto il file di codice relativo all'oggetto `ThisWorkbook` .

6. Aggiungere il codice VBA seguente al file di codice. Questo codice ottiene innanzitutto un oggetto COMAddIn che rappresenta il **ExcelImportData** il componente aggiuntivo VSTO. Quindi, il codice Usa la proprietà dell'oggetto dell'oggetto COMAddIn per chiamare il `ImportData` (metodo).

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. Premere **F5**.

8. Verificare che un nuovo foglio **Dati importati** sia stato aggiunto alla cartella di lavoro. Inoltre, verificare che nella cella A1 sia presente la stringa **Dati personali**.

9. Uscire da Excel.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni sulla programmazione di componenti aggiuntivi VSTO, vedere questi argomenti:

- Usare la classe `ThisAddIn` per automatizzare l'applicazione host ed eseguire altre attività nei progetti di componente aggiuntivo VSTO. Per altre informazioni, vedere [programma VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Creare un riquadro attività personalizzato in un componente aggiuntivo VSTO. Per altre informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md) e [come: Aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

- Personalizzare la barra multifunzione in un componente aggiuntivo VSTO. Per altre informazioni, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md) e [come: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).

## <a name="see-also"></a>Vedere anche
- [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)
- [Chiamare il codice nei componenti aggiuntivi VSTO da altre soluzioni Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Sviluppare soluzioni Office](../vsto/developing-office-solutions.md)
- [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
