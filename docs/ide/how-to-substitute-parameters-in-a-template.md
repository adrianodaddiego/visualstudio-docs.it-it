---
title: Aggiungere parametri dei nomi ai modelli di progetto e di elemento
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cf9a990be3f5e87180967a4f9f274ec79fbc357e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946881"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Procedura: Sostituire i parametri di un modello

I parametri dei modelli consentono di sostituire identificatori come nomi delle classi e spazi dei nomi quando viene creato un file da un modello. È possibile aggiungere i parametri dei modelli a modelli esistenti o creare modelli personalizzati con i parametri di modello.

I parametri dei modelli vengono scritti nel formato $*parametro*$. Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).

Nella sezione seguente viene illustrato come modificare un modello in modo da sostituire il nome di uno spazio dei nomi con il "nome di progetto sicuro".

## <a name="example---namespace-name"></a>Esempio - nome dello spazio dei nomi

1. Inserire il parametro in uno o più dei file di codice nel modello. Ad esempio:

    ```csharp
    namespace $safeprojectname$
    ```

1. Nel file *vstemplate* del modello individuare l'elemento `ProjectItem` che include il file.

1. Impostare l'attributo `ReplaceParameters` su `true` per l'elemento `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Vedere anche

- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Parametri di modello](../ide/template-parameters.md)
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)