---
title: Analisi dei test codificati dell'interfaccia utente utilizzando i log dei test codificati dell'interfaccia utente
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a5ce4f298039d6d86f8c4855d1f139b6be1d1175
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822730"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analisi dei test codificati dell'interfaccia utente usando i log dei test codificati dell'interfaccia utente

I log dei test codificati dell'interfaccia utente filtrano e registrano informazioni importanti sulle esecuzioni dei test codificati dell'interfaccia utente. I log sono presentati in un formato che consente il debug rapido degli errori.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Passaggio 1: Abilitare la registrazione

A seconda dello scenario in uso, abilitare la registrazione usando uno dei metodi seguenti:

- La destinazione è .NET Framework versione 4 senza file *App.config* nel progetto di test:

   1. Aprire il file *QTAgent32_40.exe.config*. Per impostazione predefinita, questo file si trova in *%Programmi(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

   2. Modificare il valore per EqtTraceLevel e impostarlo sul livello di log desiderato.

   3. Salvare il file.

- La destinazione è .NET Framework versione 4.5 senza file *App.config* nel progetto di test:

   1. Aprire il file *QTAgent32.exe.config*. Per impostazione predefinita, questo file si trova in *%Programmi(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

   2. Modificare il valore di EqtTraceLevel e impostarlo sul livello di log desiderato.

   3. Salvare il file.

- Il file *App.config* è presente nel progetto di test:

    - Aprire il file *App.config* nel progetto e aggiungere il codice seguente nel nodo di configurazione:

      ```xml
      <system.diagnostics>
        <switches>
          <add name="EqtTraceLevel" value="4" />
        </switches>
      </system.diagnostics>`
      ```

- La registrazione viene abilitata dal codice di test stesso:

   <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Passaggio 2: Eseguire il test codificato dell'interfaccia utente e visualizzare il log

Quando si esegue un test codificato dell'interfaccia utente dopo avere apportato le modifiche appropriate al file *QTAgent32.exe.config*, viene visualizzato un collegamento di output nei risultati di **Esplora test**. I file di log vengono generati sia per i test con esito negativo, sia per quelli con esito positivo quando il livello di traccia è impostato su "dettagliato".

1. Dal menu **Test** scegliere **Finestre** e selezionare **Esplora test**.

2. Scegliere **Compila soluzione** dal menu **Compila**.

3. In **Esplora test** selezionare il test codificato dell'interfaccia utente che si vuole eseguire, aprire il relativo menu di scelta rapida e quindi scegliere **Esegui test selezionati**.

     I test automatizzati vengono eseguiti e segnalano se sono stati superati o se hanno avuto esito negativo.

    > [!TIP]
    > Per visualizzare **Esplora test**, scegliere **Test** > **Finestre** e selezionare **Esplora test**.

4. Scegliere il collegamento **Output** nei risultati di **Esplora test**.

     ![Collegamento di output in Esplora test](../test/media/cuit_htmlactionlog1.png)

     Viene visualizzato l'output del test in cui è incluso un collegamento al log delle azioni.

     ![Risultati e collegamenti di output del test codificato dell'interfaccia utente](../test/media/cuit_htmlactionlog2.png)

5. Scegliere il collegamento *UITestActionLog.html*.

     Il log verrà visualizzato nel browser Web.

     ![File di log del test codificato dell'interfaccia utente](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Vedere anche

- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Procedura: Eseguire test da Microsoft Visual Studio](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)