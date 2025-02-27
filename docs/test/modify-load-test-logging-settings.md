---
title: Impostazioni di registrazione dei test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9751ce3b08a0ac963cccdf091ccb99001c6f2c9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62785773"
---
# <a name="modify-load-test-logging-settings"></a>Modificare le impostazioni di registrazione dei test di carico

I risultati relativi al test di carico completato contengono gli esempi di contatori delle prestazioni e le informazioni sugli errori raccolti in un log periodicamente dai computer sottoposti a test. Nel corso dell'esecuzione di un test di carico può essere raccolto un numero elevato di esempi di contatori delle prestazioni. La quantità di dati sulle prestazioni raccolti durante un test di carico dipende dalla durata dell'esecuzione del test, dall'intervallo di campionamento, dal numero di computer sottoposti a test e dal numero di contatori da raccogliere. Per un test di carico di grandi dimensioni, la quantità raccolta di dati relativi alle prestazioni può facilmente raggiungere diversi gigabyte; considerare pertanto di modificare la frequenza di salvataggio dei dati nel log. Vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Durante l'esecuzione del test di carico, il *test controller* effettua lo spooling di tutti i dati di esempio del test di carico raccolti in un log di database. Dopo il completamento del test, nel database vengono caricati dati aggiuntivi quali dettagli sugli errori e di intervallo.

|Attività|Argomenti correlati|
|-|-----------------------|
|**Salvare i log se un test di carico non riesce:** è possibile specificare se si vuole salvare il log di test quando un test di carico non riesce.|-   [Procedura: Specificare se i test non superati vengono salvati in log di test](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Impostare le dimensioni massime per il file di log:** è possibile modificare il file di configurazione XML associato al servizio del test controller per specificare le dimensioni massime da usare per il file di log.|Modificare `<add key="LogSizeLimitInMegs" value="20"/>` nel file di configurazione XML *QTCcontroller.exe.config*.|

## <a name="see-also"></a>Vedere anche

- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)