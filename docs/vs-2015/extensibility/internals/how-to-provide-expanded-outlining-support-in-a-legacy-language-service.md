---
title: 'Procedura: Fornire supporto per la struttura espanso in un servizio di linguaggio Legacy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1b2fd8f3d7e4f3637957ef11c4acb20ba51261d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442669"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Procedura: Offrire il supporto per la struttura espansa in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sono disponibili due opzioni per l'estensione di supporto per la struttura per il linguaggio oltre, supportando il **Comprimi alle definizioni** comando. È possibile aggiungere aree della struttura controllata dall'editor e aggiungere aree della struttura controllato dal client.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Aggiunta di aree della struttura controllata dall'Editor  
 Usare questo approccio per creare un'area della struttura e quindi consentire all'editor di gestire se l'area viene espanso, compresso e così via. Delle due opzioni per fornire supporto per la struttura, questa opzione è meno solida. Per questa opzione, si crea una nuova area della struttura in un intervallo specificato di testo tramite <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Dopo la creazione di quest'area, il comportamento è controllato dall'editor. Usare la procedura seguente per implementare aree della struttura controllata dall'editor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Per implementare un'area della struttura controllata dall'editor  
  
1. Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Restituisce un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato. Restituisce un puntatore al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> oggetto per il buffer.  
  
3. Chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> sul <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> per un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> per aggiungere uno o più nuovi descrive le aree contemporaneamente.  
  
     Questo metodo consente di specificare l'intervallo di testo per struttura, se aree della struttura esistenti vengono rimosse o mantenute e se l'area della struttura è espansa o compressa per impostazione predefinita.  
  
## <a name="adding-client-controlled-outline-regions"></a>Aggiunta di aree della struttura controllato dal Client  
 Usare questo approccio per la struttura di implementare controllato dal client (o intelligente) simile a quella usata per il [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] servizi di linguaggio. Un servizio di linguaggio che gestisce la propria struttura consente di monitorare il contenuto del buffer di testo per distruggere aree della struttura precedente quando è più valida e creare nuove aree della struttura in base alle esigenze.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Per implementare un'area della struttura controllato dal client  
  
1. Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Restituisce un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato. Determina se esiste già una sessione di testo nascosto per il buffer.  
  
3. Se esiste già una sessione di testo, quindi non è necessaria creare uno e un puntatore esistente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito l'oggetto. Utilizzare questo puntatore per enumerare e creano aree della struttura. In caso contrario, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> per creare una sessione di testo nascosto per il buffer. Un puntatore al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito l'oggetto.  
  
    > [!NOTE]
    > Quando si chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, è possibile specificare un client di testo nascosto (vale a dire un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> oggetto). Il client invia una notifica quando un testo nascosto o area della struttura è espanso o compresso dall'utente.  
  
4. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> struttura) parametro: Specificare il valore <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> nella `iType` membro del <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura per indicare che si sta creando un'area della struttura, anziché un'area nascosta. Specificare se l'area è controllato dal client o dall'editor nel `dwBehavior` membro del <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura. L'implementazione della struttura intelligente può contenere una combinazione di aree della struttura dell'editor e controllato dal client. Specificare il testo dell'intestazione visualizzato quando l'area della struttura è compressa, ad esempio "...", nelle `pszBanner` membro del <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura. Testo dell'intestazione dell'editor predefinita per un'area nascosta è "...".
