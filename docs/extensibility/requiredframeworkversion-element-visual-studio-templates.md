---
title: Elemento RequiredFrameworkVersion (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77bc25ec831241a87782fc6628fba2ab8e7fa0e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334200"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Elemento RequiredFrameworkVersion (modelli di Visual Studio)

Specifica la versione minima di .NET Framework richiesto dal modello. Si verifica il **versione Framework di destinazione** elenco a discesa da visualizzare nella **nuovo progetto** finestra di dialogo. Il `RequiredFrameworkVersion` elemento determina anche il valore più basso disponibile nell'elenco a discesa.

> [!IMPORTANT]
> A partire da Visual Studio 2017 versione 15.6, il **versione Framework di destinazione** elenco a discesa non è più un filtro per i modelli visualizzati nel **modelli** sezione del **nuovo progetto** finestra di dialogo. Al contrario, l'elenco a discesa funziona come un selettore di framework per il modello selezionato.

 \<VSTemplate > \<TemplateData > \<RequiredFrameworkVersion >

## <a name="syntax"></a>Sintassi

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Il testo deve essere il numero di versione minima di .NET Framework che è necessario per il modello.

## <a name="remarks"></a>Note

`RequiredFrameworkVersion` è un elemento facoltativo. Usare questo elemento solo se il modello supporta una versione minima specifica (e versioni successive, se presente) di .NET Framework. Se si specifica la `RequiredFrameworkVersion` elemento e il modello non supporta una versione minima specifica di .NET Framework, il **versione Framework di destinazione** elenco a discesa viene visualizzato quando non è applicabile.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati i metadati di un controllo standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modello di classe.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

In questo esempio, la versione minima di .NET Framework che viene richiesto dal modello, rappresentato da `RequiredFrameworkVersion`, sia 3.0. Un progetto creato con questo modello può avere come destinazione versioni di .NET Framework a partire da 3.0.

## <a name="see-also"></a>Vedere anche

- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Una versione specifica di .NET Framework di destinazione](../ide/visual-studio-multi-targeting-overview.md)
