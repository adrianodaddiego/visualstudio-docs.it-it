---
title: Elemento ProjectItem (modelli di progetto di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84fb371460bc697660e176ca9df4c984d2b234bf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438365"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Elemento ProjectItem (modelli di progetto Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica un file che viene incluso nel modello di progetto.  
  
> [!NOTE]
> Il `ProjectItem` elemento accetta attributi diversi a seconda che il modello sia per un progetto o un elemento. Questo argomento viene illustrato il `ProjectItem` (elemento) per i modelli di progetto. Per una spiegazione delle `ProjectItem` (elemento) per modelli di elementi, vedere [elemento ProjectItem (elemento modelli di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Project>  
 \<ProjectItem >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`TargetFileName`|Attributo facoltativo.<br /><br /> Specifica il nome e percorso dell'elemento del progetto quando viene creato un progetto dal modello. Questo attributo è utile per la creazione di una struttura di directory diversa dalla struttura di directory nel file zip del modello o per l'uso di sostituzione dei parametri per creare un nome di elemento.|  
|`ReplaceParameters`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento contiene i valori dei parametri devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`.|  
|`OpenInEditor`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperta nel rispettivo editor in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] quando viene creato un progetto dal modello.<br /><br /> Il `OpenInWebBrowser` e `OpenInHelpBrowser` vengono ignorati in un elemento con un `OpenInEditor` valore `true`.<br /><br /> Il valore predefinito è `false`.|  
|`OpenInWebBrowser`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto il browser Web quando viene creato un progetto dal modello.<br /><br /> Solo i file di testo che sono locali rispetto al progetto e file HTML possono essere aperto nel browser Web. Impossibile aprire gli URL esterni con questo attributo.<br /><br /> Il valore predefinito è `false`.|  
|`OpenInHelpBrowser`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento deve essere aperto nel Visualizzatore della Guida quando viene creato un progetto dal modello.<br /><br /> Solo i file di testo che sono locali rispetto al progetto e file HTML possono essere aperto nel Visualizzatore della Guida. Impossibile aprire gli URL esterni con questo attributo.<br /><br /> Il valore predefinito è `false`.|  
|`OpenOrder`|Attributo facoltativo.<br /><br /> Specifica un valore numerico che rappresenta l'ordine che verranno aperto gli elementi nei rispettivi editor. Tutti i valori devono essere multipli di 10. Gli elementi con versioni successive `OpenOrder` aperti prima di tutto i valori.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Progetto](../extensibility/project-element-visual-studio-templates.md)|Specifica il file o directory da aggiungere al progetto.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Oggetto `string` che rappresenta il nome o il percorso in un file nel file zip del modello.  
  
## <a name="remarks"></a>Note  
 `ProjectItem` è un elemento figlio facoltativo di `Project`.  
  
 Il `TargetFileName` attributo può essere utilizzato per creare una struttura di directory diversa dalla struttura di directory nel file zip del modello. Ad esempio, se il file `MyFile.vb` presente nella radice del file zip del modello, ma si vuole che il file da inserire in una directory denominata `CustomFiles` in tutti i progetti creati dal modello, si utilizzerebbe il codice XML seguente:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 Il `TargetFileName` attributo può essere utilizzato anche per rinominare i file che contengono caratteri internazionali nei loro nomi di file. Ad esempio, un file con estensione zip modello non può contenere nomi di file con caratteri Unicode, in modo che il file deve essere rinominato prima che possono essere compresse in un file ZIP. Il `TargetFileName` attributo può essere utilizzato per impostare il nome del file con il nome di file Unicode originale.  
  
 Il `TargetFileName` attributo può essere utilizzato anche per rinominare i file con i parametri. La procedura seguente illustra come rinominare il file `MyFile.vb`, che esiste nella directory radice del file con estensione zip modello, da un nome di file basato sul nome del progetto.  
  
### <a name="to-rename-files-with-parameters"></a>Per rinominare i file con parametri  
  
1. Usare il codice XML seguente nel file vstemplate:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2. Aprire il file di progetto (con estensione vbproj per un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] progetto) in un editor di testo o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3. Individuare la riga nel file di progetto che ha un aspetto simile al codice XML seguente:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4. Sostituire la riga di codice con il codice XML seguente:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Quando viene creato un progetto da questo modello, il nome del file si baseranno sul nome utente specificato nella **nuovo progetto** finestra di dialogo, con tutti i caratteri non sicuri e gli spazi rimossi. Per altre informazioni, vedere [parametri di modello](../ide/template-parameters.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra i metadati per un modello di progetto per un [!INCLUDE[csprcs](../includes/csprcs-md.md)] dell'applicazione.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
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
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Parametri di modello](../ide/template-parameters.md)   
 [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
