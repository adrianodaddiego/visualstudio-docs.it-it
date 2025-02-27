---
title: Pagina Debug, Creazione progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 039b6722ca064c64c0e0b7f7757070852e908395
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703908"
---
# <a name="debug-page-project-designer"></a>Pagina Debug, Progettazione progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!WARNING]
> Questo argomento non si applica alle app di Windows Store. Vedere [Avviare una sessione di debug (VB, C#, C++ e XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) in Windows Dev Center.  
  
 Usare la pagina **Debug** di **Creazione progetti** per impostare le proprietà per il comportamento di debug in un progetto Visual Basic o C#.  
  
 Per accedere alla pagina **Debug** selezionare un nodo del progetto in **Esplora soluzioni**. Nel menu **Progetto** scegliere **Proprietà** _NomeProgetto_. Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Debug**.  
  
## <a name="configuration-and-platform"></a>Configurazione e Piattaforma  
 Le opzioni seguenti consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.  
  
 **Configurazione**  
 Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni possibili sono **Debug** (impostazione predefinita), **Rilascio** o **Tutte le configurazioni**. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
 **Piattaforma**  
 Specifica le impostazioni della piattaforma da visualizzare o modificare. Le scelte possono includere **Qualsiasi CPU** (impostazione predefinita), **x64** e **x86**. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
## <a name="start-action"></a>Azione di avvio  
 **Avvia azione** indica l'elemento da avviare durante il debug dell'applicazione: il progetto, un programma personalizzato, un URL o nulla. Per impostazione predefinita, questa opzione è impostata su **Avvia progetto**. L'impostazione **Avvia azione** nella pagina **Debug** determina il valore della proprietà `StartAction`.  
  
 **Avvia progetto**  
 Scegliere questa opzione per specificare che durante il debug dell'applicazione deve essere avviato il file eseguibile (per i progetti Applicazione Windows e Applicazione console). Questa opzione è selezionata per impostazione predefinita.  
  
 **Avvia programma esterno**  
 Scegliere questa opzione per specificare che durante il debug dell'applicazione deve essere avviato un programma specifico.  
  
 **Avvia il browser con URL**  
 Scegliere questa opzione per specificare che durante il debug dell'applicazione è necessario accedere a un URL specifico.  
  
## <a name="start-options"></a>Opzioni di avvio  
 **Argomenti della riga di comando**  
 Immettere in questa casella di testo gli argomenti della riga di comando da usare per il debug.  
  
 **Directory di lavoro**  
 Immettere in questa casella di testo la directory da cui verrà avviato il progetto oppure fare clic sul pulsante Sfoglia (**...**) per scegliere una directory.  
  
 **Usa computer remoto**  
 Per il debug dell'applicazione da un computer remoto selezionare questa casella di controllo e immettere il percorso al computer remoto nella casella di testo.  
  
## <a name="enable-debuggers"></a>Abilita debugger  
 **Abilita debug codice non gestito**  
 Questa opzione specifica se è supportato il debug del codice nativo. Selezionare questa casella di controllo se si effettuano chiamate a oggetti COM o se si avvia un programma personalizzato scritto in codice nativo che chiama il progetto ed è necessario eseguire il debug del codice nativo. Deselezionare questa casella di controllo per disabilitare il debug di codice non gestito. Per impostazione predefinita, questa casella di controllo è deselezionata.  
  
 **Abilita debug SQL Server**  
 Selezionare o deselezionare questa casella di controllo per abilitare o disabilitare il debug delle routine SQL dall'applicazione Visual Basic. Per impostazione predefinita, questa casella di controllo è deselezionata.  
  
 **Abilita processo di hosting di Visual Studio**  
 Selezionare questa casella di controllo per abilitare il processo di hosting di Visual Studio. Per impostazione predefinita, questa casella di controllo è selezionata. Per altre informazioni, vedere [Processo di hosting (vshost.exe)](../../ide/hosting-process-vshost-exe.md).  
  
 Per il debug in un'area di sicurezza è necessario abilitare questa opzione e selezionare la casella di controllo **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** nella [Finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debugging in Visual Studio](../../debugger/debugging-in-visual-studio.md)  (Debug in Visual Studio)  
 [Impostazioni di progetto per le configurazioni di debug C#](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Gestione delle proprietà di debug](https://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: Creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md)
