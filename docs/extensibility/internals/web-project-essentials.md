---
title: Web Essentials progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ddc8bcef8612459ce9816e79250ba8b93194292
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323305"
---
# <a name="web-project-essentials"></a>Nozioni fondamentali sui progetti Web
I progetti Web creare applicazioni Web. È possibile usare un progetto Web per creare un'applicazione Web che è costituito da pagine Web intelligente. Una pagina Web smart dispone di codice lato server che esegue il rendering della pagina Web richiesta.

 Usando linguaggi di programmazione tradizionali, ad esempio [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], è possibile creare pagine Web intelligente per raccogliere ed elaborare informazioni dall'utente, archiviarlo in un database e così via.

- Il modello code-behind Associa file di codice sorgente dipendente a pagine Web con il file estensione aspx o asmx. Aspx sono ad esempio, potrebbe essere il hello.aspx.cs di file di codice sorgente dipendente.

- Il codice lato server associato a una pagina Web intelligente viene compilato in un file eseguibile che si trova nella cartella /bin sito Web.

- File di codice di origine aggiuntivi, ad esempio classi helper che non sono associati a una pagina Web specifica, si trovano nella cartella /App_Code sito Web.

  - Un progetto di sito Web (WSP) genera un file eseguibile per ogni pagina Web intelligente. File eseguibile aggiuntivi vengono generati da qualsiasi file di codice sorgente nella cartella /App_Code.

  - Un progetto di applicazione Web (WAP) produce un unico file eseguibile che combina il codice per tutte le pagine Web intelligente, nonché tutti i file di origine nella cartella /App_Code.

- Trova il file di soluzione per un progetto Web separatamente dal sito Web stesso. Per impostazione predefinita, i file della soluzione si trovano in \Documents and Settings\\*AccountUtente*documenti \My\\ *\<Visual Studio # # # >* \Projects\\ *YourWebSite*.

  > [!NOTE]
  > Se si desidera mantenere il file di soluzione con il sito Web, semplicemente spostarla in tale e riaprirlo.

- Se si apre un sito Web che non dispone di alcun file di soluzione in Visual Studio, viene generato automaticamente un nuovo file di soluzione appositamente.

- I progetti Web è necessario alcun file di progetto. Informazioni di progetto vengono archiviate nel file di soluzione, il file Web. config e così via.

- L'aggiunta di proprietà globali per un progetto Web automaticamente crea un file di archiviazione nella cartella della soluzione di progetto Web.

- Una pagina Web intelligente può essere associata a un linguaggio di programmazione lato server usando la direttiva di pagina o \<script runat = "server" > tag.

- Inoltre, le pagine Web possono avere qualsiasi numero di blocchi di script lato client scritto in qualsiasi linguaggio di scripting.

- Un sistema di progetto sito Web viene implementato mediante l'aggiunta di modelli di progetto ed elemento e la registrazione per il [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto.

- Un sistema WAP viene implementato come un sottotipo di progetto, detto anche una versione del progetto. Il [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto è flavored dal sottotipo del WAP per creare il sistema WAP. Per altre informazioni su sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).

- Una pagina Web smart combina HTML con un linguaggio di programmazione lato server. Il server-side delle lingue viene chiamato linguaggio contenuto. Per supportare una lingua indipendente, è necessario implementare il sistema del progetto Web il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> della famiglia di interfacce.

  - Per supportare il linguaggio contenuto in un editor, il servizio di linguaggio HTML necessario posticipare la visualizzazione di codice di linguaggio contenuto per un servizio di linguaggio contenuto.

  - Gli indicatori di errore (smettono) è necessario creare sempre nel buffer primario dell'editor di codice.

## <a name="see-also"></a>Vedere anche
- [Progetti Web](../../extensibility/internals/web-projects.md)