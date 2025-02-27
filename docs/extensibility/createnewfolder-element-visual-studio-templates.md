---
title: Elemento CreateNewFolder (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51b7702f1b1e1c509f4f9d88d72f170d0ed765f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341772"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>Elemento CreateNewFolder (modelli di Visual Studio)
Determina se controllare se la directory di destinazione in cui verrà creato il progetto esiste o meno. Se la directory è inesistente, è possibile crearne una nuova per il progetto. Di norma, il flag del Registro di sistema `NewProjectRequiresNewFolder(VsTemplate)` (`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`), usato da tutti i tipi di progetto comuni per determinare se creare un nuovo progetto in una nuova directory, esegue l'override di questa impostazione.

 \<VSTemplate > \<TemplateData > \<CreateNewFolder >

## <a name="syntax"></a>Sintassi

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>Tipo
 `Boolean`

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere `true` o `false`, a indicare se è necessario creare una nuova cartella contenitore quando viene creato un progetto dal modello oppure no.

## <a name="remarks"></a>Note
 `CreateNewFolder` è un elemento facoltativo. Il valore predefinito è `true`.

 Il valore specificato nell'elemento `CreateNewFolder` viene rispettato da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solo se il sistema del progetto sottostante lo supporta.

## <a name="example"></a>Esempio
 Con l'esempio di codice seguente è possibile specificare di non creare una nuova cartella quando un progetto viene creato dal modello.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
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
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)