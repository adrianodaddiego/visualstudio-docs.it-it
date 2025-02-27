---
title: Guida di Visual Studio Administrator
titleSuffix: ''
description: Altre informazioni su come distribuire Visual Studio in un ambiente aziendale.
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 61b3a2dfae667bac7c3a6a62682cdbd5b1a5feb4
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037502"
---
# <a name="visual-studio-administrator-guide"></a>Guida di Visual Studio Administrator

Negli ambienti aziendali gli amministratori di sistema distribuiscono solitamente le installazioni nei computer degli utenti finali da una condivisione di rete o tramite software di gestione dei sistemi. Il motore di installazione di Visual Studio è stato progettato per supportare la distribuzione aziendale e consente agli amministratori di sistema di creare un percorso di installazione di rete, preconfigurare valori di installazione predefiniti, distribuire codici Product Key durante il processo di installazione e gestire aggiornamenti di prodotto in seguito a una distribuzione eseguita correttamente.

Questa guida dell'amministratore offre indicazioni basate sullo scenario per la distribuzione aziendale in ambienti di rete.

## <a name="before-you-begin"></a>Prima di iniziare

Prima di distribuire Visual Studio all'interno dell'organizzazione, è necessario prendere alcune decisioni e svolgere alcune attività:

::: moniker range="vs-2019"

* Assicurarsi che ogni computer di destinazione soddisfi i [requisiti minimi di installazione](/visualstudio/releases/2019/system-requirements/).

