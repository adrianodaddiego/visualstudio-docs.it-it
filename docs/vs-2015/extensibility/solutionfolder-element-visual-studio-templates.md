---
title: Elemento SolutionFolder (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84d0c1765a14f60363b71fcdec182d448cb4f112
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969918"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>Elemento SolutionFolder (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Raggruppa i progetti in modelli multiprogetto.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
 \<SolutionFolder>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<SolutionFolder Name="DirectoryName">  
    ...  
</SolutionFolder>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Attributo obbligatorio.<br /><br /> Nome della cartella della soluzione.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica il percorso del file .vstemplate di un progetto in un modello multiprogetto.|  
|`SolutionFolder`|Elemento facoltativo.<br /><br /> Raggruppa i progetti in modelli multiprogetto.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|  
|`SolutionFolder`|Raggruppa i progetti in modelli multiprogetto.|  
  
## <a name="remarks"></a>Note  
 I modelli multiprogetto fungono da contenitori per due o più progetti. L'elemento `SolutionFolder` viene usato per organizzare i progetti in gruppi all'interno del modello. Le cartelle specificate dagli elementi `SolutionFolder` vengono create come cartelle della soluzione nel progetto in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni sui modelli multiprogetto, vedere [come: Creare modelli multiprogetto](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Esempio  
 Questo esempio usa l'elemento `SolutionFolder` per dividere il modello multiprogetto in due gruppi, `Math Classes` e `Graphics Classes`. Il modello contiene quattro progetti, due dei quali vengono inseriti in ogni cartella della soluzione.  
  
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
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare modelli per più progetti](../ide/how-to-create-multi-project-templates.md)
