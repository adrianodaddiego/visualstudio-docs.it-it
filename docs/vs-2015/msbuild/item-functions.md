---
title: Funzioni degli elementi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c94624aaea629c087b552ee46266a44f534888d5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670264"
---
# <a name="item-functions"></a>Funzioni degli elementi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partire da MSBuild 4.0, il codice nelle attività e nelle destinazioni è in grado di chiamare le funzioni di elementi per ottenere informazioni sugli elementi del progetto. Queste funzioni semplificano l'acquisizione di elementi Distinct() e sono più veloci rispetto allo scorrimento in ciclo degli elementi.  
  
## <a name="string-item-functions"></a>Funzioni degli elementi per i valori stringa  
 È anche possibile usare metodi e proprietà di stringa in .NET Framework per operare su qualsiasi valore dell'elemento. Per i metodi <xref:System.String>, specificare il nome del metodo. Per le proprietà <xref:System.String>, specificare il nome della proprietà dopo "get_".  
  
 Per gli elementi con più stringhe, è necessario eseguire il metodo o la proprietà di stringa per ogni stringa.  
  
 Nell'esempio seguente viene illustrato come usare le funzioni degli elementi per i valori stringa.  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## <a name="intrinsic-item-functions"></a>Funzioni intrinseche degli elementi  
 Nella tabella seguente sono elencate le funzioni intrinseche disponibili per gli elementi.  
  
|Funzione|Esempio|Description|  
|--------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Restituisce il numero di elementi.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Restituisce l'equivalente di `Path.DirectoryName` per ogni elemento.|  
|`Distinct`|`@(MyItem->Distinct())`|Restituisce gli elementi con valori `Include` distinti. I metadati vengono ignorati. Nel confronto non viene fatta distinzione tra maiuscole e minuscole.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Restituisce gli elementi con valori `itemspec` distinti. I metadati vengono ignorati. Per il confronto viene applicata la distinzione tra maiuscole e minuscole.|  
|`Reverse`|`@(MyItem->Reverse())`|Restituisce gli elementi in ordine inverso.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Restituisce `boolean` per indicare se un elemento ha il valore e il nome dei metadati specificati. Nel confronto non viene fatta distinzione tra maiuscole e minuscole.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Restituisce gli elementi con i metadati cancellati. Viene mantenuto solo `itemspec`.|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Restituisce gli elementi con il nome dei metadati specificato. Nel confronto non viene fatta distinzione tra maiuscole e minuscole.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Restituisce i valori dei metadati con il nome dei metadati specificato.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Restituisce gli elementi con il nome e il valore dei metadati specificati. Nel confronto non viene fatta distinzione tra maiuscole e minuscole.|  
  
 Nell'esempio seguente viene illustrato come usare le funzioni intrinseche degli elementi.  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi](../msbuild/msbuild-items.md)
