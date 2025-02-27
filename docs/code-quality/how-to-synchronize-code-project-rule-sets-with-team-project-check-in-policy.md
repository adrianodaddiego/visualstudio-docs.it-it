---
title: Regola di sincronizzazione progetto imposta con criteri di archiviazione
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80d13afe27eab28c88d2513b6c8be986ab1c960a
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260855"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Procedura: Sincronizzare i set di regole di progetto di codice con un criterio di controllo aggiuntivo progetto DevOps di Azure

Specificando un set di regole che contiene almeno le regole specificate nel set di regole per i criteri di controllo è sincronizzare le impostazioni di analisi codice per progetti di codice per i criteri di controllo per il progetto DevOps di Azure. Il responsabile per gli sviluppatori può dare è il nome e la posizione del set di regole per i criteri di controllo. Assicurarsi che l'analisi del codice per il progetto usi il set di regole corretto, è possibile usare una delle opzioni seguenti:

- Se i criteri di controllo viene utilizzato uno dei set di regole predefinite Microsoft, aprire la finestra di dialogo proprietà per il progetto di codice, visualizzare la pagina di analisi del codice e selezionare la regola impostata nella pagina analisi del codice delle impostazioni di progetto di codice. Il set di regole standard installate automaticamente con Visual Studio di Microsoft è impostata su sola lettura e non deve essere modificato. Se non vengono modificati i set di regole, le regole nel set di regole locali e criteri di corrispondenza è garantite.

- Se i criteri di controllo Usa un set di regole personalizzate, eseguire un'operazione get sul file di set di regole nel controllo della versione per creare una copia locale. Quindi specificare tale posizione locale nelle impostazioni di analisi del codice per il progetto di codice. Le regole sono necessariamente una corrispondenza se il set di regole per i criteri di controllo sono aggiornata.

     Se si esegue il mapping di percorso del controllo della versione in una cartella locale nella stessa relazione per la radice del progetto DevOps di Azure come progetto di codice, il percorso della regola è impostato con un percorso relativo. Il percorso relativo garantisce che l'impostazione di progetto di codice per l'analisi del codice può essere spostata in altri computer.

- Personalizzare una copia del set di regole per i criteri di controllo per un progetto di codice. Assicurarsi che il nuovo set di regole contiene tutte le regole nei criteri di archiviazione e qualsiasi altra regola che si desidera includere. È necessario assicurarsi che il set di regole include tutte le regole nel set di regole per i criteri di controllo.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Per specificare una regola standard Microsoft set

1. Nelle **Esplora soluzioni**, fare clic sul progetto codice e quindi fare clic su **proprietà**.

2. Fare clic su **analisi del codice**.

3. Nel **eseguire questo set di regole** elenco, fare clic su set di regole dei criteri di archiviazione.

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Per specificare un set di regole di criteri di archiviazione personalizzati

1. Se necessario, eseguire un'operazione get sul file di set di regole che specifica i criteri di controllo.

2. Nelle **Esplora soluzioni**, fare clic sul progetto codice e quindi fare clic su **proprietà**.

3. Fare clic su **analisi del codice**.

4. Nel **eseguire questo set di regole** fare clic su  **\<Sfoglia... >** .

5. Nel **aperto** finestra di dialogo, specificare la regola dei criteri di archiviazione file del set.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Per creare una regola personalizzata impostata per un progetto di codice

1. Seguire una delle procedure riportate in precedenza in questo argomento per selezionare i criteri di controllo del progetto DevOps di Azure nella pagina analisi del codice della finestra di dialogo Impostazioni di progetto.

2. Fare clic su **Apri**.

3. Aggiungere o rimuovere le regole tramite le [editor set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md).

4. Salvare la regola modificata impostato su un file con estensione ruleset nel computer locale o in un percorso UNC.

5. Aprire la finestra di dialogo proprietà per il progetto di codice e visualizzare il **analisi del codice** pagina.

6. Nel **eseguire questo set di regole** fare clic su  **\<Sfoglia... >** .

7. Nel **aperto** finestra di dialogo, specificare il set di regole file.
