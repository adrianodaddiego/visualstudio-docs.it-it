---
title: Tempi di interazione utente per i test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e19e1cb4f9b49c40923d96b177ceb4d6c31b746f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783343"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Modificare i tempi di interazione utente per simulare i ritardi di interazione umana con i siti Web in scenari di test di carico

Il tempo interazione utente consente di simulare il comportamento umano rispetto alle attese tra le interazioni con un sito Web. I tempi interazione utente intercorrono tra le richieste in un test Web e tra le interazioni test in uno scenario di test di carico. L'uso dei tempi interazione utente in un test di carico può essere utile per creare simulazioni di carico più accurate. È possibile scegliere se i tempi interazione utente devono essere usati o ignorati nei test di carico. Scegliere se usare i tempi interazione utente nei test di carico nell'**Editor test di carico**.

Il *profilo interazione utente* è un'impostazione che si applica a uno scenario in un test di carico. L'impostazione determina se i tempi interazione utente salvati nei singoli test Web vengono usati durante il test di carico. Se si vuole usare i tempi interazione utente in alcuni test Web ma non in altri, è necessario inserirli in scenari diversi. Per altre informazioni sugli scenari, vedere [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md).

Inizialmente, è necessario scegliere se usare i tempi di interazione utente nei test di carico quando si crea il test di carico con la **Creazione guidata test di carico**. Per altre informazioni, vedere [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md).

Le opzioni del profilo **interazione utente** sono descritte nell'elenco seguente:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Off**

I tempi interazione utente vengono ignorati. Usare questa impostazione quando si vuole generare il carico massimo sul server Web. Non usarla quando si tenta di creare interazioni utente più realistiche con un server Web.

**On**

I tempi interazione utente vengono usati esattamente così come sono stati registrati nel test Web. Simula più utenti che eseguono i test Web esattamente come sono stati registrati. Poiché un test di carico simula più utenti, usando gli stessi tempi interazione utente è possibile creare un modello di carico non naturale di utenti virtuali sincronizzati.

**Distribuzione normale**

Il tempo interazione utente viene usato, ma variato in una curva normale. Fornisce una simulazione più realistica di utenti virtuali variando lievemente il tempo interazione utente tra le richieste.

> [!NOTE]
> Per un elenco completo delle proprietà relative agli scenari di test di carico e delle relative descrizioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Modificare il profilo interazione utente

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Per modificare il profilo interazione utente in uno scenario di test di carico

1. Dal progetto di test di carico e prestazioni Web, aprire un test di carico.

2. Nell'**Editor test di carico** scegliere il nodo dello scenario in cui modificare il **profilo interazione utente**. Il **profilo interazione utente** verrà visualizzato nella finestra **Proprietà**. Premere **F4** per visualizzare la finestra **Proprietà**.

3. Modificare la proprietà **Profilo interazione utente** nella finestra **Proprietà**.

4. Dopo avere apportato le modifiche alle proprietà, scegliere **Salva** nel menu **File**. È quindi possibile eseguire il test di carico con il nuovo profilo interazione utente.

## <a name="see-also"></a>Vedere anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)