---
title: Finestra di dialogo Impostazioni avanzate per i servizi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: aa661f48a04057bae8db86e7215a6fc7cafbcfe4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699838"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Finestra di dialogo Impostazioni avanzate per i servizi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I servizi delle applicazioni client offrono accesso semplificato a servizi di accesso, ruolo e profilo di [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] da applicazioni Windows Forms e Windows Presentation Foundation (WPF). Per configurare i servizi delle applicazioni client, è possibile usare la pagina **Servizi** in **Creazione progetti**. Per altre informazioni sulla pagina **Servizi**, vedere [Services Page, Project Designer](../../ide/reference/services-page-project-designer.md) (Pagina Servizi, Creazione progetti).  
  
 Per configurare le impostazioni avanzate dei servizi delle applicazioni client, usare la finestra di dialogo **Impostazioni avanzate per i servizi**  della pagina **Servizi** in **Creazione progetti**. Queste impostazioni consentono di eseguire l'override di alcuni comportamenti predefiniti di servizi di applicazioni e abilitare scenari meno comuni. Per altre informazioni, vedere [Servizi applicazioni client](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).  
  
 Per accedere alla finestra di dialogo **Impostazioni avanzate per i servizi**, selezionare un nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà** dal menu **Progetto**. Quando **Progettazione progetti** si apre, fare clic sulla scheda **Servizi** e premere il **Avanzate**. Questo pulsante rimarrà disabilitato fino all'abilitazione dei servizi delle applicazioni client.  
  
## <a name="task-list"></a>Elenco attività  
 [Procedura: Configurare i servizi delle applicazioni client](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
 [Procedura: Lavorare Offline con servizi delle applicazioni Client](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Salva hash della password localmente per consentire l'accesso offline**  
 Specifica se un modulo crittografato della password dell'utente sarà memorizzato nella cache locale per consentire all'utente di accedere quando l'applicazione è in modalità offline. Per altre informazioni, vedere [Procedura: Lavorare Offline con servizi delle applicazioni Client](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Questa opzione è selezionata per impostazione predefinita.  
  
 **Richiedi agli utenti di accedere di nuovo a ogni scadenza del cookie del server**  
 Specifica se gli utenti precedentemente autenticati vengono automaticamente riautenticati quando l'applicazione accede al servizio ruoli o profili e il cookie di autenticazione server è scaduto. Selezionare questa opzione per negare l'accesso ai servizi dell'applicazione e richiedere esplicitamente una nuova autenticazione se il cookie è scaduto. Questa opzione è utile per applicazioni distribuite in percorsi pubblici al fine di garantire che gli utenti che escono dall'applicazione non rimangano autenticati a tempo indeterminato mentre questa continua a essere eseguita. Per impostazione predefinita, questa opzione è deselezionata.  
  
 **Timeout cache servizio ruolo**  
 Specifica il tempo che il provider dei ruoli client userà per i valori del ruolo memorizzati nella cache anziché accedere al servizio ruoli. Impostare questo intervallo di tempo su un valore basso quando i ruoli vengono aggiornati di frequente o su un valore più alto quando i ruoli vengono aggiornati di rado. Il valore predefinito è un giorno.  
  
 Il provider di ruoli accede ai valori del ruolo memorizzati nella cache o al servizio dei ruoli quando si chiama il metodo <xref:System.Web.Security.RolePrincipal.IsInRole%2A>. Per cancellare la cache a livello di codice e forzare l'accesso di questo metodo al servizio remoto, chiamare il metodo <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.  
  
 **Usa stringa di connessione personalizzata**  
 Specifica se i provider di servizi client useranno un archivio dati personalizzato per la cache locale. Per impostazione predefinita, i provider di servizi useranno il file system locale per la cache. Se si seleziona questa opzione, la casella di testo sarà automaticamente popolata con una stringa di connessione predefinita. È possibile mantenere la stringa di connessione predefinita per generare automaticamente e usare un database SQL Server Compact Edition oppure è possibile specificare una stringa di connessione a un database SQL Server esistente. Per altre informazioni, vedere [Procedura: Configurare i servizi delle applicazioni client](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). Per impostazione predefinita, questa opzione è deselezionata.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi applicazioni client](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [Services Page, Project Designer](../../ide/reference/services-page-project-designer.md)  (Pagina Servizi, Creazione progetti)  
 [Procedura: Configurare i servizi dell'applicazione Client](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [Procedura: Lavorare Offline con servizi delle applicazioni Client](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)
