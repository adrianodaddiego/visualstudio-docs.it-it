---
title: Visualizzazione di file tramite l'apertura con comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66ca76d7e25d1f9f1fa23605a83b68094686fcd5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351559"
---
# <a name="display-files-by-using-the-open-with-command"></a>Visualizzare i file usando il comando Apri con
Un progetto può chiedere l'IDE per visualizzare il **aperta con** nella finestra di dialogo. Questa richiesta chiede all'utente di aprire un file con una selezione dell'editor standard. I passaggi seguenti descrivono questo processo:

1. Le chiamate di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, specificando il valore `OSE_UseOpenWithDialog` per il `OSEOpenDocEditor` parametro.

2. Basato sull'estensione del nome file del documento, l'IDE determina quale editor elencate nel controllo del Registro di sistema può aprire il documento specificato e visualizza queste informazioni nel **Apri con** nella finestra di dialogo.

    > [!NOTE]
    > Progetti con un editor intrinseco che deve essere incluso nel **aperta con** nella finestra di dialogo deve registrare una factory dell'editor per ogni tali editor. Editor intrinseco funzionare solo insieme a un particolare tipo di progetto, che viene applicato nell'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (metodo). L'IDE include una factory dell'editor predefinita per l'editor di testo principale e l'editor binario. L'IDE crea anche un'istanza di una factory dell'editor per conto di ogni associazione di file Windows registrati. Un esempio di file di questo tipo è Microsoft Word.

3. Non appena l'utente seleziona un elemento dal **Apri con** finestra di dialogo, quindi l'IDE si apre il documento chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> (metodo). Per altre informazioni, vedere [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vedere anche
- [Aprire e salvare elementi del progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Visualizzare i file usando il comando Apri File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Procedura: Apri editor standard](../../extensibility/how-to-open-standard-editors.md)
