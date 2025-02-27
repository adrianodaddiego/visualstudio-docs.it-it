---
title: Elemento ProjectTemplateLink (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e911977156a6b750c1e15fec46ead77e1bac0204
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335850"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Elemento ProjectTemplateLink (modelli di Visual Studio)
Specifica il percorso per il *vstemplate* file di un progetto in un modello multiprogetto.

 \<VSTemplate > \<TemplateContent > \<ProjectCollection > \<ProjectTemplateLink > - oppure - \<VSTemplate > \<TemplateContent > \<ProjectCollection > \<SolutionFolder > \<ProjectTemplateLink >

## <a name="syntax"></a>Sintassi

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`ProjectName`|Attributo facoltativo.<br /><br /> Specifica il nome di ogni singolo progetto in un modello multiprogetto. Il **nuovo progetto** nella finestra di dialogo non è possibile assegnare nomi ai singoli progetti.|
|`CopyParameters`|Consente la copia di tutte le variabili nel modello del gruppo centrale in ognuno dei modelli collegati.<br /><br /> I parametri nei modelli collegati dispongono del prefisso `"$ext_*$"`. Ad esempio, se nel modello del gruppo padre il parametro `$projectname$` ha un valore **ExampleProject1**, quando il modello collegato Ottiene il proprio turno per essere eseguito, acquisisce un parametro `$ext_projectname$`, ovvero una copia del `$projectname$`parametro di modello del gruppo padre.<br /><br /> In questo modo i modelli collegati possono condividere alcuni parametri comuni, che possono essere facilmente creati solo nel modello del gruppo padre.<br /><br /> Questo attributo è facoltativo ed è automaticamente impostato su `false` quando non è incluso.<br /><br /> Introdotto in Visual Studio 2013 Update 2. Per correlare la versione corretta del prodotto, vedere [fanno riferimento agli assembly recapitati in Visual Studio 2013 SDK Update 2](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Raggruppa i progetti in modelli multiprogetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo specifica il percorso per il *vstemplate* file del modello.

## <a name="remarks"></a>Note
 I modelli multiprogetto fungono da contenitori per due o più progetti. Il `ProjectTemplateLink` elemento viene usato per specificare il percorso del *vstemplate* file per uno dei progetti nel modello. Il *vstemplate* file di un modello multiprogetto contiene un `ProjectTemplateLink` (elemento) per ogni progetto del modello. Per altre informazioni sui modelli multiprogetto, vedere [come: Creare modelli multiprogetto](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Esempio
 Questo esempio mostra una radice multiprogetto semplice *vstemplate* file. In questo esempio, il modello contiene due progetti `My Windows Application` e `My Class Library`. L'attributo `ProjectName` nell'elemento `ProjectTemplateLink` imposta il nome per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da assegnare a questo progetto. Se il `ProjectName` attributo non esiste, il nome del *vstemplate* file viene usato come nome del progetto.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: Creare modelli multiprogetto](../ide/how-to-create-multi-project-templates.md)