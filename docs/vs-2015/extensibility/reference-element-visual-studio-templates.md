---
title: Fare riferimento all'elemento (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3d67fd19122e160159a6f636516dbca582fe31d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968796"
---
# <a name="reference-element-visual-studio-templates"></a>Elemento Reference (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Riferimenti a >  
 \<Riferimento >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica le informazioni relative a un assembly, che usa il modello per aggiungere un riferimento dell'assembly per i progetti. Deve essere presente un `Assembly` elemento in ogni `Reference` elemento.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Riferimenti](../extensibility/references-element-visual-studio-templates.md)|Raggruppa i riferimenti all'assembly che il modello aggiunge ai progetti.|  
  
## <a name="remarks"></a>Note  
 `Reference` è un elemento figlio obbligatorio di `References`.  
  
 Il `Reference` e `References` elementi possono essere utilizzati solo nei file con estensione vstemplate che hanno una `Type` valore dell'attributo `Item`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il `TemplateContent` elemento di un modello di elemento. Questo file XML vengono aggiunti riferimenti agli assembly System. dll e System.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
