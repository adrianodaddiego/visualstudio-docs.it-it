---
title: 'Procedura: Debug an ActiveX Control | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c76167468d9eb6fbe93c3bef0c4ae8c15634fc5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894430"
---
# <a name="how-to-debug-an-activex-control"></a>Procedura: Eseguire il debug di un controllo ActiveX

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Per effettuare il debug di un controllo ActiveX, è necessario specificare un contenitore (eseguibile) in cui elaborare il controllo stesso.

## <a name="to-specify-a-container-for-the-debug-session"></a>Per specificare un contenitore per la sessione di debug

1. Selezionare il progetto in Esplora soluzioni.

2. Dal **View** menu, scegliere **pagine delle proprietà**.

3. Nella finestra di dialogo **Pagine delle proprietà del progetto** aprire la cartella **Proprietà di configurazione** e selezionare **Debug**.

4. Nella categoria **Debug** individuare la proprietà **Command**.

5. Specificare il percorso del contenitore. Ad esempio, C:\Programmi\Internet Explorer\IEXPLORE.EXE.

6. Se si specifica Internet Explorer come contenitore ed è attivata la modalità Active Desktop, digitare `/new` nella casella **Argomenti del comando**.

7. Fare clic su **OK**.

     Se non si specifica alcun contenitore nella finestra di dialogo **Project Property Pages** (Pagine delle proprietà del progetto), sarà possibile specificarlo all'avvio del debug. Quando si seleziona un comando per avviare il debug, viene visualizzata la finestra di dialogo [Eseguibile per la sessione di debug](../debugger/executable-for-debugging-session-dialog-box.md). Nella finestra di dialogo specificare il nome percorso del contenitore.

## <a name="see-also"></a>Vedere anche

- [Controlli ActiveX](/cpp/mfc/activex-controls)
- [Test di proprietà ed eventi con Test Container](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)
- [Debug in Visual Studio](../debugger/index.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)