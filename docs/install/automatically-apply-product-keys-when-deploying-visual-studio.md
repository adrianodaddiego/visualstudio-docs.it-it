---
title: Applicare automaticamente codici Product Key
description: Informazioni sulla procedura di applicazione dei codici Product Key a livello di programmazione durante la distribuzione di Visual Studio.
ms.date: 04/10/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f1cdc3d8516271cd397c1d22118ca21a92f78cd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974215"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio

È possibile applicare il codice Product Key a livello di programmazione come parte dello script utilizzato per automatizzare la distribuzione di Visual Studio. È possibile impostare i codici Product Key su un dispositivo a livello di programmazione durante l'installazione di Visual Studio o al termine dell'installazione.

## <a name="apply-the-license-after-installation"></a>Applicare la licenza dopo l'installazione

::: moniker range="vs-2017"

È possibile attivare una versione installata di Visual Studio con un codice Product Key tramite l'utilità `StorePID.exe` nei computer di destinazione in modalità invisibile all'utente. `StorePID.exe` è un programma di utilità che viene installato con Visual Studio 2017 nel percorso predefinito seguente: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

È possibile attivare una versione installata di Visual Studio con un codice Product Key tramite l'utilità `StorePID.exe` nei computer di destinazione in modalità invisibile all'utente. `StorePID.exe` è un programma di utilità che viene installato con Visual Studio 2019 nel percorso predefinito seguente: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 Eseguire `StorePID.exe` con privilegi elevati, usando un agente System Center o un prompt dei comandi con privilegi elevati. Continuare quindi con il codice Product Key (con i trattini) e il codice Microsoft Product Code (MPC).

>[!IMPORTANT]
> Assicurarsi di includere i trattini nel codice Product Key.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

In questo esempio è riportata una riga di comando per l'applicazione della licenza di Visual Studio 2017 Enterprise, con codice MPC 08860 e codice Product Key `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, presupponendone l'installazione in un percorso predefinito:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

In questo esempio è riportata una riga di comando per l'applicazione della licenza di Visual Studio 2019 Enterprise, con codice MPC 09260 e codice Product Key `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, presupponendone l'installazione nel percorso predefinito:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 La tabella seguente riporta i codici MPC per ogni edizione di Visual Studio:

| Edizione di Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Edizione di Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

Se `StorePID.exe` applica correttamente il codice Product Key, restituisce un `%ERRORLEVEL%` pari a 0. Se si verificano errori, verrà restituito uno dei codici seguenti, a seconda della condizione di errore:

| Error                     | Codice |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](../install/install-visual-studio.md)
* [Creare un'installazione offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
