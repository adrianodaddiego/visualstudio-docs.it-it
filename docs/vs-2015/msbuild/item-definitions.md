---
title: Definizioni degli elementi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7097311c3d1aae718096c3bf74ec04c3e5ea8818
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433581"
---
# <a name="item-definitions"></a>Definizioni degli elementi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 consente la dichiarazione statica di elementi nei file di progetto mediante l'elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md). I metadati possono essere tuttavia aggiunti solo al livello dell'elemento, anche se sono identici per tutti gli elementi. A partire da [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, è stato introdotto un elemento di progetto denominato [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) che consente di superare questa limitazione. *ItemDefinitionGroup* consente di definire un set di definizioni degli elementi che aggiungono i valori dei metadati predefiniti a tutti gli elementi del tipo di elemento denominato.  
  
 L'elemento *ItemDefinitionGroup* viene visualizzato immediatamente dopo l'elemento [Project](../msbuild/project-element-msbuild.md) nel file di progetto. Le definizioni degli elementi offrono le funzionalità seguenti:  
  
- È possibile definire metadati predefiniti globali per gli elementi all'esterno di una destinazione. In altri termini, gli stessi metadati si applicano a tutti gli elementi del tipo specificato.  
  
- I tipi di elemento possono presentare più definizioni. Quando al tipo vengono aggiunte altre specifiche di metadati, l'ultima ha la precedenza. \(I metadati seguono lo stesso ordine di importazione delle proprietà.\)  
  
- I metadati possono essere additivi. Ad esempio, i valori CDefines vengono accumulati in modo condizionale, a seconda delle proprietà impostate. Ad esempio `MT;STD_CALL;DEBUG;UNICODE`.  
  
- I metadati possono essere rimossi.  
  
- È possibile usare condizioni per controllare l'inclusione di metadati.  
  
## <a name="item-metadata-default-values"></a>Valori predefiniti dei metadati degli elementi  
 I metadati degli elementi definiti in un ItemDefinitionGroup sono solo una dichiarazione di metadati predefiniti. I metadati non vengono applicati a meno che non sia definito un elemento che usa un ItemGroup per contenere i valori dei metadati.  
  
> [!NOTE]
> In molti degli esempi riportati in questo argomento viene illustrato un elemento ItemDefinitionGroup, ma la definizione di ItemGroup corrispondente viene omessa per chiarezza.  
  
 I metadati definiti in modo esplicito in un ItemGroup hanno la precedenza su quelli presenti in ItemDefinitionGroup. I metadati presenti in ItemDefinitionGroup vengono applicati solo per i metadati non definiti in un ItemGroup. Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 In questo esempio il metadato predefinito "m" viene applicato all'elemento "i" perché non è definito in modo esplicito dall'elemento "i". Al contrario, il metadato predefinito "n" non viene applicato all'elemento "i" perché è già definito dall'elemento "i".  
  
> [!NOTE]
> I nomi di parametri ed elementi XML prevedono la distinzione tra maiuscole e \-minuscole. I metadati degli elementi e i \/nomi di proprietà o elementi non prevedono tale \-distinzione. Di conseguenza, gli elementi ItemDefinitionGroup i cui nomi differiscono solo per l'uso di maiuscole o minuscole devono essere considerati come lo stesso ItemGroup.  
  
## <a name="value-sources"></a>Origini dei valori  
 I valori per i metadati definiti in un ItemDefinitionGroup possono provenire da molte origini diverse, come indicato di seguito:  
  
- Proprietà PropertyGroup  
  
- Elemento da un ItemDefinitionGroup  
  
- Trasformazione dell'elemento in un elemento ItemDefinitionGroup  
  
- Variabile di ambiente  
  
- Proprietà globale \(dalla riga di comando di MSBuild.exe\)  
  
- Proprietà riservata  
  
- Metadati noti in un elemento di un ItemDefinitionGroup  
  
- Sezione CDATA \<\!\[CDATA\[nessun dato analizzato\]\]\>  
  
> [!NOTE]
> I metadati degli elementi di un ItemGroup non sono utili in una dichiarazione di metadati di un ItemDefinitionGroup perché gli elementi dell'ItemDefinitionGroup vengono elaborati prima di quelli dell'ItemGroup.  
  
## <a name="additive-and-multiple-definitions"></a>Definizioni additive e multiple  
 Quando si aggiungono definizioni o si usano più ItemDefinitionGroup, tenere presente quanto segue:  
  
- Eventuali altre specifiche dei metadati vengono aggiunte al tipo.  
  
- L'ultima specifica ha la precedenza.  
  
  In presenza di più ItemDefinitionGroup, ogni specifica successiva aggiunge i metadati alla definizione precedente. Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 In questo esempio il metadato "o" viene aggiunto a "m" e "n".  
  
 È anche possibile aggiungere i valori dei metadati definiti in precedenza. Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
 In questo esempio il valore definito in precedenza per il metadato "m" \(m1\) viene aggiunto al nuovo valore \(m2\), in modo che il valore finale sia "m1;m2".  
  
> [!NOTE]
> Questo può verificarsi anche nello stesso ItemDefinitionGroup.  
  
 Quando si esegue l'override dei metadati definiti in precedenza, l'ultima specifica ha la precedenza. Nell'esempio seguente il valore finale del metadato "m" è compreso tra "m1" e "m1a".  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## <a name="using-conditions-in-an-itemdefinitiongroup"></a>Uso delle condizioni in un ItemDefinitionGroup  
 È possibile usare condizioni in un ItemDefinitionGroup per controllare l'inclusione dei metadati. Ad esempio:  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 In questo caso, il metadato predefinito "m1" dell'elemento "i" viene incluso solo se il valore della proprietà "Configuration" è "Debug".  
  
> [!NOTE]
> Nelle condizioni sono supportati solo i riferimenti ai metadati locali.  
  
 I riferimenti ai metadati definiti in un ItemDefinitionGroup precedente sono locali per l'elemento, non per il gruppo di definizione. In altre parole, l'ambito dei riferimenti è specifico dell'elemento. Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i>  
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 In questo esempio l'elemento "i" fa riferimento all'elemento "test" nella condizione.  
  
## <a name="overriding-and-deleting-metadata"></a>Override ed eliminazione di metadati  
 È possibile eseguire l'override dei metadati definiti in un elemento ItemDefinitionGroup in un elemento ItemDefinitionGroup successivo lasciando vuoto il valore dei metadati. È anche possibile eliminare un elemento dei metadati impostandolo su un valore vuoto. Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 L'elemento "i" contiene ancora il metadato "m", ma ora il valore è vuoto.  
  
## <a name="scope-of-metadata"></a>Ambito dei metadati  
 Gli ItemDefinitionGroup hanno un ambito globale su proprietà definite e globali, ovunque siano definite. Le definizioni dei metadati predefiniti in un ItemDefinitionGroup possono essere autoreferenziali. Ad esempio, di seguito viene usato un riferimento ai metadati semplice:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 È possibile usare anche un riferimento ai metadati qualificato:  
  
```  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Quanto segue, tuttavia, non è valido:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 A partire da [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, anche gli ItemGroup possono essere autoreferenziali. Ad esempio:  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Batch MSBuild](../msbuild/msbuild-batching.md)
