---
title: Finestra di dialogo Impostazioni di sicurezza avanzate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: afdeda6c18c20af1b7f82e42cedc4aadac13ebcb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661673"
---
# <a name="advanced-security-settings-dialog-box"></a>Finestra di dialogo Impostazioni di sicurezza avanzate
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa finestra di dialogo consente di specificare le impostazioni di sicurezza correlate al debug nell'area di sicurezza.  
  
 Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, quindi scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Sicurezza**. Nella pagina **Sicurezza** selezionare **Abilita impostazioni di sicurezza ClickOnce**, fare clic su **È un'applicazione con attendibilità parziale**, quindi fare clic su **Avanzate**.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Esegui debug dell'applicazione con il set di autorizzazioni selezionato**  
 Se si seleziona questa casella di controllo, durante il debug verrà usato il set di autorizzazioni selezionato nella pagina **Sicurezza**. Questa opzione è selezionata per impostazione predefinita.  
  
 Per il corretto funzionamento del debug in un'area di sicurezza è necessario abilitare questa opzione e l'opzione **Abilita processo di hosting di Visual Studio**, disponibile nella pagina **Debug** di **Creazione progetti**.  
  
 Per i progetti Applicazione Web browser WPF, l'opzione **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** è selezionata e disabilitata.  
  
 **Concedi all'applicazione accesso al proprio sito di origine**  
 Se si seleziona questa casella di controllo, l'applicazione può accedere al sito Web o alla condivisione server in cui è pubblicata. Questa opzione è selezionata per impostazione predefinita.  
  
 **Esegui debug dell'applicazione come se fosse stata scaricata dal seguente URL**  
 Se è necessario consentire all'applicazione di accedere al sito Web o alla condivisione server corrispondente all'**URL di installazione** specificato nella pagina **Pubblica**, digitare qui l'URL. Questa opzione è disponibile solo se la casella di controllo **Concedi all'applicazione accesso al proprio sito di origine** è selezionata.  
  
## <a name="see-also"></a>Vedere anche  
 [Pagina Sicurezza, Creazione progetti](../../ide/reference/security-page-project-designer.md)
