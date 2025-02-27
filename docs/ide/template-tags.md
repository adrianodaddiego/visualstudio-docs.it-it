---
title: Aggiungere o modificare tag nei modelli di progetto
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jillfra
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 4a5113fa7f420d58892e2737ec9196422486490e
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2019
ms.locfileid: "66038627"
---
# <a name="add-tags-to-project-templates"></a>Aggiungere tag ai modelli di progetto

A partire da [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) versione 16.1 Preview 2, è possibile aggiungere tag per il linguaggio, la piattaforma e il tipo di progetto ai modelli di progetto. I tag vengono usati in due posizioni nella finestra di dialogo Nuovo progetto:

- I tag vengono visualizzati sotto la descrizione del modello

   ![Modello di progetto con i tag nella finestra di dialogo Nuovo progetto](media/npd-item-with-template-tags.png)

- I tag consentono operazioni di ricerca e filtro per i modelli

   ![Ricerca e filtro nella finestra di dialogo Nuovo progetto](media/npd-search-and-filter.png)

È possibile aggiungere tag aggiornando il file XML con estensione *vstemplate* usando i tag modello inclusi in Visual Studio o tramite la creazione di tag modello personalizzati. I tag modello vengono visualizzati solo nella finestra di dialogo Nuovo progetto di Visual Studio 2019. Non influiscono sul rendering del modello nelle versioni precedenti di Visual Studio.

## <a name="add-or-edit-tags"></a>Aggiungere o modificare tag

È possibile aggiungere o modificare tag nel file XML *vstemplate* del modello di progetto nei casi seguenti:

* [Creazione di un nuovo modello di progetto](/visualstudio/ide/how-to-create-project-templates) tramite l'Esportazione guidata modelli

* [Aggiornamento del modello di progetto esistente](/visualstudio/ide/how-to-update-existing-templates)

* [Creazione di un nuovo modello di progetto VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)

## <a name="syntax"></a>Sintassi

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Attributi

Gli attributi seguenti sono facoltativi e progettati per scenari utente avanzati.

|Attributo|Description|
|---------------|-----------------|
|`Package`|GUID che specifica l'ID del pacchetto di Visual Studio.|
|`ID`|Specifica l'ID di risorsa di Visual Studio.|

Sintassi:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Elementi

### <a name="child-elements"></a>Elementi figlio

Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Obbligatorio) Classifica il modello in base alla categoria e ne definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.|

## <a name="text-value"></a>Valore di testo

È necessario un valore di testo, a meno che non si usino gli attributi `Package` e `ID`.

Il testo fornisce il nome del modello.

## <a name="built-in-tags"></a>Tag predefiniti

Visual Studio offre numerosi tag predefiniti che possono essere aggiunti per eseguire il rendering di una risorsa localizzata. L'elenco seguente include i tag predefiniti e i valori corrispondenti tra parentesi.

| Linguaggio | Piattaforma | Tipo progetto |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Cloud (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Console (`console`) |
| F# (`fsharp`) | iOS (`ios`) | Desktop (`desktop`) |
| Java (`java`) | Linux (`linux`) | Estensioni (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Giochi (`games`) |
| Python (`python`) | tvOS (`tvos`) | IoT (`iot`) |
| Query Language (`querylanguage`) | Windows (`windows`) | Libreria (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Machine Learning (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Dispositivi mobili (`mobile`) |
| | | Office (`office`) |
| | | Altro (`other`) |
| | | Servizio (`service`) |
| | | Test (`test`) |
| | | UWP (`uwp`) |
| | | Web (`web`) |

## <a name="example"></a>Esempio

L'esempio seguente mostra i metadati per un modello di progetto per un'applicazione Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche

- [Riferimenti allo schema dei modelli di Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Creazione di modelli di progetti e di elementi](/visualstudio/ide/creating-project-and-item-templates)
- [Personalizzare modelli di progetto e modelli di elemento](/visualstudio/ide/customizing-project-and-item-templates)
- [Introduzione al modello di progetto VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)