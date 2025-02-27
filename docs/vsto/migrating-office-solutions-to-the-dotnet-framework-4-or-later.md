---
title: Eseguire la migrazione di soluzioni Office a .NET Framework 4 o versioni successive
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 729fafd1f6dfdf889293c9686f455be8de5a81fc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970375"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Eseguire la migrazione di soluzioni Office a .NET Framework 4 o versioni successive
  Se il framework di destinazione di un progetto di Office viene modificato per il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o in un secondo momento da una versione precedente di .NET Framework, alcune potrebbero essere necessari passaggi aggiuntivi per continuare a eseguire la soluzione nei computer di sviluppo e agli utenti finali. Per altre informazioni, vedere [necessarie modifiche per l'esecuzione di progetti di Office migrati a .NET Framework 4 o .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Inoltre, il progetto potrebbe non venire più compilato. Alcune funzionalità dei progetti di Office dispongono di modelli di programmazione diversi per le diverse versioni di .NET Framework. Quando il framework di destinazione di un progetto di Office viene modificato per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva da una versione precedente di .NET Framework, è necessario apportare le seguenti modifiche al codice del progetto:

- [Aggiornare i progetti di Excel e Word che si esegue la migrazione a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aggiornamento delle personalizzazioni della barra multifunzione nei progetti di Office migrati a .NET Framework 4 o .NET Framework 4.5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)

- [Aggiornare aree del modulo nei progetti di Outlook che si esegue la migrazione a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Il framework di destinazione di un progetto di Office cambia quando si aggiorna il progetto da una versione precedente di Visual Studio. Per altre informazioni, vedere [esegue l'aggiornamento e la migrazione di soluzioni Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Per altre informazioni sui motivi per cui alcune funzionalità nei progetti di Office dispongono di un modello di programmazione diverso quando la destinazione è il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, vedere [modifiche alla progettazione dei progetti di Office destinati a .NET Framework 4 o .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) e [Visual Studio Tools per Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Vedere anche
- [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Procedura: Scegliere una versione di .NET Framework di destinazione](../ide/how-to-target-a-version-of-the-dotnet-framework.md)
- [Risolvere gli errori nelle soluzioni Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Supporto aggiuntivo per gli errori nelle soluzioni Office](../vsto/additional-support-for-errors-in-office-solutions.md)
