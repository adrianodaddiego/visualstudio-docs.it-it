---
title: 'Procedura: Importare i risultati del test di carico in un repository'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 16f6558373c111dbaf933184cf5ae23d00962b7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949966"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Procedura: Importare i risultati del test di carico in un repository

Quando si esegue un test di carico, le informazioni raccolte durante l'esecuzione vengono archiviate nel repository dei risultati del test di carico. Il repository dei risultati del test di carico contiene i dati del contatore delle prestazioni e le informazioni sugli errori. Per altre informazioni, vedere [Gestione dei risultati dei test di carico nel repository dei risultati del test di carico](../test/manage-load-test-results-in-the-load-test-results-repository.md).

È possibile gestire i risultati del test di carico dall'Editor test di carico usando la finestra di dialogo **Apri e gestisci risultati del test di carico**. È possibile aprire, importare, esportare e rimuovere i risultati test di carico.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Per importare i risultati in un repository

1. Da un progetto di test di carico e prestazioni web aprire un test di carico.

2. Scegliere **Apri e gestisci risultati** nella barra degli strumenti incorporata.

     Viene visualizzata la finestra di dialogo **Apri e gestisci risultati del test di carico**.

3. In **Immettere un nome del controller per trovare i risultati del test di carico** selezionare un controller. Selezionare **\<locale>** per accedere ai risultati archiviati localmente.

     Se disponibili, i risultati del test di carico sono visualizzati nell'elenco **Risultati test di carico**. L'elenco contiene le colonne **Ora**, **Durata**, **Utente**, **Risultato**, **Test** e **Descrizione**. In **Test** è indicato il nome del test, mentre in **Descrizione** è riportata la descrizione facoltativa aggiunta prima dell'esecuzione del test.

4. Scegliere **Importa**.

     Viene visualizzata la finestra di dialogo **Importa risultati test di carico**.

5. Nella casella **Nome file** digitare il nome di un file dei risultati del test archiviato e scegliere **Apri**.

     \- oppure -

     Individuare il file e scegliere **Apri**.

    > [!NOTE]
    > Un file dei risultati del test archiviato specificato in questo passaggio deve essere stato creato mediante un'operazione di esportazione.

     I risultati vengono importati e visualizzati nell'elenco **Risultati test di carico**.

## <a name="see-also"></a>Vedere anche

- [Gestire i risultati dei test di carico nel repository dei risultati del test di carico](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Procedura: Esportare i risultati del test di carico da un repository](../test/how-to-export-load-test-results-from-a-repository.md)