* Definire le esigenze di manutenzione.

  Se l'azienda ha l'esigenza di mantenere un set di funzionalità più a lungo ma desidera comunque ottenere aggiornamenti di manutenzione regolari, prevedere di usare una baseline di manutenzione. Per altre informazioni, vedere la sezione ***Opzioni di supporto per i clienti Enterprise e Professional*** nella pagina [Ciclo di vita del prodotto e manutenzione di Visual Studio](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

  Se si prevede di applicare gli aggiornamenti di manutenzione insieme agli aggiornamenti delle funzionalità cumulativi, è possibile scegliere gli elementi più recenti.

* Scegliere il modello di aggiornamento.

  Decidere da dove i singoli computer client devono ottenere gli aggiornamenti. In particolare, decidere se procurarsi gli aggiornamenti da Internet o da una condivisione locale a livello aziendale. Se si sceglie di usare una condivisione locale, decidere se i singoli utenti possono aggiornare i propri client o se un amministratore si farà carico di aggiornare i client a livello di codice.

* Decidere di quali [carichi di lavoro e componenti](workload-and-component-ids.md?view=vs-2019) ha bisogno l'azienda.

* Decidere se usare un [file di risposta](automated-installation-with-response-file.md?view=vs-2019), scelta che semplifica la gestione delle informazioni dettagliate nel file di script.

* Decidere se abilitare Criteri di gruppo e se configurare la disabilitazione dei suggerimenti dei clienti nei singoli computer in Visual Studio.

::: moniker-end

::: moniker range="vs-2017"

* Assicurarsi che ogni computer di destinazione soddisfi i [requisiti minimi di installazione](/visualstudio/productinfo/vs2017-system-requirements-vs/).

* Definire le esigenze di manutenzione.

  Se l'azienda ha l'esigenza di mantenere un set di funzionalità più a lungo ma desidera comunque ottenere aggiornamenti di manutenzione regolari, prevedere di usare una baseline di manutenzione. Per altre informazioni, vedere la sezione ***Supporto per le versioni precedenti di Visual Studio*** nella pagina [Ciclo di vita del prodotto e manutenzione di Visual Studio](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio).

  Se si prevede di applicare gli aggiornamenti di manutenzione insieme agli aggiornamenti delle funzionalità cumulativi, è possibile scegliere gli elementi più recenti.

* Scegliere il modello di aggiornamento.

  Decidere da dove i singoli computer client devono ottenere gli aggiornamenti. In particolare, decidere se procurarsi gli aggiornamenti da Internet o da una condivisione locale a livello aziendale. Se si sceglie di usare una condivisione locale, decidere se i singoli utenti possono aggiornare i propri client o se un amministratore si farà carico di aggiornare i client a livello di codice.

* Decidere di quali [carichi di lavoro e componenti](workload-and-component-ids.md?view=vs-2017) ha bisogno l'azienda.

* Decidere se usare un [file di risposta](automated-installation-with-response-file.md?view=vs-2017), scelta che semplifica la gestione delle informazioni dettagliate nel file di script.

* Decidere se abilitare Criteri di gruppo e se configurare la disabilitazione dei suggerimenti dei clienti nei singoli computer in Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Passaggio 1: Scaricare i file di prodotto Visual Studio

* [Selezionare i carichi di lavoro e i componenti](workload-and-component-ids.md?view=vs-2019) da installare.

* [Creare una condivisione di rete per i file di prodotto di Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>Passaggio 2: Creare uno script di installazione

* Creare uno script di installazione che usi [parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) per controllare l'installazione.

  >[!NOTE]
  > È possibile semplificare gli script utilizzando un [file di risposta](automated-installation-with-response-file.md?view=vs-2019). Assicurarsi di creare un file di risposta che contenga l'opzione di installazione predefinita.

* (Facoltativo) Includere nello script di installazione le istruzioni per [applicare un codice Product Key per contratti multilicenza](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019), in modo che gli utenti non debbano attivare il software separatamente.

* (Facoltativo) Aggiornare il layout di rete per [controllare il momento in cui gli aggiornamenti del prodotto vengono messi a disposizione degli utenti finali e la loro provenienza](controlling-updates-to-visual-studio-deployments.md?view=vs-2019).

* (Facoltativo) Impostare i criteri del registro di sistema che influiscono sulla distribuzione di Visual Studio, ad esempio dove sono installati alcuni pacchetti condivisi con altre versioni o istanze, [dove vengono memorizzati i pacchetti nella cache](set-defaults-for-enterprise-deployments.md?view=vs-2019) o [se i pacchetti vengono memorizzati nella cache](disable-or-move-the-package-cache.md?view=vs-2019).

* (Facoltativo) Impostare Criteri di gruppo. È anche possibile [configurare Visual Studio per disabilitare i suggerimenti dei clienti](../ide/visual-studio-experience-improvement-program.md) nei singoli computer.

## <a name="step-3---deploy"></a>Passaggio 3: Distribuire

* Usare la tecnologia di distribuzione desiderata per eseguire lo script nelle workstation di sviluppo di destinazione.

## <a name="step-4---deploy-updates"></a>Passaggio 4: Distribuire gli aggiornamenti

* [Aggiornare il percorso di rete con gli aggiornamenti più recenti](update-a-network-installation-of-visual-studio.md?view=vs-2019) di Visual Studio eseguendo regolarmente il comando usato nel passaggio 1 in modo da aggiungere i componenti aggiornati.

  È possibile aggiornare Visual Studio usando uno script di aggiornamento. A tale scopo, usare il parametro della riga di comando [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019).

## <a name="step-5---optional-use-visual-studio-tools"></a>Passaggio 5: (Facoltativo) Usare gli strumenti di Visual Studio

Sono stati resi disponibili diversi strumenti che consentono di [rilevare e gestire le istanze installate di Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019) nei computer client.

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Passaggio 1: Scaricare i file di prodotto Visual Studio

* [Selezionare i carichi di lavoro e i componenti](workload-and-component-ids.md?view=vs-2017) da installare.

* [Creare una condivisione di rete per i file di prodotto di Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>Passaggio 2: Creare uno script di installazione

* Creare uno script di installazione che usi [parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) per controllare l'installazione.

  >[!NOTE]
  > È possibile semplificare gli script utilizzando un [file di risposta](automated-installation-with-response-file.md?view=vs-2017). Assicurarsi di creare un file di risposta che contenga l'opzione di installazione predefinita.

* (Facoltativo) Includere nello script di installazione le istruzioni per [applicare un codice Product Key per contratti multilicenza](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017), in modo che gli utenti non debbano attivare il software separatamente.

* (Facoltativo) Aggiornare il layout di rete per [controllare il momento in cui gli aggiornamenti del prodotto vengono messi a disposizione degli utenti finali e la loro provenienza](controlling-updates-to-visual-studio-deployments.md?view=vs-2017).

* (Facoltativo) Impostare i criteri del registro di sistema che influiscono sulla distribuzione di Visual Studio, ad esempio dove sono installati alcuni pacchetti condivisi con altre versioni o istanze, [dove vengono memorizzati i pacchetti nella cache](set-defaults-for-enterprise-deployments.md?view=vs-2019) o [se i pacchetti vengono memorizzati nella cache](disable-or-move-the-package-cache.md?view=vs-2017).

* (Facoltativo) Impostare Criteri di gruppo. È anche possibile [configurare Visual Studio per disabilitare i suggerimenti dei clienti](../ide/visual-studio-experience-improvement-program.md) nei singoli computer.

## <a name="step-3---deploy"></a>Passaggio 3: Distribuire

* Usare la tecnologia di distribuzione desiderata per eseguire lo script nelle workstation di sviluppo di destinazione.

## <a name="step-4---deploy-updates"></a>Passaggio 4: Distribuire gli aggiornamenti

* [Aggiornare il percorso di rete con gli aggiornamenti più recenti](update-a-network-installation-of-visual-studio.md?view=vs-2017) di Visual Studio eseguendo regolarmente il comando usato nel passaggio 1 in modo da aggiungere i componenti aggiornati.

  È possibile aggiornare Visual Studio usando uno script di aggiornamento. A tale scopo, usare il parametro della riga di comando [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019).

## <a name="step-5---optional-use-visual-studio-tools"></a>Passaggio 5: (Facoltativo) Usare gli strumenti di Visual Studio

Sono stati resi disponibili diversi strumenti che consentono di [rilevare e gestire le istanze installate di Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017) nei computer client.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
* [Installare i certificati necessari per l'installazione offline di Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Importare o esportare configurazioni di installazione](import-export-installation-configurations.md)
* [Visual Studio Setup Archives](https://devblogs.microsoft.com/setup/tag/vs2017/) (Archivi di installazione di Visual Studio)
* [Ciclo di vita del prodotto e manutenzione di Visual Studio](/visualstudio/releases/2019/servicing/)
* [Impostazioni di caricamento automatico sincrono](../extensibility/synchronously-autoloaded-extensions.md)
