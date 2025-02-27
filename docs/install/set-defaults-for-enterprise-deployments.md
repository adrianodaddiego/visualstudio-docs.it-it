---
title: Impostare i valori predefiniti per le distribuzioni aziendali
description: Informazioni sui criteri di dominio e altre operazioni di configurazione per la distribuzione aziendale di Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: be29a8eff4e36df04721e8f946b9b2b0ebae3145
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945014"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Impostare i valori predefiniti per le distribuzioni aziendali di Visual Studio

È possibile impostare i criteri del Registro di sistema che influiscono sulla distribuzione di Visual Studio. Questi criteri sono globali per il nuovo programma di installazione e incidono sugli aspetti seguenti:

- Dove vengono installati alcuni pacchetti condivisi con altre versioni o istanze
- Dove vengono memorizzati i pacchetti
- Se vengono memorizzati tutti i pacchetti

È possibile impostare alcuni di questi criteri usando le [opzioni della riga di comando](use-command-line-parameters-to-install-visual-studio.md), impostare i valori del Registro di sistema nel computer in uso o persino distribuirli tramite Criteri di gruppo all'interno dell'organizzazione.

## <a name="registry-keys"></a>Chiavi del Registro di sistema

Esistono diverse percorsi in cui è possibile impostare i valori predefiniti dell'organizzazione in modo da esercitarne il controllo tramite Criteri di gruppo o direttamente nel Registro di sistema. Visual Studio controlla in modo sequenziale se sono stati impostati criteri aziendali; non appena viene trovato un valore di criteri nell'ordine seguente, le chiavi rimanenti vengono ignorate.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (in sistemi operativi a 64 bit)

> [!IMPORTANT]
> Se non si imposta la chiave `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` e si imposta invece una delle altre chiavi, è necessario impostare entrambe le altre chiavi nei sistemi operativi a 64 bit. Questo problema verrà risolto in un aggiornamento futuro del prodotto.

Se non sono ancora impostati, alcuni valori del Registro di sistema vengono impostati automaticamente al primo utilizzo. In questo modo si garantisce che eventuali installazioni successive usino gli stessi valori, che vengono archiviati nella seconda chiave del Registro di sistema: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

È possibile impostare i valori del Registro di sistema seguenti:

| **Name** | **Type** | **Default** | **Descrizione** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Directory in cui vengono archiviati i manifesti di pacchetto e, facoltativamente, i payload. Per altre informazioni, vedere la pagina [Disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Consente di mantenere i payload dei pacchetti anche dopo l'installazione. È possibile modificare questo valore in qualsiasi momento. Disabilitando questi criteri vengono rimossi tutti i payload di pacchetti memorizzati nella cache per l'istanza da riparare o modificare. Per altre informazioni, vedere la pagina [Disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Directory in cui sono installati alcuni pacchetti condivisi tra più versioni di istanze di Visual Studio. È possibile modificare il valore in qualsiasi momento, ma questa operazione influirà solo sulle installazioni future. I prodotti già installati nel percorso precedente non devono essere spostati o potrebbero non funzionare correttamente. |

> [!IMPORTANT]
> Se si modificano i criteri del Registro di sistema `CachePath` dopo un'installazione, è necessario spostare la cache del pacchetto esistente nel nuovo percorso e verificare che sia protetto in modo che `SYSTEM` e `Administrators` abbiano il controllo completo e `Everyone` l'accesso in lettura.
> Se non si sposta o non si protegge la cache esistente, è possibile che si verifichino problemi con le installazioni future.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

- [Installare Visual Studio](install-visual-studio.md)
- [Disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md)
- [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
