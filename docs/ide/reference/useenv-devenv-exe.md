---
title: -UseEnv (devenv.exe)
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37326bbe44eed15a562f0d28c01eac02973a2487
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789258"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Avvia Visual Studio e carica alcune variabili di ambiente per la compilazione.

> [!NOTE]
> Questa opzione viene installata con il carico di lavoro **Sviluppo di applicazioni desktop con C++**.

## <a name="syntax"></a>Sintassi

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argomenti

- *SolutionName*

  Percorso completo e nome del file di soluzione.

- *ProjectName*

  Percorso completo e nome del file di progetto.

## <a name="remarks"></a>Osservazioni

Questa opzione influisce sull'IDE di Visual Studio nelle proprietà del progetto per **Directory di VC++**. Se si specifica l'opzione `/UseEnv`, il nodo **Directory di VC++** mostra i valori per le variabili di ambiente PATH, INCLUDE, LIBPATH e LIB. (Indica anche i valori per **Directory di origine** e **Escludi directory**.) In caso contrario, il nodo sostituisce le variabili di ambiente con cinque valori di directory: **Directory file eseguibili**, **Directory di inclusione**, **Directory riferimenti**, **Directory librerie** e **Directory libreria WinRT**.

> [!TIP]
> Per accedere alle proprietà del progetto, fare clic con il pulsante destro del mouse su un progetto C++ e scegliere **Proprietà**. Nella finestra di dialogo **Pagine delle proprietà** selezionare **Proprietà di configurazione** e quindi **Directory di VC++**.

Quando viene specificato un nome di progetto con questa opzione, lo strumento visualizza le variabili di ambiente per tutti i progetti nella soluzione padre del progetto.

## <a name="example"></a>Esempio

L'esempio seguente avvia Visual Studio e carica le variabili di ambiente nella pagina delle proprietà della soluzione `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Pagina delle proprietà Directory di VC++ (Windows)](/cpp/ide/vcpp-directories-property-page)
