---
title: Tempo di preparazione del passaggio per un modello di carico passaggio per i test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f3353b6c46520dde1134c7ccff835b215b2d0ef8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821091"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Procedura: Specificare la proprietà relativa al tempo di preparazione del passaggio per un modello di carico passaggio

Dopo avere creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test. Per altre informazioni, vedere [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Per un elenco completo delle proprietà degli scenari di test di carico e le relative descrizioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

La proprietà **Tempo di preparazione passaggio** viene impostata nella finestra **Proprietà**. Le proprietà degli scenari dei test di carico vengono modificate nell'**Editor test di carico**.

La proprietà **Tempo di preparazione passaggio** viene usata solo con un modello di carico passaggio. Per altre informazioni, vedere [Modificare i modelli di carico per modellare le attività utente virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Un modello di carico per passaggio viene utilizzato per aumentare il carico sul server o sui server durante l'esecuzione dei test di carico, in modo da visualizzare la variazione delle prestazioni man mano che il carico utente aumenta. Per verificare, ad esempio, le prestazioni del server o dei server mentre il carico utente aumenta a 2000 utenti, è possibile eseguire un test di carico di 10 ore utilizzando un modello di carico per passaggio con le proprietà seguenti:

- Numero utenti iniziale: 100

- Numero massimo utenti: 2000

- Intervallo passaggi (secondi): 1800

- Tempo di preparazione passaggio (secondi): 20

- Numero utenti per passaggio: 100

Queste impostazioni attivano l'esecuzione del test di carico per 30 minuti (1800 secondi) a carichi utente di 100, 200, 300, fino a 2000 utenti.

> [!NOTE]
> La proprietà **Tempo di preparazione passaggio** è l'unica di queste proprietà che non può essere scelta nella **Creazione guidata test di carico**.

La proprietà **Tempo di preparazione passaggio** consente l'aumento graduale, anziché immediato, da un passaggio al successivo (ad esempio da 100 a 200 utenti). In questo esempio il carico utente aumenterebbe da 100 a 200 utenti in un intervallo di 20 secondi, ovvero un aumento di 5 utenti al secondo.

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Per modificare la proprietà Tempo di preparazione passaggio per un modello di carico per passaggio

1. Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzata la struttura ad albero del test di carico.

2. Nella cartella **Scenari** dell'albero del test di carico aprire il nodo dello scenario per il quale si vuole specificare il tempo di preparazione del passaggio.

3. Selezionare il nodo **Modello di carico passaggio**.

    > [!NOTE]
    > Il modello di carico per lo scenario deve essere un modello di carico per passaggio. In caso contrario, nel modello di carico verrà visualizzato il tipo di modello di carico attualmente associato allo scenario. Per altre informazioni, vedere [Modificare i modelli di carico per modellare le attività utente virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario vengono visualizzate nella finestra **Proprietà**.

5. Impostare il valore per la proprietà **Tempo di preparazione passaggio** immettendo un numero per i secondi richiesti in ogni passaggio per aggiungere gradualmente gli utenti specificati tramite la proprietà **Numero utenti per passaggio**.

6. Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore di **Tempo di preparazione passaggio**.

## <a name="see-also"></a>Vedere anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
- [Modificare i modelli di carico per definire le attività di utenti virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md)