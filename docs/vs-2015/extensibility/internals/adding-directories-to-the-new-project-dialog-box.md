---
title: Aggiunta di directory per la finestra di dialogo Nuovo progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955636"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Aggiunta di directory nella finestra di dialogo Nuovo progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando si creano nuovi tipi di progetto, è anche possibile registrare una nuova directory nel **nuovo progetto** finestra di dialogo per la visualizzazione per l'uso come modelli. Esempio di codice seguente illustra come registrare una nuova directory, noto anche come un nodo. Nell'esempio vengono registrati modelli esposti dal VSPackage CLSID_Package. Di conseguenza, il lato sinistro della **nuovo progetto** nella finestra di dialogo offre il nodo aggiunto, con un nome stabilito dalla risorsa Folder_Label_ResID. Questa risorsa verrà caricata della DLL satellite di VSPackage.  
  
 Il **cartella** valore rappresenta un GUID di una cartella in cui viene visualizzato il nodo Folder_Label_ResID. Nell'esempio, rappresenta il GUID il **altri progetti** cartella il **tipi di progetto** riquadro del **nuovo progetto** nella finestra di dialogo. Se il **altri progetti** valore è assente, l'etichetta viene posizionata nella parte superiore.  
  
 Il valore TemplatesDir specifica il percorso completo della directory che contiene i modelli di progetto. Questi file possono essere file con estensione vsz o file di modello tipico per la clonazione.  
  
 Se si specifica TemplatesLocalizedSubDir, deve essere l'ID risorsa della stringa che denomina la sottodirectory della TemplatesDir che contiene i modelli localizzati. Poiché [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] carica la risorsa stringa da una DLL satellite se presente, ogni DLL satellite può contenere un nome di sottodirectory diverse. Il valore SortPriority specifica una priorità di ordinamento.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Aggiunta di directory nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
