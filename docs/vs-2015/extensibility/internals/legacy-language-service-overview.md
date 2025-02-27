---
title: Panoramica del servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5964aa82d76791d29313ac787f1216c9c9ad283
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066156"
---
# <a name="legacy-language-service-overview"></a>Panoramica dei servizi di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servizio di linguaggio fornisce supporto dell'editor che consente di implementare determinati [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] funzionalità. Le classi del servizio linguaggio Framework di pacchetto gestito (MPF) offrono il supporto completo per le funzionalità usati di frequente e un supporto parziale per le altre funzionalità.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Funzionalità completamente supportate in MPF  
 Le classi del servizio del linguaggio MPF supportano le funzionalità seguenti:  
  
- Evidenziazione della sintassi  
  
- struttura  
  
- Aggiunta di commenti blocchi di codice  
  
- Corrispondenza parentesi graffe  
  
- Frammenti di codice  
  
- Proprietà personalizzate dei documenti  
  
- Informazioni sui parametri di IntelliSense  
  
- Informazioni rapide di IntelliSense  
  
- Completamento dei membri IntelliSense  
  
- Completamento delle parole IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Funzionalità parzialmente supportate in MPF  
 MPF supporta parzialmente solo per le funzionalità seguenti. Ciò significa che è necessario implementare i metodi chiamati da MPF.  
  
- Riformattazione del codice. Si fornisce il codice che implementa la riformattazione.  
  
- Esegue la convalida dei punti di interruzione identificando gli intervalli di codice valido. Si fornisce il codice che identifica gli intervalli di codice.  
  
- Supporto del debugger **Auto** finestra per la visualizzazione di variabili. Si fornisce il codice che determina gli elementi da visualizzare nella finestra.  
  
- Che supportano il **sulla barra di navigazione** per la navigazione rapida tra tipi e membri. Si implementa e restituire una classe helper che consente di popolare gli elenchi nel **sulla barra di navigazione** caselle combinate.  
  
## <a name="implementation"></a>Implementazione  
 È necessario completare diversi passaggi per implementare il servizio di linguaggio stesso e le funzionalità di servizio di linguaggio che si desidera supportare per la propria lingua. Questi passaggi sono descritti negli argomenti seguenti:  
  
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
- [Definizione della struttura in un servizio di linguaggio legacy](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
- [Aggiunta di commenti al codice in un servizio di linguaggio legacy](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
- [Riformattazione del codice in un servizio di linguaggio legacy](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
- [Proprietà personalizzate dei documenti in un servizio di linguaggio legacy](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
- [Supporto per i frammenti di codice in un servizio di linguaggio legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
- [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
- [Completamento delle parole in un servizio di linguaggio legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
- [Completamento dei membri in un servizio di linguaggio legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
- [Informazioni rapide in un servizio di linguaggio legacy](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
- [Supporto per la finestra Auto in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
- [Convalida dei punti di interruzione in un servizio di linguaggio legacy](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)
