---
title: '&lt;RelatedProducts&gt; elemento (programma di avvio automatico) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70afe724be5b782bc90e162fd65f83ad1b0d0d23
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968717"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; elemento (programma di avvio automatico)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il `RelatedProducts` elemento definisce gli altri prodotti dipendono o sono inclusi nel prodotto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `RelatedProducts` elemento è figlio di `Product` elemento. Non dispone di attributi.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 Il `DependsOnProduct` elemento indica che il prodotto corrente dipende dal prodotto specificato e che il prodotto deve essere installato prima di quello corrente. È un figlio di `RelatedProducts` elemento. Oggetto `RelatedProducts` elemento può contenere uno o più `DependsOnProduct` elementi.  
  
 `DependsOnProduct` ha l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Code`|Il nome del prodotto incluso, come specificato dal codice il `ProductCode` attributo del `Product` elemento. Per altre informazioni, vedere [ \<prodotto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 Il `EitherProducts` elemento definisce zero o più `DependsOnProduct` elementi, e non include attributi. Almeno un `DependsOnProduct` in questo set deve essere installato prima del prodotto corrente. Oggetto `RelatedProducts` può contenere zero o più `EitherProducts` elementi.  
  
## <a name="includesproduct"></a>IncludesProduct  
 Il `IncludesProduct` elemento indica che un prodotto sia incluso nell'installazione corrente e non richiede un'installazione separata. È un figlio di `RelatedProducts` elemento. Oggetto `RelatedProducts` elemento può contenere uno o più `IncludesProduct` elementi.  
  
 `IncludesProduct` ha l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Code`|Il nome del prodotto incluso, come specificato dal codice il `ProductCode` attributo del `Product` elemento. Per altre informazioni, vedere [ \<prodotto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente specifica che sia installato Microsoft Installer con la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]e pertanto non richiede un'installazione separata.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<Product> Element](../deployment/product-element-bootstrapper.md)
