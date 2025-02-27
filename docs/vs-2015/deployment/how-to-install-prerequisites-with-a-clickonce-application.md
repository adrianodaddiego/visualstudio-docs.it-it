---
title: "Procedura: Installare i prerequisiti con un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18c8dd4d0bc79ac2f3af44b8b5f8dd6faacb9f45
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434085"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Procedura: Installare i prerequisiti con un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tutti i [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazioni richiedono che la versione corretta di .NET Framework sia installata in un computer prima di poter essere eseguiti, molte applicazioni hanno anche altri prerequisiti. Quando si pubblica un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione, è possibile scegliere un set di componenti dei prerequisiti per essere incluso nel pacchetto insieme all'applicazione. Al momento dell'installazione, verrà eseguita la verifica per ogni prerequisito determinare se esiste già; Se non verrà installato prima di installare il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione.  
  
 Invece di assemblare e pubblicare i prerequisiti, è anche possibile specificare un percorso di download per i componenti. Invece inclusi i prerequisiti con tutte le applicazioni pubblicate, ad esempio, si potrebbe usare una condivisione file centralizzato o percorso Web che contiene i programmi di installazione per tutti i prerequisiti, al momento dell'installazione, verranno scaricati i componenti e installato da quel percorso.  
  
> [!IMPORTANT]
> È necessario aggiungere pacchetti di installazione dei prerequisiti nel computer di sviluppo prima di pubblicare la prima volta [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione. Per altre informazioni, vedere [Procedura: Includere i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Prerequisiti vengono gestiti nel **prerequisiti** finestra di dialogo, accessibile dal **Publish** riquadro del **Progettazione progetti**.  
  
> [!NOTE]
> Oltre all'elenco predeterminato dei prerequisiti, è possibile aggiungere componenti personalizzati all'elenco. Per altre informazioni, vedere [creazione di pacchetti Bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Per specificare i prerequisiti da installare con un'applicazione ClickOnce  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Selezionare il **pubblica** riquadro.  
  
3. Fare clic sui **prerequisiti** per aprire il **prerequisiti** nella finestra di dialogo.  
  
4. Nella finestra di dialogo **Prerequisiti** verificare che la casella di controllo **Crea programma di installazione per installare componenti dei prerequisiti** sia selezionata.  
  
5. Nel **prerequisiti** elencare, controllare i componenti che si desiderano installare e quindi fare clic su **OK**.  
  
     I componenti selezionati verranno incluso nel pacchetto e pubblicati insieme all'applicazione.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Per specificare un percorso di download diverse per i prerequisiti  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Selezionare il **pubblica** riquadro.  
  
3. Fare clic sui **prerequisiti** per aprire il **prerequisiti** nella finestra di dialogo.  
  
4. Nella finestra di dialogo **Prerequisiti** verificare che la casella di controllo **Crea programma di installazione per installare componenti dei prerequisiti** sia selezionata.  
  
5. Nel **specificare il percorso di installazione dei prerequisiti** sezione, selezionare **Scarica prerequisiti dal seguente percorso**.  
  
6. Selezionare un percorso nell'elenco a discesa scegliere o immettere un URL, percorso del file o percorso FTP e quindi fare clic su **OK.**  
  
    > [!NOTE]
    > È necessario assicurarsi che i programmi di installazione per i componenti specificati esistano nel percorso specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
