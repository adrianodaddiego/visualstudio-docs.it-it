---
title: Elemento ProvideDefaultName (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bd18dd979436b02cc12a4dab5439bdb5f371e2d
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "58970397"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Elemento ProvideDefaultName (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica se il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sistema di progetto verrà generato un nome predefinito per il modello nella **Aggiungi nuovo elemento** o **nuovo progetto** nella finestra di dialogo.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProvideDefaultName>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 Il testo deve essere `true` o `false`, che indica se generare un nome predefinito per il modello nella o meno la **Aggiungi nuovo elemento** o **nuovo progetto** nella finestra di dialogo.  
  
## <a name="remarks"></a>Note  
 `ProvideDefaultName` è un elemento facoltativo. Il valore predefinito è `true`.  
  
 Se il `ProvideDefaultName` elemento viene `false`, il **nome** caselle del **Aggiungi nuovo elemento** e **nuovo progetto** finestre di dialogo contengono il valore `<Enter_name>`.  
  
 Usare il [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) elemento per specificare il nome predefinito del progetto o elemento il **Aggiungi nuovo elemento** e **nuovo progetto** finestre di dialogo.  
  
## <a name="example"></a>Esempio  
 I seguente esempio di codice impostare il `ProvideDefaultName` elemento `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
