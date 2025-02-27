---
title: Modello di Visual Studio Manifest Schema Reference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a421986e076d2badc6dc7eb76247d243da155b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323020"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Riferimento dello schema del manifesto di modello di Visual Studio
Questo schema viene descritto il formato del manifesto del modello di Visual Studio (*con estensione vstman*) i file che vengono generati per i modelli di progetto o un elemento di Visual Studio. Lo schema descrive anche la posizione e altre informazioni rilevanti relative al modello.

 : Poiché esistono elemento separato e le directory di progetto, un manifesto mai deve avere una combinazione di modelli di progetto ed elemento.

> [!IMPORTANT]
> Questo manifesto è disponibile a partire da Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest
 L'elemento radice del manifesto.

### <a name="attributes"></a>Attributi

- **Versione**: Stringa che rappresenta la versione del manifesto del modello. Obbligatorio.

- **Impostazioni locali**: Stringa che rappresenta le impostazioni locali o impostazioni locali del manifesto del modello. Il valore delle impostazioni locali si applica a tutti i modelli. È necessario usare un manifesto separato per ogni impostazione locale. Facoltativo.

### <a name="child-elements"></a>Elementi figlio

- **VSTemplateContainer** facoltativo.

- **VSTemplateDir** facoltativo.

### <a name="parent-element"></a>Elemento padre
 Nessuno.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Il contenitore del modello di manifesto elementi. Un contenitore di modello per ogni modello che definisce un manifesto.

### <a name="attributes"></a>Attributi
 **VSTemplateType**: Valore stringa che specifica il tipo del modello (`"Project"`, `"Item"`, o `"ProjectGroup"`). Obbligatorio

### <a name="child-elements"></a>Elementi figlio

- **RelativePathOnDisk**:  Il percorso relativo del file del modello su disco. Questo percorso definisce anche la posizione del modello nell'albero del modello illustrato nella **nuovo progetto** oppure **nuovo elemento** finestra di dialogo. Per i modelli distribuiti come una directory e i singoli file, questo percorso fa riferimento alla directory contenente i file di modello. Per i modelli distribuiti come un *zip* file, questo percorso deve essere il percorso per il *zip* file.

- **VSTemplateHeader: Oggetto [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento che descrive l'intestazione.

### <a name="parent-element"></a>Elemento padre
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Descrive la directory in cui si trova il modello. Un manifesto può contenere più **VSTemplateDir** voci per fornire nome localizzato e ordinamento per le directory di ordinamento per determinarne l'aspetto di albero delle categorie di modello.

 A causa di un progetto, **VSTemplateDir** voci devono essere visualizzato solo nei manifesti specificati non locali.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

- **RelativePath**: Il percorso del modello. Può esistere solo una voce per ogni percorso, il primo avrà la precedenza per tutti i manifesti.

- **LocalizedName**: Oggetto **NameDescriptionIcon** elemento che specifica il nome localizzato. Facoltativo.

- **SortOrder**: Stringa che specifica l'ordinamento. Facoltativo.

- **ParentFolderOverrideName**: Nome stato eseguito l'override della cartella padre. Facoltativo. Questo elemento dispone di un **nome** attributo, ovvero un valore stringa che specifica il nome.

### <a name="parent-element"></a>Elemento padre
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Specifica il nome e descrizione, possibilmente per i modelli localizzati. Visualizzare **LocalizedName** sopra.

### <a name="attributes"></a>Attributi

- **Pacchetto**: Valore stringa che specifica il pacchetto. Facoltativo.

- **ID**: Valore stringa che specifica l'ID. Facoltativo.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-element"></a>Elemento padre
 **LocalizedName**

## <a name="examples"></a>Esempi
 Il codice seguente è un esempio di un modello di progetto *con estensione vstman* file.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Il codice seguente è un esempio di un modello di elemento *con estensione vstman* file.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```
