---
title: "Procedura: Impostare autorizzazioni personalizzate per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c8a6fd6625726f749afcf20b80f83178a47ab92
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406997"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce
È possibile distribuire un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che usa le autorizzazioni predefinite per le aree Internet o Intranet locale. In alternativa, è possibile creare un'area personalizzata per le autorizzazioni specifiche necessarie all'applicazione. È possibile eseguire questa operazione personalizzando le autorizzazioni di sicurezza nella pagina **Sicurezza** di **Creazione progetti**.

### <a name="to-customize-a-permission"></a>Per personalizzare un'autorizzazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Sicurezza** .

3. Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .

4. Selezionare il pulsante di opzione **È un'applicazione con attendibilità parziale** .

     I controlli nella sezione **Autorizzazioni di sicurezza ClickOnce** sono abilitati.

5. Dall'elenco a discesa **Area da cui verrà installata l'applicazione** selezionare **(Personalizzata)**.

6. Fare clic su **Modifica XML autorizzazioni**.

     Il file *app.manifest* verrà aperto nell'editor XML.

7. Prima dell'elemento `</applicationRequestMinimum>` , aggiungere il codice XML per le autorizzazioni richieste dall'applicazione.

    > [!NOTE]
    > È possibile usare il metodo `ToXml` di un set di autorizzazioni per generare il codice XML per il manifesto dell'applicazione. Ad esempio, per generare il codice XML per il set di autorizzazioni <xref:System.Security.Permissions.EnvironmentPermission> , chiamare il metodo <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> .

## <a name="see-also"></a>Vedere anche
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
