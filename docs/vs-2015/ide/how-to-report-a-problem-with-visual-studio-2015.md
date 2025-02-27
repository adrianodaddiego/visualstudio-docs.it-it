---
title: Come segnalare un problema con Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 24ecb76e-b7ad-432d-88ab-d9849963465d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d8cedd5ab26539d5ebe32aee8df272691dd0a779
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083649"
---
# <a name="how-to-report-a-problem-with-visual-studio-2015"></a>Come segnalare un problema con Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [Come segnalare un problema in Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

Se si verifica un problema con Visual Studio 2015, è opportuno segnalarlo a Microsoft in modo che possa diagnosticarlo e risolverlo.  Con lo strumento **Segnala un problema** è possibile raccogliere informazioni dettagliate sul problema e inviarle a Microsoft in pochi clic.

Microsoft rispetta la privacy degli utenti. Per informazioni sul trattamento dei dati inviati a Microsoft, vedere l'[Informativa sulla privacy Microsoft per aziende e sviluppatori](https://www.visualstudio.com/dn948229).

## <a name="open-the-report-a-problem-tool"></a>Aprire lo strumento Segnala un problema

Fare clic sull'icona di feedback utente accanto ad **Avvio veloce** nella barra del titolo oppure fare clic su **Guida > Commenti e suggerimenti > Segnala un problema**.

![Voce di menu Segnala un problema](../ide/media/report-a-problem-menu-item.png "Voce di menu Segnala un problema")

## <a name="describe-the-problem"></a>Descrivere il problema

### <a name="describe_the_problem"></a>

1. Inserire un titolo descrittivo per il problema in modo da consentirne l'invio al team di Visual Studio dedicato.

2. Fornire eventuali dettagli aggiuntivi e, se possibile, la procedura per riprodurre il problema.

3. Scegliere un'area collegata al problema nell'elenco a discesa. Se non si è certi, scegliere l'opzione più probabile.

   ![Finestra di dialogo Segnala un problema](../ide/media/report-a-problem-dialog.png "Finestra di dialogo Segnala un problema")

## <a name="provide-a-screenshot-optional"></a>Aggiungere uno screenshot (facoltativo)

Scegliere **Includi uno screenshot** per inviare la schermata corrente a Microsoft. Lo strumento consente di ritagliare l'immagine per visualizzare solo la parte della schermata che illustra il problema. È possibile collegare ulteriori screenshot o altri file facendo clic sul pulsante **Allega file aggiuntivi** .

## <a name="provide-a-trace-and-heap-dump-optional"></a>Fornire una traccia e un dump di heap (facoltativo)

### <a name="provide_a_trace_and_heap_dump"></a>

1. I file di traccia e di dump di heap sono utili per diagnosticare i problemi.   Siamo grati agli utenti che usano lo strumento Segnala un problema per registrare la procedura che consente di riprodurre il problema e inviare i dati a Microsoft.

2. Fare clic sulla freccia di espansione accanto a **Registrare le azioni per riprodurre il problema**. Se il problema causa il blocco o l'arresto anomalo di Visual Studio, aprire un'altra istanza di Visual Studio e selezionarla nella visualizzazione elenco.

3. Fare clic su **Avvia registrazione** e completare i passaggi per riprodurre il problema. Al termine, fare clic sul pulsante **Arresta registrazione** nella finestra mobile.

4. Attendere alcuni minuti mentre Visual Studio raccoglie e comprime le informazioni registrate. Quando il processo di raccolta è completato, la finestra di dialogo avrà un aspetto simile al seguente:

     ![Registrare un file di traccia](../ide/media/record-a-trace-file.png "Registrare un file di traccia")

## <a name="describe-the-workaround-if-there-is-one"></a>Descrivere la soluzione alternativa, se presente

Se è stata trovata una soluzione alternativa, descriverla nella casella di modifica fornita a tale scopo. In questo modo, Microsoft sarà in grado di fornire agli utenti non solo una diagnosi del problema, ma anche una possibile soluzione.

## <a name="submit-the-report"></a>Inviare il report

Fare clic sul pulsante Invia per inviare il report, insieme a eventuali immagini e ai file di traccia o di dump. Se il pulsante **Invia** è disattivato, verificare di aver specificato un titolo e una descrizione.

## <a name="see-also"></a>Vedere anche

- [Talk to Us](../ide/talk-to-us.md) (Comunicazioni con Microsoft)
