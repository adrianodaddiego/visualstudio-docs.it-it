---
title: 'Errore: Debug non è&#39;t possibili perché nel sistema è attivato un Debugger del Kernel | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- kernel debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63666302bcbf9f8f44c6121b583f0cf7b259f3ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850940"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Errore: Debug non è&#39;t possibili perché nel sistema è attivato un Debugger del Kernel
Quando si esegue il debug del codice gestito, è possibile che venga visualizzato il seguente messaggio di errore:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Questo messaggio viene visualizzato quando si tenta di eseguire il debug di codice gestito:

- in un sistema [!INCLUDE[win7](../debugger/includes/win7_md.md)] o [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] avviato in modalità debug.

- l'applicazione utilizzare CLR versione CLR 2.0, 3.0 o 3.5.

## <a name="solution"></a>Soluzione

#### <a name="to-fix-this-problem"></a>Per risolvere il problema

- Aggiornare l'applicazione per utilizzare CLR versione 4.0 o 4.5

   -oppure-

- Disabilitare il debug del kernel ed eseguire il debug in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   -oppure-

- Eseguire il debug con il debugger del kernel anziché [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   -oppure-

- Nel debugger del kernel disabilitare le eccezioni in modalità utente.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Per disabilitare il debug del kernel nella sessione corrente

- Al prompt dei comandi, digitare:

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Per disabilitare il debug del kernel per tutte le sessioni (Windows Vista e Windows 7)

1. Al prompt dei comandi, digitare:

    ```cmd
    bcdedit /debug off
    ```

2. Riavviare il computer.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Per disabilitare il debug del kernel per tutte le sessioni (altri sistemi operativi Windows)

1. Individuare boot.ini nell'unità di sistema, in genere C:\\. Il file boot.ini potrebbe essere nascosto e di sola lettura. Per visualizzarlo, è pertanto necessario utilizzare il seguente comando:

    ```cmd
    dir /ASH
    ```

2. Aprire boot.ini utilizzando Blocco note e rimuovere le seguenti opzioni:

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Riavviare il computer.

#### <a name="to-debug-with-the-kernel-debugger"></a>Per eseguire il debug con il debugger del kernel

1. Se il debugger del kernel è collegato, verrà visualizzato un messaggio che chiede se si desidera continuare a eseguire il debug. Scegliere il pulsante per continuare.

2. È possibile che venga generata un'eccezione `User break exception(Int 3).`. In questo caso, digitare il seguente comando del debugger del kernel per continuare a eseguire il debug:

     `gn`

## <a name="see-also"></a>Vedere anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug di codice gestito](../debugger/debugging-managed-code.md)
