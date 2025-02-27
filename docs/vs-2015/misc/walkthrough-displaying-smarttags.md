---
title: 'Procedura dettagliata: Visualizzazione degli smart tag | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: jillfra
ms.openlocfilehash: 116f76324a2150413c0ae6d08bc99e114efcc50e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436508"
---
# <a name="walkthrough-displaying-smarttags"></a>Procedura dettagliata: Visualizzazione degli smart tag
Gli smart tag sono deprecati e sono stati sostituiti dai menu Lampadina. Vedere [Procedura dettagliata: Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Gli smart tag sono tag sul testo che si espandono per visualizzare un set di azioni. Ad esempio, in un progetto di Visual Basic o Visual C# viene visualizzata una linea rossa sotto una parola quando si rinomina un identificatore, come un nome di variabile. Quando si sposta il puntatore del mouse sulla sottolineatura, viene visualizzato un pulsante accanto al puntatore. Se si fa clic sul pulsante, viene visualizzata un'azione consigliata, ad esempio la ridenominazione di **IsRead in IsReady**. Se si fa clic sull'azione, tutti i riferimenti a **IsRead** nel progetto vengono rinominati in **IsReady**.  
  
 Anche se gli smart tag fanno parte dell'implementazione di IntelliSense nell'editor, è possibile implementare smart tag creando sottoclassi di <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> e quindi implementando le interfacce <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> e <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.  
  
> [!NOTE]
> Altri tipi di tag possono essere implementati in modo simile.  
  
 Procedura dettagliata illustra come creare uno smart tag che viene visualizzato sulla parola corrente e ha due azioni consigliate: **Converti in maiuscolo** e **Convert in lettere minuscole**.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1. Creare un progetto di classificatore editor. Assegnare alla soluzione il nome `SmartTagTest`.  
  
2. Aprire il file source.extension.vsixmanifest nell'Editor manifest VSIX.  
  
3. Verificare che la sezione **Asset** contenga un tipo `Microsoft.VisualStudio.MefComponent` , che **Origine** sia impostato su `A project in current solution`e che **Progetto** sia impostato su SmartTagTest.dll.  
  
4. Salvare e chiudere il file source.extension.vsixmanifest.  
  
5. Aggiungere il riferimento seguente al progetto e impostare **CopyLocal** su `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6. Eliminare i file di classe esistenti.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Implementazione di un tagger per gli smart tag  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Per implementare un tagger per gli smart tag  
  
1. Aggiungere un file di classe e assegnargli il nome `TestSmartTag`.  
  
2. Aggiungere le importazioni seguenti:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3. Aggiungere una classe denominata `TestSmartTag` che eredita da <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4. Aggiungere un costruttore per la classe che chiama il costruttore base con <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> impostato su <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, che fa sì che venga visualizzata una linea blu sotto il primo carattere di una parola. Se si usa <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, verrà visualizzata una riga rossa sotto l'ultimo carattere della parola.  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5. Aggiungere una classe denominata `TestSmartTagger` che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> con tipo `TestSmartTag` e che implementa <xref:System.IDisposable>.  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6. Aggiungere i campi privati seguenti alla classe del tagger.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7. Aggiungere un costruttore che imposta i campi privati e sottoscrive l'evento <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> in modo da creare il tag per la parola corrente. Questo metodo chiama anche un metodo privato `GetSmartTagActions` , che viene descritto più avanti.  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Aggiungere un metodo `GetSmartTagActions` per configurare le azioni smart tag. Le azioni stesse verranno implementate in passaggi successivi.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Dichiarare l'evento `SmartTagsChanged` .  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Implementare il gestore eventi `OnLayoutChanged` per generare l'evento `TagsChanged`, che provoca la chiamata di <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Implementare il metodo <xref:System.IDisposable.Dispose%2A> in modo che annulli la sottoscrizione dell'evento <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Implementazione del provider di tagger per gli smart tag  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Per implementare il provider di tagger per gli smart tag  
  
1. Aggiungere una classe denominata `TestSmartTagTaggerProvider` che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Esportarla con <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> impostato su Before="default" e <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> impostato su <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2. Importare <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> come proprietà.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3. Implementare il metodo <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Implementazione di azioni smart tag  
  
#### <a name="to-implement-smart-tag-actions"></a>Per implementare azioni smart tag  
  
1. Creare due classi, denominate `UpperCaseSmartTagAction` e `LowerCaseSmartTagAction`. Entrambe le classi implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Le due classi sono simili, con l'unica eccezione che una chiama <xref:System.String.ToUpper%2A> e l'altra chiama <xref:System.String.ToLower%2A>. Anche se i passaggi seguenti descrivono solo la classe dell'azione per le maiuscole, è necessario implementarle entrambe. Usare i passaggi per l'implementazione dell'azione per le maiuscole come criterio per l'implementazione dell'azione per le minuscole.  
  
2. Dichiarare un set di campi privati.  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Aggiungere un costruttore che imposta i campi.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Implementare le proprietà nel modo indicato di seguito.  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> sostituendo il testo nell'intervallo con l'equivalente in maiuscole.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione SmartTagTest ed eseguirla nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Per compilare e testare la soluzione SmartTagTest  
  
1. Compilare la soluzione.  
  
2. Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3. Creare un file di testo e digitare alcune parole.  
  
     Dovrebbe essere visualizzata una linea blu sotto la prima lettera della prima parola del testo.  
  
4. Spostare il puntatore del mouse sulla linea blu.  
  
     Accanto al puntatore dovrebbe essere visualizzato un pulsante.  
  
5. Quando si fa clic sul pulsante, dovrebbero essere visualizzate due azioni consigliate: **Converti in maiuscolo** e **Convert in lettere minuscole**. Se si fa clic sulla prima azione, tutto il testo nella parola corrente verrà convertito in maiuscole. Se si fa clic sulla seconda azione, tutto il testo nella parola corrente verrà convertito in minuscole.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: collegamento di un tipo di contenuto a un'estensione](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)