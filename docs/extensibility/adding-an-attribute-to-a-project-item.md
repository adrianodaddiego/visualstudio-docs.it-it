---
title: Aggiunta di un attributo a un elemento di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8524ebc866d92cfe39a19dc79165da7c38025628
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352373"
---
# <a name="add-an-attribute-to-a-project-item"></a>Aggiungere un attributo a un elemento del progetto
I metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> ottenere e impostare il valore degli attributi di un elemento del progetto. SetItemAttribute crea l'attributo se non esiste già, aggiungerlo ai metadati dell'elemento di progetto.

## <a name="add-an-attribute-to-a-project-item"></a>Aggiungere un attributo a un elemento del progetto

- Il codice seguente usa il <xref:EnvDTE.DTE> oggetto di automazione e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> metodo per aggiungere un attributo a un elemento del progetto. L'ID di elemento di progetto viene ottenuto dal nome di elemento di progetto "program.cs". L'attributo "MyAttribute" viene aggiunto a questo elemento del progetto e assegnato il valore "MyValue".

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Vedere anche
- [Rendere persistenti i dati nel file di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
