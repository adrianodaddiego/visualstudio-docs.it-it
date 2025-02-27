---
title: "Procedura: Personalizzare la pagina Web predefinita per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ec63fe5ae4b99252321b86b44066c46842a0851
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433901"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Procedura: Personalizzare la pagina Web predefinita per un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si pubblica un'applicazione ClickOnce per il Web, una pagina Web viene automaticamente generata e pubblicata insieme all'applicazione. La pagina predefinita contiene il nome dell'applicazione e i collegamenti per installare l'applicazione, installare i prerequisiti o accedere alla Guida in MSDN.  
  
> [!NOTE]
> I collegamenti effettivi che viene visualizzato nella pagina dipendono dal computer in cui viene visualizzata la pagina e ciò che sono inclusi i prerequisiti.  
  
 Il nome predefinito per la pagina Web è Publish; htm. è possibile modificare il nome nel **Progettazione progetti**. Per altre informazioni, vedere [Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 La pagina Web Publish viene pubblicata solo se viene rilevata una versione più recente.  
  
> [!NOTE]
> Le modifiche apportate alle **pubblica** impostazioni non riguardano la pagina Publish. htm, con una sola eccezione: se si aggiunge o rimuove i prerequisiti dopo la pubblicazione inizialmente, l'elenco dei prerequisiti non saranno accurata. È necessario modificare il testo per il collegamento dei prerequisiti in modo da riflettere le modifiche.  
  
### <a name="to-customize-the-publish-web-page"></a>Per personalizzare la pagina Web pubblica  
  
1. Pubblicare l'applicazione ClickOnce in un percorso Web. Per altre informazioni, vedere [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2. Nel server Web, aprire il file Publish. htm in Visual Web Designer o un altro editor di codice HTML.  
  
3. Personalizzare la pagina in base alle esigenze e salvarlo.  
  
4. Facoltativo. Per impedire la sovrascrittura della pagina Web pubblica personalizzate di Visual Studio, deselezionare **genera automaticamente pagina web di distribuzione dopo ogni pubblicazione** nella finestra di dialogo Opzioni di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
