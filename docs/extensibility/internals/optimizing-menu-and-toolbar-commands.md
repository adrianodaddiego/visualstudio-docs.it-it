---
title: Ottimizzazione dei Menu e comandi della barra degli strumenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c76e4f37fd77bd35526153bd86d419417a6cdb6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333123"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Ottimizzazione dei comandi di menu e barre degli strumenti
L'aggiunta di pacchetti VSPackage e i comandi corrispondenti a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] potrebbe essere un'interfaccia utente piena. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce metodi per ridurre al minimo la confusione di comando dell'interfaccia utente.

## <a name="in-this-section"></a>In questa sezione
- [Miglioramento della disponibilità dei comandi](../../extensibility/internals/making-commands-available.md)

 Vengono fornite linee guida generali per ridurre al minimo affollare del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente quando si aggiungono pacchetti VSPackage.

- [Linee guida per il posizionamento](../../extensibility/internals/command-placement-guidelines.md)

 Fornisce linee guida specifiche per l'implementazione di un pacchetto VSPackage in base alle dimensioni del set di comandi.

## <a name="related-sections"></a>Sezioni correlate
- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.