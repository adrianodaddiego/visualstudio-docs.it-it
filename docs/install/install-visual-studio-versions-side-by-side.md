---
title: Installare versioni di Visual Studio side-by-side
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 123f01b2e4545545a380f5a37adcdaf883bc9e91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974722"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Installare versioni di Visual Studio side-by-side

È possibile installare Visual Studio in un computer in cui è già installata una versione precedente o successiva di Visual Studio.

::: moniker range="vs-2017"

Prima di installare le versioni side-by-side, verificare le condizioni seguenti:

* Se si usa Visual Studio 2017 per aprire una soluzione creata in Visual Studio 2015, successivamente è possibile aprire e modificare nuovamente la soluzione nella versione precedente purché non siano state implementate funzionalità specifiche di Visual Studio 2017.

* Se si prova a usare Visual Studio 2017 per aprire una soluzione creata in Visual Studio 2015 o in una versione precedente, potrebbe essere necessario modificare i progetti e i file per renderli compatibili con Visual Studio 2017. Per altre informazioni vedere la pagina [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017).

::: moniker-end

::: moniker range=">= vs-2019"

Prima di installare le versioni side-by-side, verificare le condizioni seguenti:

* Se si usa Visual Studio 2019 per aprire una soluzione creata in Visual Studio 2017, successivamente è possibile aprire e modificare nuovamente la soluzione nella versione precedente purché non siano state implementate funzionalità specifiche di Visual Studio 2019.

* Se si prova a usare Visual Studio 2019 per aprire una soluzione creata in Visual Studio 2017 o in una versione precedente, potrebbe essere necessario modificare i progetti e i file per renderli compatibili con Visual Studio 2019. Per altre informazioni vedere la pagina [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

* Se si disinstalla una versione di Visual Studio da un computer in cui sono installate più versioni, le associazioni di file per Visual Studio verranno rimosse per tutte le versioni.

* Visual Studio non aggiorna automaticamente le estensioni, perché non tutte le estensioni sono compatibili. È necessario reinstallare le estensioni da [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkId=178891) o dall'autore del software.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versioni di .NET Framework e installazioni side-by-side

I progetti Visual Basic, Visual C# e Visual F# usano l'opzione **Framework di destinazione** in **Creazione progetti** per specificare la versione di .NET Framework che un progetto usa. Per un progetto C++ è possibile modificare manualmente il framework di destinazione modificando il file con estensione vcxproj. Per altre informazioni, vedere la pagina [Compatibilità tra le versioni in .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

Quando si crea un progetto, è possibile specificare a quale versione di .NET Framework è destinato il progetto nell'elenco **.NET Framework** della finestra di dialogo **Nuovo progetto** .

Per informazioni specifiche del linguaggio, vedere l'argomento corrispondente nella tabella seguente.

::: moniker range="vs-2017"

| Linguaggio | Argomento |
|--------------|-----------|
| Visual Basic | [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Pagina Applicazione, Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Sviluppare con F# in Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md?view=vs-2017)
* [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Compilazione di applicazioni isolate C/C++ e di assembly side-by-side](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Linguaggio | Argomento |
|--------------|-----------|
| Visual Basic | [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Pagina Applicazione, Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Sviluppare con F# in Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Compilazione di applicazioni isolate C/C++ e di assembly side-by-side](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end