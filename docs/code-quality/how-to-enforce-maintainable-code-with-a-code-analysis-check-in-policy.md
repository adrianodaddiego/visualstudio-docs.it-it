---
title: Usare un criterio di controllo dell'analisi codice
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0924d3c7b6f39e4ec026a77ee8e0418361e311ba
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260914"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedura: Imporre codice di facile manutenibilità con criteri di controllo dell'analisi codice

Gli sviluppatori possono usare lo strumento di metrica codice per misurare la complessità e della manutenibilità del codice, ma non è possibile richiamare la metrica del codice come parte di un criterio di controllo. Tuttavia, è possibile abilitare le regole di analisi del codice che consentono di verificare la conformità del codice con standard della metrica del codice e applicare le regole tramite i criteri di archiviazione. Per altre informazioni sulla metrica del codice, vedere [i valori delle metriche del codice](../code-quality/code-metrics-values.md).

È possibile abilitare la profondità dell'ereditarietà, accoppiamento di classe, indice di manutenibilità e le regole di complessità applicare il codice gestibile tramite criteri di controllo dell'analisi del codice. Tutti e quattro queste regole si trovano sotto la categoria "Regole di manutenibilità" nell'editor dei criteri analisi codice.

Gli amministratori di controllo della versione di Team Foundation possono aggiungere le regole di manutenibilità di analisi codice per i requisiti dei criteri di archiviazione. Questi check-in criteri richiedono agli sviluppatori di eseguire l'analisi del codice basato su queste modifiche alle regole prima dell'avvio di un'archiviazione.

## <a name="to-open-the-code-analysis-policy-editor"></a>Per aprire l'editor Criteri di analisi codice

1. Nelle **Team Explorer**, fare clic sul progetto, fare clic su **le impostazioni del progetto**, quindi fare clic su **controllo del codice sorgente**.

     Il **controllo del codice sorgente** verrà visualizzata la finestra di dialogo.

2. Nel **dei criteri di archiviazione** scheda e fare clic su **Add**.

     Il **aggiungere i criteri di archiviazione** verrà visualizzata la finestra di dialogo.

3. Nel **dei criteri di archiviazione** elenco, selezionare la **analisi del codice** casella di controllo e quindi fare clic su **OK**.

     Il **Editor dei criteri analisi codice** verrà visualizzata la finestra di dialogo.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Per abilitare le regole di manutenibilità analisi codice

1. Nel **Editor criteri di analisi di codice** nella finestra di dialogo **le impostazioni delle regole**, espandere il **regole di manutenibilità** nodo.

2. Selezionare le caselle di controllo per le regole seguenti:

   - Profondità dell'ereditarietà: **CA1501 AvoidExcessiveInheritance** -soglia: Più di 5 livelli di avviso

   - Complessità: **CA1502 AvoidExcessiveComplexity** -soglia: Avviso in più di 25

   - Indice di manutenibilità: **CA1505 AvoidUnmaintainableCode** -soglia: Avviso per meno di 20

   - Accoppiamento di classe: **CA1506 AvoidExcessiveClassCoupling** -soglia: Avviso più di 80 per una classe e più di 30 per un metodo

     Inoltre, se si desidera che una violazione delle regole per impedire una compilazione corretta, selezionare la **trattare avvisi come errori** casella di controllo accanto alla descrizione della regola.

3. Fare clic su **OK**. Il nuovo criterio si applica ora a archiviazioni future.

## <a name="see-also"></a>Vedere anche

- [Valori della metrica del codice](../code-quality/code-metrics-values.md)
- [Creazione e utilizzo di criteri di controllo dell'analisi del codice](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
