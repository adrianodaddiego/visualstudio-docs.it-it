---
title: Registrazione degli eventi per le soluzioni Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 480a355ee2af321341c54b90edcc582d49102186
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951941"
---
# <a name="event-logging-for-office-solutions"></a>Registrazione degli eventi per le soluzioni Office
  È possibile usare il Visualizzatore eventi di Windows per visualizzare i messaggi di eccezione acquisiti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quando si installano o disinstallano soluzioni Office. Questi messaggi del registratore eventi possono essere usati per risolvere i problemi di installazione e di distribuzione.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="read-the-event-log"></a>Leggere il registro eventi
 Aprire il **Visualizzatore eventi** e applicare un filtro per visualizzare solo gli eventi desiderati.

### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Per leggere il registro eventi in Windows Server 2003 e Windows XP

1. Aprire **Strumenti di amministrazione**nel Pannello di controllo.

2. Avviare il **Visualizzatore eventi**.

3. Nell'elenco dei registri eventi, selezionare **Applicazione**.

4. Scegliere **Filtro** dal menu **Visualizza**.

5. Selezionare **VSTO 4.0** nell'elenco **Origine evento**.

6. Per gli eventi di installazione, digitare **4096** nella casella **ID evento**.

7. Fare clic su **OK** per visualizzare l'elenco filtrato.

### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Per leggere il registro eventi in Windows 7, Windows Vista e Windows Server 2008

1. Aprire **Strumenti di amministrazione**nel Pannello di controllo.

2. Avviare il **Visualizzatore eventi**.

3. Espandere **Registri di Windows**.

4. Nell'elenco dei registri eventi, selezionare **Applicazione**.

5. Scegliere **Filtro registro corrente** dal menu **Azione**.

6. Selezionare **VSTO 4.0** nell'elenco **Origine evento**.

7. Per gli eventi di installazione, digitare **4096** nella casella **ID evento**.

8. Fare clic su **OK** per visualizzare l'elenco filtrato.

   Il Visualizzatore eventi include le informazioni seguenti:

- Il percorso del manifesto della distribuzione per la soluzione.

- Un messaggio che descrive la causa dell'errore o dell'eccezione.

  Questi messaggi di eccezione possono consentire di determinare la causa di un problema di installazione, ad esempio un certificato o un percorso di documento non attendibile oppure un manifesto della distribuzione non valido.

  Dopo la disinstallazione di una soluzione Office, i messaggi di eccezione rimangono nel registro eventi.

  Per visualizzare o registrare messaggi di eccezione durante l'esecuzione di una soluzione Office, vedere [Debug Office projects](../vsto/debugging-office-projects.md) e [progetti di Office di eseguire il Debug](../vsto/debugging-office-projects.md).

### <a name="localization"></a>Localizzazione
 Il linguaggio del messaggio di eccezione viene determinato dal linguaggio di runtime di Visual Studio Tools per Office. Ad esempio, se il computer dell'utente finale ha il language pack giapponese installato, il messaggio di eccezione viene scritto nel registro eventi in giapponese.

## <a name="disable-the-event-logger"></a>Disabilitare il Registratore eventi
 Quando si installano o disinstallano soluzioni Office, il registratore eventi viene attivato per impostazione predefinita. Per disabilitarlo è possibile impostare la variabile di ambiente VSTO_EVENTLOGDISABLED su "1" (uno).

### <a name="to-disable-the-event-log"></a>Per disabilitare il registro eventi

1. Aprire **Sistema**nel Pannello di controllo.

2. Nella scheda **Avanzate** fare clic su **Variabili di ambiente**.

3. Nel riquadro **Variabili di sistema** , fare clic su **Nuovo**.

4. Nella finestra di dialogo **Nuova variabile di sistema** , digitare **VSTO_EVENTLOGDISABLED** nella casella **Nome variabile** .

5. Nella casella **Valore variabile** , digitare **1**.

6. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Risolvere i problemi di distribuzione di soluzioni Office](../vsto/troubleshooting-office-solution-deployment.md)
