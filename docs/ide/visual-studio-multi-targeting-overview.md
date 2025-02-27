---
title: Definire .NET Framework come destinazione
ms.date: 02/06/2018
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 451464cd2576c1dd70c7b8235cead327b2f05ca2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582112"
---
# <a name="visual-studio-multi-targeting-overview"></a>Panoramica del multitargeting di Visual Studio

In Visual Studio è possibile specificare la versione o il profilo di .NET Framework per cui si vuole sviluppare il progetto. Per un'applicazione da eseguire in un altro computer, la versione di .NET Framework per cui viene sviluppata l'applicazione deve essere compatibile con quella installata nel computer.

È anche possibile creare una soluzione contenente progetti destinati a versioni diverse di .NET Framework. Sviluppare per .NET Framework consente di garantire che l'applicazione usi solo le funzionalità disponibili nella versione specificata di .NET Framework.

> [!TIP]
> È anche possibile definire la destinazione delle applicazioni per piattaforme diverse. Per altre informazioni, vedere [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Funzionalità per la definizione di .NET Framework come destinazione

La definizione della destinazione del framework include le seguenti funzionalità:

- Quando si apre un progetto destinato a una versione precedente di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], con Visual Studio è possibile aggiornare automaticamente la versione di destinazione o lasciarla invariata.

- Quando si crea un progetto, è possibile specificare la versione di .NET Framework che si vuole usare come destinazione.

- È possibile modificare la versione di .NET Framework a cui è destinato un progetto esistente.

- È possibile definire la destinazione di una versione diversa di .NET Framework in ognuno dei diversi progetti di una stessa soluzione.

- Quando si modifica la versione di .NET Framework a cui è destinato un progetto, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] effettua tutte le modifiche necessarie ai riferimenti e ai file di configurazione.

Quando si lavora su un progetto destinato a una versione precedente del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio modifica in modo dinamico l'ambiente di sviluppo, come indicato di seguito:

- Vengono filtrati gli elementi delle finestre di dialogo **Aggiungi nuovo elemento**, **Aggiungi nuovo riferimento** e **Aggiungi riferimento al servizio** per omettere scelte che non sono disponibili nella versione di destinazione.

- Vengono filtrati i controlli personalizzati nella **Casella degli strumenti** per rimuovere quelli che non sono disponibili nella versione di destinazione e per visualizzare solo i controlli più aggiornati quando sono disponibili più controlli.

- Vengono applicati i filtri **IntelliSense** per omettere funzionalità del linguaggio che non sono disponibili nella versione di destinazione.

- Vengono filtrate le proprietà nella finestra **Proprietà** per omettere quelle che non sono disponibili nella versione di destinazione.

- Vengono filtrate le opzioni di menu per omettere opzioni che non sono disponibili nella versione di destinazione.

- Per le compilazioni, vengono usate la versione e le opzioni del compilatore appropriate per la versione di destinazione.

> [!NOTE]
> La definizione della destinazione del framework non garantisce che l'applicazione verrà eseguita correttamente. È necessario testare l'applicazione per assicurarsi che venga eseguita la versione di destinazione. Non è possibile usare come destinazione versioni di framework precedenti a .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Selezione una versione di .NET Framework di destinazione

Quando si crea un progetto, selezionare la versione di .NET Framework di destinazione dopo la selezione di un modello di progetto. L'elenco di framework disponibili include le versioni di framework installate applicabili al tipo di modello selezionato. Per i tipi di modello che non richiedono .NET Framework, ad esempio i modelli di .NET Core, l'elenco a discesa **Framework** è nascosto.

::: moniker range="vs-2017"

![Elenco a discesa dei framework in VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Elenco a discesa dei framework in VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

In un progetto esistente è possibile modificare la versione di .NET Framework di destinazione nella finestra di dialogo delle proprietà del progetto. Per altre informazioni, vedere [Procedura: Scegliere una versione di .NET Framework di destinazione](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Risolvere i riferimenti ad assembly di sistema e utente

Per impostare come destinazione una versione di .NET Framework, è necessario prima installare i riferimenti dell'assembly appropriato. È possibile scaricare Developer Pack per versioni diverse di .NET Framework dalla pagina [.NET downloads](https://www.microsoft.com/net/download/windows) (Download di .NET).

La finestra di dialogo **Aggiungi riferimento** disabilita gli assembly di sistema non pertinenti alla versione di destinazione di .NET Framework, in modo che non possano essere aggiunti a un progetto inavvertitamente. Gli assembly di sistema sono file con estensione *dll* inclusi in una versione di .NET Framework. I riferimenti che appartengono a una versione del framework successiva alla versione di destinazione non verranno risolti e i controlli che dipendono da un riferimento di questo tipo non possono essere aggiunti. Se si vuole abilitare questo riferimento, reimpostare la destinazione di .NET Framework del progetto su una che include il riferimento.  Per altre informazioni, vedere [Procedura: Scegliere una versione di .NET Framework di destinazione](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Per altre informazioni sui riferimenti ad assembly, vedere [Risoluzione di assembly in fase di progettazione](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Abilitare LINQ

Quando si usa .NET Framework 3.5 o versioni successive, vengono aggiunti automaticamente un riferimento a **System.Core** e un'importazione a livello di progetto per <xref:System.Linq> (solo in Visual Basic). Per usare le funzionalità LINQ, è necessario attivare anche `Option Infer` (solo in Visual Basic). Se si passa a una versione precedente di .NET Framework, il riferimento e l'importazione vengono rimossi automaticamente. Per altre informazioni, vedere [Uso di LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Vedere anche

- [Multitargeting (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)