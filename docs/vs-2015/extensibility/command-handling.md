---
title: La gestione dei comandi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968899"
---
# <a name="command-handling"></a>Gestione dei comandi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor è possibile definire nuovi comandi. I comandi vengono in genere visualizzati in un menu, in una barra degli strumenti o in un menu di scelta rapida.  
  
 Per altre informazioni sulla definizione dei comandi e menu, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un servizio di linguaggio è possibile controllare il menu di scelta rapida vengono visualizzati nell'editor, mediante l'intercettazione di <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumerazione. In alternativa, è possibile controllare il menu di scelta rapida in base al marcatore. Per altre informazioni, vedere [comandi importanti per i filtri dei servizi di linguaggio](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Aggiunta di comandi a menu di scelta rapida Editor  
 Per aggiungere un comando di menu di scelta rapida, è innanzitutto necessario definire un set di comandi di menu che appartengono a un gruppo specifico. L'esempio seguente è tratto dal file con estensione vsct generato come parte della procedura dettagliata [procedura dettagliata: Aggiunta di funzionalità in un Editor personalizzato](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Guid padre = "guidCustomEditorCmdSet" id = "0" / >  
  
 \<Le stringhe >  
  
 \<ButtonText > menu di scelta rapida di CustomEditor\</ButtonText >  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</ Stringhe di >  
  
 \</Menu>  
  
 \</Menus>  
  
 Il testo precedente aggiunge un comando di menu di scelta rapida con il testo **menu di scelta rapida CustomEditor**. Il GUID del menu di scelta è che del set di comandi che viene creato con questo editor e il tipo è "Context".  
  
 È anche possibile usare i comandi predefiniti che non devono essere definiti nel file con estensione vsct. Ad esempio, se si esamina il file EditorPane.cs generato dal modello di pacchetto di Visual Studio, è trovare che un set di comandi predefiniti, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definito da <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, vengono gestiti nei gestori di comando, ad esempio il metodo onSelectAll.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
