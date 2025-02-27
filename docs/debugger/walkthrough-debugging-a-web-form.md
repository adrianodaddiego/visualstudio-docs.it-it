---
title: Eseguire il debug di un modulo Web | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f884206ecafebbe26bfdadfaa7e95f3dbd0f389f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901632"
---
# <a name="walkthrough-debugging-a-web-form"></a>Procedura dettagliata: Debug di un Web Form
Nei passaggi di questa procedura dettagliata viene illustrato come eseguire il debug di un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], noto anche come Web Form. Viene spiegato come avviare e arrestare l'esecuzione, impostare punti di interruzione ed esaminare le variabili nella finestra **Espressioni di controllo**.

> [!NOTE]
> Per completare la procedura dettagliata, è necessario disporre di privilegi di amministratore per il computer server. Per impostazione predefinita, il processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], aspnet_wp.exe o w3wp.exe viene eseguito come processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Per eseguire il debug di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], è necessario disporre dei privilegi di amministratore per il computer in cui [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] viene eseguito. Per altre informazioni, vedere [System Requirements](../debugger/aspnet-debugging-system-requirements.md).

Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="to-create-the-web-form"></a>Per creare il Web Form

1. Se una soluzione è già aperta, chiuderla.

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Sito Web**.

    Verrà visualizzata la finestra di dialogo **Nuovo sito Web**.

3. Nel riquadro **Modelli** selezionare **Sito Web ASP.NET**.

4. Nel **ubicazione** riga, fare clic su **HTTP** dall'elenco e nella casella di testo, digitare **http://localhost/WebSite**.

5. Nell'elenco **Linguaggio** fare clic su **Visual C#** oppure su **Visual Basic**.

6. Fare clic su **OK**.

    In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene creato un nuovo progetto e viene visualizzato il codice sorgente HTML predefinito. Viene anche creata una nuova directory virtuale denominata **WebSite** in **Sito Web predefinito di IIS**.

7. Fare clic sulla scheda **Progettazione** sul margine inferiore.

8. Scegliere la scheda **Casella degli strumenti** sul margine sinistro o selezionarla dal menu **Visualizza**.

    Verrà aperta la **Casella degli strumenti** .

9. Nella **Casella degli strumenti** fare clic sul controllo **Button** e aggiungerlo nell'area di progettazione principale Default.aspx.

10. Nella **Casella degli strumenti** fare clic sul controllo **Textbox** e trascinarlo nell'area di progettazione principale Default.aspx.

11. Fare doppio clic sul controllo Button trascinato.

     Ciò consente di visualizzare la tabella codici: Default.aspx.cs per C# o default per [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Il cursore dovrebbe trovarsi in corrispondenza della funzione `Button1_Click`.

12. Nella funzione `Button1_Click` aggiungere il codice seguente:

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. Scegliere **Compila soluzione** dal menu **Compila**.

     Il progetto dovrebbe essere compilato senza errori.

     A questo punto sarà possibile avviare il debug.

## <a name="to-debug-the-web-form"></a>Per eseguire il debug del Web Form

1. Nella finestra Default.aspx.cs o Default.aspx.vb fare clic sul margine sinistro della stessa riga del testo aggiunto:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    Verrà visualizzato un punto di colore rosso e il testo sulla riga verrà evidenziato in rosso. Il punto di colore rosso rappresenta un punto di interruzione. Quando verrà raggiunto questo punto nel codice, l'esecuzione dell'applicazione nel debugger verrà interrotta. Sarà quindi possibile visualizzare lo stato dell'applicazione ed eseguirne il debug. Per altre informazioni, vedere [Punti di interruzione](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

2. Scegliere **Avvia debug** dal menu **Debug**.

3. Viene visualizzata la finestra di dialogo **Debug non attivato**. Selezionare l'opzione **Modifica file Web.config per abilitare il debug**, quindi fare clic su **OK**.

    Verrà avviato Internet Explorer e verrà visualizzata la pagina appena progettata.

4. In Internet Explorer fare clic sul pulsante.

    In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà visualizzata la riga in cui si imposta il punto di interruzione sulla tabella codici Default.aspx.cs o Default.aspx.vb. Tale riga dovrebbe essere evidenziata in giallo. A questo punto è possibile visualizzare le variabili dell'applicazione e controllarne l'esecuzione. L'esecuzione dell'applicazione verrà interrotta e sarà necessario eseguire un comando.

5. Scegliere **Finestre** dal menu **Debug**, quindi **Espressioni di controllo** e infine **Espressione di controllo 1**.

6. Nella finestra **Espressioni di controllo** digitare **TextBox1.Text**.

    Nella finestra **Espressioni di controllo** verrà visualizzato il valore della variabile `TextBox1.Text`:

   '""'

7. Scegliere **Esegui istruzione/routine** dal menu **Debug**.

    Il valore di `TextBox1.Text` viene modificato nella finestra **Espressioni di controllo**:

   `"Button was clicked!"`

8. Scegliere **Continua** dal menu **Debug**.

9. In Internet Explorer fare di nuovo clic sul pulsante.

     L'esecuzione verrà nuovamente interrotta in corrispondenza del punto di interruzione.

10. Nella finestra Default.aspx.cs o Default.aspx.vb fare clic sul punto di colore rosso sul margine sinistro.

     Il punto di interruzione verrà rimosso.

11. Scegliere **Termina debug** dal menu **Debug**.

## <a name="to-attach-to-the-web-form-for-debugging"></a>Per connettere il debugger al Web Form

1. È possibile connettere il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a un processo in esecuzione. Per ottimizzare l'efficacia del debug, compilare il file eseguibile come versione di debug con i file dei simboli con estensione pdb.

2. Nella finestra Default.aspx.cs o Default.aspx.vb fare clic sul margine sinistro per impostare nuovamente un punto di interruzione in corrispondenza della riga aggiunta:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. Nel menu **Debug** fare clic su **Avvia senza eseguire debug**.

    Verrà eseguito il Web Form in Internet Explorer, ma il debugger non verrà connesso.

4. Connettersi al processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Per altre informazioni, vedere [debug di applicazioni Web distribuite](../debugger/debugging-deployed-web-applications.md).

5. In Internet Explorer fare clic sul pulsante nel form.

    In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è necessario raggiungere il punto di interruzione in Default.aspx.cs, Default.aspx.vb o Default.aspx.

6. Dopo il completamento del debug, scegliere **Termina debug** dal menu **Debug**.

## <a name="see-also"></a>Vedere anche

- [Eseguire il debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)