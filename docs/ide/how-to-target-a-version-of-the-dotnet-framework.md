---
title: Scegliere una versione di .NET Framework di destinazione
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8bdcade321c3660e89ab6b7cf6e0b79471b393
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548648"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Procedura: Scegliere una versione di .NET Framework di destinazione

Questo articolo descrive in che modo si specifica come destinazione una versione di .NET Framework quando si crea un progetto. Descrive inoltre come modificare la versione di destinazione in progetto Visual Basic, C# o F# esistente.

> [!IMPORTANT]
> Per informazioni su come modificare la versione di destinazione per progetti C++, vedere [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Scegliere una versione di destinazione durante la creazione di un progetto

Quando si crea un progetto, le versioni di .NET Framework disponibili dipendono dalle versioni installate e dal modello di progetto selezionato.

1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

1. Scegliere un modello per il tipo di progetto che si vuole creare. Immettere un nome per il progetto.

1. Nell'elenco a discesa **Framework** nella parte inferiore della finestra di dialogo scegliere la versione di .NET Framework a cui si vuole destinare il progetto.

   L'elenco dei framework mostra solo le versioni applicabili al modello scelto. Alcuni tipi di progetto, ad esempio .NET Core, non richiedono .NET Framework. In questi casi, l'elenco a discesa **Framework** è nascosto.

   ::: moniker range="vs-2017"

   ![Elenco a discesa Framework nella finestra di dialogo Nuovo progetto](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Selettore di Framework in Visual Studio 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Continuare con la [creazione del progetto](create-new-project.md).

## <a name="change-the-targeted-version"></a>Cambiare la versione di destinazione

È possibile cambiare la versione di destinazione di .NET Framework in un progetto Visual Basic, C# o F# seguendo questa procedura.

1. In **Esplora soluzioni** aprire il menu di scelta rapida del progetto che si vuole modificare e scegliere **Proprietà**.

    ![Proprietà Esplora soluzioni di Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. Nella colonna sinistra della finestra **Proprietà** scegliere la scheda **Applicazione**.

    ![Scheda Applicazione delle proprietà app in Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Dopo aver creato un'app UWP, non è possibile cambiare la versione di destinazione di Windows o di .NET Framework.

1. Nell'elenco **Framework di destinazione** selezionare la versione appropriata.

1. Nella finestra di dialogo di verifica visualizzata scegliere **Sì**.

    Il progetto verrà scaricato. Una volta caricato nuovamente, il progetto sarà destinato alla versione di .NET Framework appena scelta.

    > [!NOTE]
    > Se il codice contiene riferimenti a una versione di .NET Framework diversa rispetto a quella di destinazione, è possibile che vengano visualizzati dei messaggi di errore durante la compilazione o l'esecuzione del codice. Per risolvere questi errori è necessario modificare i riferimenti. Vedere [Risolvere i problemi relativi agli errori di impostazione di .NET Framework come destinazione](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Vedere anche

- [Panoramica del multitargeting di Visual Studio](../ide/visual-studio-multi-targeting-overview.md)
- [Risolvere i problemi relativi agli errori di impostazione di .NET Framework come destinazione](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Applicazione (pagina), Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)