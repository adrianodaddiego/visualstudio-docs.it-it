---
title: 'Procedura: Abilitare le impostazioni di sicurezza ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e52acc18aa18873076df3d02071616c0399b1f33
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407127"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Procedura: Abilitare le impostazioni di sicurezza ClickOnce
Sicurezza dall'accesso di codice per applicazioni ClickOnce deve essere abilitata per poter pubblicare l'applicazione. Ciò avviene automaticamente quando si pubblica un'applicazione usando la pubblicazione guidata.

 In alcuni casi, l'abilitazione di sicurezza dall'accesso di codice può influire sulle prestazioni quando si compila o il debug dell'applicazione. In questi casi, si desidera disabilitare temporaneamente le impostazioni di sicurezza.

 Impostazioni di sicurezza ClickOnce possono essere abilitate o disabilitate sul **sicurezza** pagina della **creazione progetti**.

### <a name="to-enable-clickonce-security-settings"></a>Per abilitare le impostazioni di sicurezza ClickOnce

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Sicurezza** .

3. Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .

     È ora possibile personalizzare le impostazioni di sicurezza per l'applicazione nella pagina sicurezza.

    > [!NOTE]
    > Questa casella di controllo è selezionata automaticamente ogni volta che l'applicazione viene pubblicata con il **pubblica** procedura guidata.

### <a name="to-disable-clickonce-security-settings"></a>Per disabilitare le impostazioni di sicurezza ClickOnce

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Sicurezza** .

3. Cancella il **Enable ClickOnce Security Settings** casella di controllo.

     L'applicazione verrà eseguita con le impostazioni di sicurezza con attendibilità totale; tutte le impostazioni sul **sicurezza** pagina verrà ignorata.

    > [!NOTE]
    > Ogni volta che l'applicazione viene pubblicata con la pubblicazione guidata, verrà selezionata questa casella di controllo; è necessario cancellarlo nuovo termine di ogni pubblicazione.

## <a name="see-also"></a>Vedere anche
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
