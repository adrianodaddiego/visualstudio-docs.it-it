---
title: Selezionare i percorsi di installazione
description: Informazioni su come ridurre lo spazio occupato dall'installazione di Visual Studio nell'unità di sistema indicando un percorso in unità diverse per Download Cache, componenti condivisi, SDK e strumenti. Ad esempio, spostare alcuni file dall'unità C all'unità D.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 651295d94a8125e26caa96b71ab438c62841ac10
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974354"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Selezionare i percorsi di installazione in Visual Studio

::: moniker range="vs-2019"

è possibile ridurre lo spazio occupato dall'installazione di Visual Studio nell'unità di sistema cambiando il percorso di alcuni file. In particolare è possibile usare un percorso diverso per la Download Cache, i componenti condivisi, i SDK e file degli strumenti.

::: moniker-end

::: moniker range="vs-2017"

**Novità della versione 15.7**: è possibile ridurre lo spazio occupato dall'installazione di Visual Studio nell'unità di sistema cambiando il percorso di alcuni file. In particolare è possibile usare un percorso diverso per la Download Cache, i componenti condivisi, i SDK e file degli strumenti.

::: moniker-end

   > [!NOTE]
   > Esistono alcuni strumenti e SDK con regole diverse riguardo al percorso di installazione. Questi strumenti e SDK vengono installati nell'unità di sistema anche se si sceglie un altro percorso.

Pronti per iniziare? Ecco come fare.

::: moniker range="vs-2017"

1. Quando si installa Visual Studio scegliere la scheda **Percorsi di installazione**.

   ![Visual Studio 2017 - Selezionare il percorso di installazione](media/vs-installation-locations.png "Selezionare il percorso di installazione.")

1. Nella sezione **IDE di Visual Studio** accettare il valore predefinito. Viene installato il prodotto principale e vengono inclusi file specifici per questa versione di Visual Studio.

   ![Sezione IDE di Visual Studio della scheda Percorsi di installazione](media/vs-installation-locations-ide.png "Accettare l'impostazione predefinita per la sezione IDE di Visual Studio della scheda Percorsi di installazione.")

   > [!TIP]
   > Se l'unità di sistema è un'unità SSD è consigliabile accettare il percorso predefinito nell'unità di sistema. Motivo: quando si sviluppa con Visual Studio, si eseguono operazioni di lettura e scrittura in numerosi file, aumentando così le attività di input/output del disco. È opportuno scegliere l'unità più veloce per gestire il carico.

1. Nella sezione **Download Cache** decidere se si vuole mantenere la Download Cache e quindi scegliere dove archiviare i file corrispondenti.

     ![Sezione Download Cache della scheda Percorsi di installazione](media/vs-installation-locations-cache.png "Scegliere se mantenere la Download Cache dopo l'installazione, quindi specificare l'unità in cui archiviare i file.")

    1. Selezionare o deselezionare **Mantieni la Download Cache dopo l'installazione**.

       Se si decide di non mantenere la Download Cache, il percorso viene usato solo temporaneamente. Questa azione non ha effetto sui file di installazioni precedenti né li elimina.

    1. Specificare l'unità in cui verranno archiviati i file di installazione e i manifesti dalla Download Cache.

        Ad esempio, se si seleziona il carico di lavoro "Sviluppo di applicazioni desktop con C++", le dimensioni richieste temporaneamente sono 1,58 GB nell'unità di sistema, spazio che verrà liberato non appena viene completata l'installazione.

       > [!IMPORTANT]
       > Il percorso viene impostato con la prima installazione e non può essere modificato in un secondo tempo dall'interfaccia utente del programma di installazione. Invece per spostare la Download Cache è necessario [usare i parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md).

1. Nella sezione **Componenti condivisi, strumenti e SDK** specificare l'unità in cui si vogliono archiviare i file condivisi dalle installazioni side-by-side di Visual Studio. Anche i SDK e gli strumenti vengono archiviati in questa directory.

   ![Sezioni Componenti condivisi, Strumenti e SDK della scheda Percorsi di installazione](media/vs-installation-locations-shared.png "Specificare il percorso in cui archiviare i componenti condivisi, gli strumenti e i SDK.")

::: moniker-end

::: moniker range="vs-2019"

1. Quando si installa Visual Studio scegliere la scheda **Percorsi di installazione**.

   ![Visual Studio 2019 - Selezionare il percorso di installazione](media/vs-2019/vs-installer-installation-locations.png "Selezionare il percorso di installazione.")

1. Nella sezione **IDE di Visual Studio** accettare il valore predefinito. Viene installato il prodotto principale e vengono inclusi file specifici per questa versione di Visual Studio.

   > [!TIP]
   > Se l'unità di sistema è un'unità SSD è consigliabile accettare il percorso predefinito nell'unità di sistema. Motivo: quando si sviluppa con Visual Studio, si eseguono operazioni di lettura e scrittura in numerosi file, aumentando così le attività di input/output del disco. È opportuno scegliere l'unità più veloce per gestire il carico.

1. Nella sezione **Download Cache** decidere se si vuole mantenere la Download Cache e quindi scegliere dove archiviare i file corrispondenti.

    * Selezionare o deselezionare **Mantieni la Download Cache dopo l'installazione**.

       Se si decide di non mantenere la Download Cache, il percorso viene usato solo temporaneamente. Questa azione non ha effetto sui file di installazioni precedenti né li elimina.

    * Specificare l'unità in cui verranno archiviati i file di installazione e i manifesti dalla Download Cache.

        Ad esempio, se si seleziona il carico di lavoro "Sviluppo di applicazioni desktop con C++", le dimensioni richieste temporaneamente sono 1,58 GB nell'unità di sistema, spazio che verrà liberato non appena viene completata l'installazione.

       > [!IMPORTANT]
       > Il percorso viene impostato con la prima installazione e non può essere modificato in un secondo tempo dall'interfaccia utente del programma di installazione. Invece per spostare la Download Cache è necessario [usare i parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md).

1. Nella sezione **Componenti condivisi, strumenti e SDK** viene usata la stessa unità scelta nella sezione "Download cache". La directory \Microsoft\VisualStudio\Condiviso archivia i file condivisi dalle installazioni side-by-side di Visual Studio. Anche i SDK e gli strumenti vengono archiviati in questa directory.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Modificare Visual Studio](update-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
