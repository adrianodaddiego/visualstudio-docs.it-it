---
title: Analizzare i risultati dei test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, accessing
- Load Test Viewer
- load tests, accessing
- load tests, analyzing
- load tests, results
- Load Test Viewer, viewing
ms.assetid: b0a3e694-2894-479b-b270-7e61e9fafacd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e4b14be6df351a6975fb8a7cf6fa506a5d4f6041
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979432"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Procedura: Accedere ai risultati dei test di carico per l'analisi

Quando si esegue un test di carico dall'Editor test di carico, i risultati del test vengono aperti automaticamente e il test di carico in esecuzione viene visualizzato nell'**Analizzatore test di carico**. Quando si esegue un test di carico dalla riga di comando, è necessario accedere manualmente ai risultati del test di carico.

I risultati relativi al test di carico completato contengono gli esempi di contatori delle prestazioni e le informazioni sugli errori raccolti periodicamente dai computer sottoposti a test. Nel corso dell'esecuzione di un test di carico può essere raccolto un numero elevato di esempi di contatori delle prestazioni. La quantità di dati sulle prestazioni raccolti durante un test di carico dipende dalla durata dell'esecuzione del test, dall'intervallo di campionamento, dal numero di computer sottoposti a test, dal numero di contatori raccolti, dagli agenti di raccolta dati configurati e dai livelli di registrazione. Per un test di carico di grandi dimensioni, la quantità di dati sulle prestazioni raccolti può facilmente raggiungere diversi gigabyte. Per altre informazioni, vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>Per accedere ai risultati di un test di carico

1. Da un progetto di test di carico e prestazioni web aprire un test di carico.

2. Nella barra degli strumenti dell'Editor test di carico scegliere il pulsante **Apri e gestisci risultati**.

     Viene visualizzata la finestra di dialogo **Apri e gestisci risultati**.

3. In **Immettere un nome del controller per trovare i risultati del test di carico** selezionare un controller. Selezionare **\<locale> - Senza controller** per accedere ai risultati archiviati localmente.

4. In **Mostra risultati per test di carico seguente** selezionare il test di carico di cui si vuole visualizzare i risultati. Selezionare **\<Mostra risultati per tutti i test>** per visualizzare tutti i risultati per tutti i test.

     Se disponibili, i risultati del test di carico sono visualizzati nell'elenco **Risultati test di carico**. L'elenco contiene le colonne **Ora**, **Durata**, **Utente**, **Risultato**, **Test** e **Descrizione**. In **Test** è indicato il nome del test, mentre in **Descrizione** è riportata la descrizione facoltativa aggiunta prima dell'esecuzione del test.

    > [!NOTE]
    > I risultati vengono visualizzati insieme ai più recenti all'inizio dell'elenco.

5. Nell'elenco **Risultati test di carico** selezionare i risultati da analizzare e scegliere **Apri**.

6. Verrà visualizzato l'**Analizzatore test di carico**. I risultati del test di carico selezionati appaiono nella visualizzazione Riepilogo. Per altre informazioni, vedere [Panoramica del riepilogo dei risultati dei test di carico](../test/load-test-results-summary-overview.md).

     È possibile gestire altri aspetti dei risultati del test di carico nella finestra di dialogo **Apri e gestisci risultati**, incluse le operazioni di importazione, esportazione e rimozione dei risultati del test di carico. Per altre informazioni, vedere [Gestione dei risultati dei test di carico nel repository dei risultati del test di carico](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)