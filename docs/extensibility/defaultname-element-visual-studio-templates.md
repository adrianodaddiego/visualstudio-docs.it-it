---
title: Elemento DefaultName (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dbb720bf04c36b2d9f018be5418a25088e259f4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348158"
---
# <a name="defaultname-element-visual-studio-templates"></a>Elemento DefaultName (modelli di Visual Studio)
Specifica il nome che verrà generato il sistema di progetto di Visual Studio per il progetto o un elemento al momento della creazione.

 \<VSTemplate> \<TemplateData> \<DefaultName>

## <a name="syntax"></a>Sintassi

```
<DefaultName>
    Default Project Name
</DefaultName>
```

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

 Tale testo specifica il nome predefinito del progetto o elemento.

## <a name="remarks"></a>Note
 `DefaultName` è un elemento facoltativo.

 Per i progetti, questo elemento specifica il nome della directory di cui è archiviato il progetto su disco. Per gli elementi, specifica il nome del file del file di origine.

 Quando si crea un progetto o un elemento, è possibile modificare il nome predefinito usando il **nome** opzione, che è disponibile dal **nuovo progetto** la finestra di dialogo o **Aggiungi nuovo elemento** finestra di dialogo.

 Se non si desidera il sistema di progetto per generare il nome predefinito per il progetto o un elemento, quindi impostare il [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) elemento `False`.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per il modello di elementi standard per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)