---
title: La registrazione di estensioni di File per le distribuzioni Side-By-Side | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bdfb562ddfcce2584b8868c3c931c21f9dbc127
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334236"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrare le estensioni di file per le distribuzioni side-by-side
Per i pacchetti VSPackage distribuiti in un ambiente side-by-side, è necessario registrare le estensioni di file per associare i file con la versione corretta di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A meno che non si usa un'estensione di file specifici della versione, la registrazione consente agli utenti di aprire il progetto e file di elementi nella versione appropriata del progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Contenuto della sezione
- [Sulle estensioni di file](../extensibility/about-file-name-extensions.md) viene illustrato come estensioni di file registrate.

- [Specificare i gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md) fornisce informazioni su come registrare le applicazioni che possono essere aperti, modifica e così via, un'estensione particolare.

- [Registrare i verbi per estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md) illustra come registrare i verbi.

- [Gestisci associazioni file side-by-side](../extensibility/managing-side-by-side-file-associations.md) descrive come gestire le installazioni side-by-side in cui una determinata versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve essere richiamato per aprire un file.

## <a name="related-sections"></a>Sezioni correlate
- [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) vengono descritti i problemi relativi a più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e ai VSPackage durante lo sviluppo e distribuzione agli utenti finali.