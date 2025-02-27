---
title: Disabilitare l'attivazione dell'URL dell'App ClickOnce con finestra di progettazione
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8296f08c29b3259c19393a860ee34f6c3f05a42
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263282"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Procedura: Disabilitare gli URL di applicazioni ClickOnce tramite la finestra di progettazione
In genere, un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione verrà avviata automaticamente subito dopo l'installazione da un server Web. Per motivi di sicurezza, è possibile decidere di disattivare questo comportamento e comunicare agli utenti di avviare l'applicazione dal **avviare** menu invece. La procedura seguente descrive come disabilitare l’attivazione dell’URL.

 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installate nel computer dell'utente da un server Web. Non è utilizzabile per le applicazioni solo online, che possono essere avviate solo tramite i rispettivi URL. Per altre informazioni sulla differenza tra le applicazioni solo online e installate, vedere [scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Questa procedura Usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È inoltre possibile eseguire questa attività usando il [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Per altre informazioni, vedere [Procedura: Disabilitare l'attivazione dell'URL delle applicazioni ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Routine

#### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione

1. Fare clic sul nome del progetto in **Esplora soluzioni**, fare clic su **proprietà**.

2. Nel **delle proprietà** pagina, fare clic sul **pubblica** scheda.

3. Fare clic su **Opzioni**.

4. Fare clic su **manifesti**.

5. Selezionare la casella di controllo etichettata **blocco applicazione venga attivata tramite un URL**.

6. Distribuire l'applicazione,

## <a name="see-also"></a>Vedere anche
- [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)