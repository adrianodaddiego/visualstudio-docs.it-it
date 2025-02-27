---
title: Tempo di risposta delle pagine in un test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed1bd922b390d5b6e90c68b08683e1b9bdb46f32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821248"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Procedura: Visualizzare il tempo di risposta delle pagine Web in un test di carico usando l'Analizzatore test di carico

Il tempo richiesto per il caricamento di ogni pagina web è definito *tempo di risposta*. Quando si crea un test web, è possibile impostare un tempo di risposta obiettivo per ogni richiesta di pagina web nel test web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Se il test web viene eseguito sotto stress in un test di carico, sarà possibile analizzare le seguenti informazioni per ogni pagina:

- Il tempo di risposta medio per la pagina.

- La percentuale di iterazioni test che soddisfano il tempo di risposta obiettivo per la pagina.

- È possibile analizzare i tempi di risposta della pagina Web usando la visualizzazione Tabelle o la visualizzazione Grafici nell'**Analizzatore test di carico**:

- Analisi dei tempi di risposta della pagina web nella visualizzazione Tabelle

- Analisi dei tempi di risposta della pagina web nella visualizzazione Grafici

## <a name="view-response-time-data-in-a-table"></a>Visualizzare i dati sul tempo di risposta in una tabella

1. Nell'**Analizzatore test di carico** scegliere **Tabelle** nella barra degli strumenti per assicurarsi che venga visualizzata la griglia della tabella.

2. Nella casella di riepilogo **Tabella** selezionare **Pagine**.

