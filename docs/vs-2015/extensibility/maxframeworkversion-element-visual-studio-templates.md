---
title: Elemento MaxFrameworkVersion (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968710"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica la versione massima di .NET Framework richiesto dal modello. Determina se il modello viene visualizzato nel **modelli** sezione del **Aggiungi nuovo progetto** della finestra di dialogo in base al valore selezionato nel **versioneFrameworkdidestinazione** finestra di **Aggiungi nuovo progetto** nella finestra di dialogo.  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce come viene visualizzato in entrambi i **nuovo progetto** o il **Aggiungi nuovo elemento** nella finestra di dialogo.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere il più alto numero di versione di .NET Framework che è consentito dal modello.  
  
## <a name="remarks"></a>Note  
 `MaxFrameworkVersion` è un elemento facoltativo. L'elemento nel `TemplateData` sezione del file con estensione vstemplate funge da filtro per il **modelli** sezione del **Aggiungi nuovo progetto** nella finestra di dialogo. Solo i modelli con requisiti di .NET Framework minore di `MaxFrameworkVersion` i valori degli elementi verranno visualizzati in base al valore selezionato nel **versione Framework di destinazione** finestra di **Aggiungi nuovo progetto**finestra di dialogo. Il `MaxFrameworkVersion` elemento deve essere omesso solo se necessario, per non causare inavvertitamente modelli venga visualizzata quando vengono usati con le versioni più recenti di .NET Framework.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati di un controllo standard [!INCLUDE[csprcs](../includes/csprcs-md.md)] modello di classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 In questo esempio, la versione massima di .NET Framework richiesto dal modello, rappresentato da `MaxFrameworkVersion`, è 3.5. Il modello precedente verrà visualizzato solo quando si seleziona 3.0 o 3.5 nel **versione Framework di destinazione** nella casella il **Aggiungi nuovo progetto** nella finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
