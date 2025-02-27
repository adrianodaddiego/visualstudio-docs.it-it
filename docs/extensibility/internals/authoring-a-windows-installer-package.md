---
title: Creazione di un pacchetto di programma di installazione di Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da68fa0a6c115a09ba2050f8c84ea6700ee4fc76
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315795"
---
# <a name="author-a-windows-installer-package"></a>Creare un pacchetto Windows Installer
Il modello di Windows Installer le unità di dati. Anziché scrivere uno script contenente le procedure per copiare i file e scrivere le voci del Registro di sistema, ad esempio, si creano righe e colonne nelle tabelle di database che contengono dati di file e Registro di sistema.

## <a name="database-entries"></a>Voci di database
Per installare un pacchetto VSPackage, un pacchetto Windows Installer deve contenere le voci del database per eseguire le attività seguenti:

- Eseguire la ricerca del sistema per individuare le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta il pacchetto VSPackage (usando le tabelle di Windows Installer che includono AppSearch CompLocator, RegLocator, DrLocator e firma).

- Annullare l'installazione se nessuna versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è installato o se un altro requisito di sistema del pacchetto VSPackage non viene soddisfatta (usando la tabella LaunchCondition).

- Installare il pacchetto VSPackage e i file dipendenti (utilizzando la directory, componenti e le tabelle file).

- Aggiungere le informazioni appropriate per il pacchetto VSPackage nel Registro di sistema (usando la tabella del Registro di sistema).

- Integrare il pacchetto VSPackage nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiamando **/setup devenv.exe** (usando la tabella CustomAction).

Per altre informazioni, vedere [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Strumenti di installazione
Un'ampia gamma di strumenti di installazione di terze parti offrono un ambiente di sviluppo per pacchetti di Windows Installer. I seguenti strumenti gratuiti sono disponibili:

- InstallShield limited edition

   È possibile ottenere una versione limitata di InstallShield tramite Visual Studio **nuovo progetto** finestra di dialogo. Espandere **altri tipi di progetto** e quindi selezionare **il programma di installazione e distribuzione**. Selezionare il modello di InstallShield.

- Set di strumenti Windows Installer XML

   Il set di strumenti di Windows Installer XML (WiX) compila i pacchetti di Windows Installer dai file di origine XML. Il set di strumenti WiX è un progetto open source di Microsoft. È possibile scaricare il codice sorgente e file eseguibili da [set di strumenti Wix](http://sourceforge.net/projects/wix).

   Per i prodotti commerciali integrano [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vedere [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Vedere anche
- [Installare i pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)