3. I dati per ogni pagina vengono visualizzati nella griglia. Solitamente vengono visualizzate le colonne seguenti.

   |Intestazione colonna|Description|
   |-|-|
   |**Page**|Nome della pagina Web.|
   |**Scenario**|Nome dello scenario. Importante se il test Web include più di uno scenario.|
   |**Test**|Nome del test delle prestazioni web. Importante se il test di carico include più di un test delle prestazioni web.|
   |**Network**|Tipo di rete.<br /><br /> Per impostazione predefinita, questi dati non vengono raccolti. Per raccoglierli, nell'**Editor test di carico** sotto il nodo **Impostazioni di esecuzione** selezionare il nodo dell'impostazione di esecuzione da modificare. Nella finestra **Proprietà**, per la proprietà **Intervallo archiviazione dettagli**, selezionare **AllIndividualDetails**.|
   |**Totale**|Numero complessivo di richieste effettuate per la pagina Web. Corrisponde al totale di tutte le iterazioni nel test di carico.|
   |**Media**|Tempo di risposta medio della pagina.<br /><br /> Per impostazione predefinita, questi dati non vengono raccolti. Per raccoglierli, nell'**Editor test di carico** sotto il nodo **Impostazioni di esecuzione** selezionare il nodo dell'impostazione di esecuzione da modificare. Nella finestra **Proprietà**, per la proprietà **Intervallo archiviazione dettagli**, selezionare **AllIndividualDetails**.|
   |**Min**|Tempo di risposta minimo della pagina.<br /><br /> Per impostazione predefinita, questi dati non vengono raccolti. Per raccoglierli, nell'**Editor test di carico** sotto il nodo **Impostazioni di esecuzione** selezionare il nodo dell'impostazione di esecuzione da modificare. Nella finestra **Proprietà**, per la proprietà **Intervallo archiviazione dettagli**, selezionare **AllIndividualDetails**.|
   |**Mediana**|Tempo di risposta mediano della pagina.<br /><br /> Per impostazione predefinita, questi dati non vengono raccolti. Per raccoglierli, nell'**Editor test di carico** sotto il nodo **Impostazioni di esecuzione** selezionare il nodo dell'impostazione di esecuzione da modificare. Nella finestra **Proprietà**, per la proprietà **Intervallo archiviazione dettagli**, selezionare **AllIndividualDetails**.|
   |**90%**|Novantesimo percentile per il tempo di risposta. Ciò indica che il 90% delle pagine ha risposto più velocemente di questo numero, mentre il 10% più lentamente.<br /><br /> Per impostazione predefinita, questi dati non vengono raccolti. Per raccoglierli, nell'**Editor test di carico** sotto il nodo **Impostazioni di esecuzione** selezionare il nodo dell'impostazione di esecuzione da modificare. Nella finestra **Proprietà**, per la proprietà **Intervallo archiviazione dettagli**, selezionare **AllIndividualDetails**.|
   |**95%**|Novantacinquesimo percentile per il tempo di risposta. Ciò indica che il 95% delle pagine ha risposto più velocemente di questo numero, mentre il 5% più lentamente.|
   |**99%**|Novantanovesimo percentile per il tempo di risposta. Ciò indica che il 99% delle pagine ha risposto più velocemente di questo numero, mentre il 1% più lentamente.<br /><br /> Per impostazione predefinita, questi dati non vengono raccolti. Per raccoglierli, nell'**Editor test di carico** sotto il nodo **Impostazioni di esecuzione** selezionare il nodo dell'impostazione di esecuzione da modificare. Nella finestra **Proprietà**, per la proprietà **Intervallo archiviazione dettagli**, selezionare **AllIndividualDetails**.|
   |**Max**|Tempo di risposta massimo della pagina.<br /><br /> Per impostazione predefinita, questi dati non vengono raccolti. Per raccoglierli, nell'**Editor test di carico** sotto il nodo **Impostazioni di esecuzione** selezionare il nodo dell'impostazione di esecuzione da modificare. Nella finestra **Proprietà**, per la proprietà **Intervallo archiviazione dettagli**, selezionare **AllIndividualDetails**.|
   |**Deviazione standard**|Per impostazione predefinita, i dati della deviazione standard non vengono raccolti. Per raccoglierli, nell'**Editor test di carico** sotto il nodo **Impostazioni di esecuzione** selezionare il nodo dell'impostazione di esecuzione da modificare. Nella finestra **Proprietà**, per la proprietà **Intervallo archiviazione dettagli**, selezionare **AllIndividualDetails**.|
   |**Tempo di risposta pagina**|Tempo di risposta medio per tutte le richieste effettuate per la pagina Web.|
   |**Obiettivo**|Tempo pagina obiettivo. Si tratta di un valore costante per la pagina. **Nota:**  il tempo pagina obiettivo viene visualizzato solo quando nel test delle prestazioni Web è stato definito l'obiettivo per la richiesta.|
   |**% corrispondenza a obiettivo**|Percentuale delle richieste effettuate per la pagina web che soddisfano il tempo di risposta obiettivo.|

   Per altre informazioni, vedere [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Visualizzare i dati sul tempo di risposta in un grafico

È anche possibile visualizzare i dati sul tempo di risposta in un grafico, per rilevare le modifiche nel corso del tempo durante il test di carico. Questa opzione è particolarmente utile se il modello di carico aumenta durante l'esecuzione del test, ad esempio se si utilizza il modello di carico per passaggio. Per altre informazioni, vedere [Modificare i modelli di carico per modellare le attività utente virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Per visualizzare i dati sul tempo di risposta in un grafico:

1. Nell'**Analizzatore test di carico** scegliere **Grafici** nella barra degli strumenti per assicurarsi che venga visualizzato il grafico.

2. Nella finestra **Contatori** espandere il nodo dello scenario desiderato, ad esempio `Scenario1`.

3. Espandere il nodo del test delle prestazioni web desiderato.

4. Espandere il nodo **Pagine**.

5. Espandere il nodo della pagina desiderato.

6. Fare clic con il pulsante destro del mouse su **% di pagine corrispondenti a obiettivo**, quindi scegliere **Mostra contatore su grafico**.

    I dati vengono aggiunti al grafico.

7. (Facoltativo) Ripetere il passaggio precedente per **Avg. Page Time**, **Page Response Time Goal** e **Total Pages**.

   > [!NOTE]
   > Il valore **Page Response Time Goal** è costante.

   Per altre informazioni, vedere [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)