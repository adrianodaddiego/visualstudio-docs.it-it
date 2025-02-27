---
title: Elemento ProjectTemplateLink (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6ee9f5d4a162f994cfea4fb3fe620599c1627b3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681322"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Elemento ProjectTemplateLink (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica il percorso del file .vstemplate di un progetto in un modello multiprogetto.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
 \<ProjectTemplateLink>  
-oppure-  
\<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
 \<SolutionFolder>  
 \<ProjectTemplateLink>  
  
## <a name="syntax"></a>Sintassi  
  
```  
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
|`CopyParameters`|Consente la copia di tutte le variabili nel modello del gruppo centrale in ognuno dei modelli collegati.<br /><br /> I parametri nei modelli collegati dispongono del prefisso `"$ext_*$"`. Ad esempio, se nel modello del gruppo padre il parametro `$projectname$` ha un valore **ExampleProject1**, quando il modello collegato Ottiene il proprio turno per essere eseguito, acquisisce un parametro `$ext_projectname$`, ovvero una copia del `$projectname$`parametro di modello del gruppo padre.<br /><br /> In questo modo i modelli collegati possono condividere alcuni parametri comuni, che possono essere facilmente creati solo nel modello del gruppo padre.<br /><br /> Questo attributo è facoltativo ed è automaticamente impostato su `false` quando non è incluso.<br /><br /> Introdotto in Visual Studio 2013 Update 2. Per correlare la versione corretta del prodotto, vedere [che fanno riferimento a recapitare gli assembly in Visual Studio 2013 SDK Update 2](https://msdn.microsoft.com/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Raggruppa i progetti in modelli multiprogetto.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Questo testo specifica il percorso del file .vstemplate del modello.  
  
## <a name="remarks"></a>Note  
 I modelli multiprogetto fungono da contenitori per due o più progetti. L'elemento `ProjectTemplateLink` viene usato per specificare il percorso del file .vstemplate per uno dei progetti presenti nel modello. Il file .vstemplate di un modello multiprogetto contiene un elemento `ProjectTemplateLink` per ciascun progetto presente nel modello. Per altre informazioni sui modelli multiprogetto, vedere [come: Creare modelli multiprogetto](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene mostrato un file .vstemplate radice multiprogetto semplice. In questo esempio, il modello contiene due progetti `My Windows Application` e `My Class Library`. L'attributo `ProjectName` nell'elemento `ProjectTemplateLink` imposta il nome per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] da assegnare a questo progetto. Se l'attributo `ProjectName` non esiste, per il nome del progetto verrà usato il nome del file .vstemplate.  
  
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
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare modelli per più progetti](../ide/how-to-create-multi-project-templates.md)
