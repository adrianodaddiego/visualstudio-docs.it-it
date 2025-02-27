---
title: Guida dell'amministratore di Help Viewer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b00f89b60c7e884bfaf71e971722530b44a78b4e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445692"
---
# <a name="help-viewer-administrator-guide"></a>Guida dell'amministratore di Help Viewer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il visualizzatore della Guida consente di gestire le installazioni della Guida locale per gli ambienti di rete con o senza accesso a Internet. Il contenuto della Guida locale viene configurato per ogni singolo computer. Per impostazione predefinita, gli utenti devono disporre dei diritti di amministratore per aggiornare l'installazione della Guida locale.  
  
 Se l'ambiente di rete consente ai client di accedere a Internet, il visualizzatore della Guida consente di usare script della riga di comando per distribuire contenuto della Guida locale da Internet.  
  
 Se l'ambiente di rete non consente ai client di accedere a Internet, il visualizzatore della Guida può distribuire il contenuto della Guida locale dalla Intranet o da una condivisione di rete. È anche possibile disabilitare le opzioni della Guida dell'IDE di Visual Studio, ad esempio la Guida online/offline, l'installazione del contenuto al primo avvio dell'IDE, la specifica di un servizio per i contenuti Intranet e la gestione del contenuto, usando gli override delle chiavi del Registro di sistema.  
  
 La sintassi di base è la seguente:  
  
 \<*percorso*> \HlpCtntmgr.exe /operation \< *argomento*> /catalogname \< *nome*> /locale \< *impostazionilocali*> /sourceuri \< *percorso msha o URL*>  
  
 Per altre informazioni sulla sintassi della riga di comando di HlpCtntMgr.exe, vedere [Argomenti della riga di comando per Gestione contenuto della Guida](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Per altre informazioni sulla creazione del contenuto, sulla creazione di un endpoint servizio Intranet e tipi di attività simili, vedere Help Viewer SDK.  
  
## <a name="deploying-local-help-content-from-the-internet"></a>Distribuzione del contenuto della Guida locale da Internet  
 È possibile usare il servizio del pacchetto con il contenuto MSDN per distribuire il contenuto della Guida locale da Internet ai computer client. Usare la sintassi seguente:  
  
 \\<*percorso*>\v2.2\HlpCtntmgr.exe /operation \<*nome*> /catalogname \<*nome catalogo*> /locale \<*impostazioni locali*>  
  
 Per altre informazioni sulla sintassi della riga di comando di HlpCtntMgr.exe, vedere [Argomenti della riga di comando per Gestione contenuto della Guida](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Requisiti:  
  
- I computer client devono disporre di accesso a Internet.  
  
- Gli utenti devono disporre dei diritti di amministratore per aggiornare, aggiungere o rimuovere il contenuto della Guida locale dopo l'installazione.  
  
  Avvertenze:  
  
- L'origine predefinita per la Guida sarà ancora Online.  
  
  > [!TIP]
  > È possibile cambiare l'origine predefinita per la Guida modificando la chiave del Registro di sistema HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp. Per altre informazioni, vedere [Override di Gestione contenuto della Guida](../ide/help-content-manager-overrides.md).  
  
- Ai client verrà ancora richiesto di installare il contenuto della Guida di base al primo avvio di Visual Studio. È possibile disabilitare questa richiesta modificando la chiave del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection.  
  
### <a name="example"></a>Esempio  
 L'esempio seguente installa il contenuto in lingua inglese per Visual Studio in un computer client.  
  
##### <a name="to-install-english-content-from-the-internet"></a>Per installare il contenuto in lingua inglese da Internet  
  
1. Scegliere **Start** e quindi **Esegui**.  
  
2. Digitare quanto segue:  
  
     C:\Program Files (x86)\Microsoft Help Viewer\v2.2\hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale en-us  
  
3. Premere INVIO.  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Distribuzione del contenuto della Guida locale preinstallato nei computer client  
 È possibile installare un set di contenuti online in un computer e quindi copiarlo in altri computer.  
  
 Requisiti:  
  
- Il computer in cui si installa il set del contenuto deve avere accesso a Internet.  
  
- Gli utenti devono disporre dei diritti di amministratore per aggiornare, aggiungere o rimuovere il contenuto della Guida locale dopo l'installazione.  
  
  > [!TIP]
  > Se gli utenti non dispongono dei diritti di amministratore, si consiglia di disabilitare la scheda Gestisci contenuto nel visualizzatore della Guida. Per altre informazioni, vedere [Override di Gestione contenuto della Guida](../ide/help-content-manager-overrides.md).  
  
  Avvertenze:  
  
- Se gli utenti non dispongono dei diritti di amministratore, si consiglia di disabilitare la scheda Gestisci contenuto nel visualizzatore della Guida. Per altre informazioni, vedere [Override di Gestione contenuto della Guida](../ide/help-content-manager-overrides.md).  
  
- L'origine predefinita per la Guida sarà ancora Online.  
  
- Ai client verrà ancora richiesto di installare il contenuto della Guida di base al primo avvio di Visual Studio. Per altre informazioni, vedere [Override di Gestione contenuto della Guida](../ide/help-content-manager-overrides.md).  
  
### <a name="create-the-content-set"></a>Creare il set di contenuti  
 Prima di poter creare il set di contenuti di base, è necessario disinstallare tutto il contenuto di Visual Studio locali dal computer di destinazione.  
  
##### <a name="to-uninstall-local-help"></a>Per disinstallare la Guida locale  
  
1. In Help Viewer scegliere la scheda **Gestisci contenuto**.  
  
2. In **Documentazione disponibile** passare al set di documenti di Visual Studio.  
  
3. Scegliere **Rimuovi** accanto a ogni elemento secondario.  
  
4. Scegliere **Avvia** per disinstallare  
  
5. Passare a *n*:\\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 e verificare che la cartella contenga solo il file catalogType.xml.  
  
   Dopo aver rimosso tutto il contenuto della Guida locale di Visual Studio installato in precedenza, si è pronti per scaricare il set di contenuti di base.  
  
##### <a name="to-download-the-content"></a>Per scaricare il contenuto  
  
1. In Help Viewer scegliere la scheda **Gestisci contenuto**.  
  
2. In **Documentazione disponibile** passare al set di documenti che si vuole scaricare e scegliere **Aggiungi**.  
  
3. Scegliere **Avvia**.  
  
   Ora è necessario creare un pacchetto del contenuto per poterlo distribuire ai computer client.  
  
##### <a name="to-package-the-content"></a>Per creare un pacchetto del contenuto  
  
1. Creare una cartella in cui copiare il contenuto da distribuire.  
  
     Ad esempio: c:\VS12Help.  
  
2. Aprire cmd.exe con le autorizzazioni di amministratore.  
  
3. Passare alla cartella creata nel passaggio 1.  
  
4. Digitare quanto segue:  
  
     Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \<*nome cartella*>\ /y /e /k /o  
  
     Ad esempio: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`  
  
### <a name="deploying-the-content"></a>Distribuzione del contenuto  
  
##### <a name="to-deploy-the-content"></a>Per distribuire il contenuto  
  
1. Creare una condivisione di rete e copiare il contenuto della Guida in tale posizione.  
  
     Ad esempio copiare il contenuto di c:\VS12Help in \\\myserver\VS12Help.  
  
2. Creare un file .bat che dovrà contenere lo script di distribuzione per il contenuto della Guida. Poiché potrebbe verificarsi un blocco di lettura nel client per qualsiasi file da eliminare durante il push, è necessario arrestare il client prima del push degli aggiornamenti.  
  
     Ad esempio:  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)  
  
    REM - get processor type and create/run registry update file  
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64  
  
    @echo Architecture type is x86  
  
    ECHO Windows Registry Editor Version 5.00 > x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "FirstTimeRun"="False"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg  
  
    regedit.exe /s x86.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)  
  
    GOTO CONTINUE  
  
    :AMD64  
    @echo Architecture type is AMD64  
  
    ECHO Windows Registry Editor Version 5.00 > x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg  
    ECHO "FirstTimeRun"="False"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg  
  
    regedit.exe /s x64.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)  
  
    :CONTINUE  
    ```  
  
3. Eseguire il file .bat nei computer locali in cui deve essere installato il contenuto della Guida.  
  
## <a name="see-also"></a>Vedere anche  
 [Argomenti della riga di comando per la Gestione contenuto della Guida](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [Ovverride di Gestione contenuto della Guida](../ide/help-content-manager-overrides.md)
