---
title: Creazione di istanze del progetto tramite le factory di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b6f6dee7850610b222cf26964dd4811fcf79b5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329400"
---
# <a name="create-project-instances-by-using-project-factories"></a>Creare istanze del progetto tramite le factory di progetto
Tipi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usano un *factory progetto* per creare istanze di oggetti del progetto. È simile a una factory di classe standard per gli oggetti COM cocreatable una factory progetto. Oggetti del progetto non sono tuttavia cocreatable; possono essere creati solo mediante una factory progetto.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE chiama la factory del progetto implementata nel pacchetto VSPackage quando un utente carica un progetto esistente o crea un nuovo progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Il nuovo oggetto di progetto fornisce l'IDE con le informazioni necessarie per popolare **Esplora soluzioni**. Il nuovo oggetto di progetto fornisce inoltre le interfacce necessarie per supportare tutte le azioni dell'interfaccia utente rilevante avviate dall'IDE.

 È possibile implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaccia in una classe nel progetto. In genere, si trova in un proprio modulo.

 I progetti che supportano l'aggregazione da un proprietario devono mantenere una chiave del proprietario nel relativo file di progetto. Quando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metodo viene chiamato su un progetto con una chiave del proprietario, il progetto di proprietà converte la chiave del proprietario in una factory progetto GUID chiama quindi il `CreateProject` metodo factory del progetto per eseguire la creazione effettiva.

## <a name="create-an-owned-project"></a>Creare un progetto di proprietà
 Un proprietario crea un progetto di proprietà in due fasi:

1. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> (metodo). In questo modo il progetto di proprietà per creare un oggetto di progetto aggregato basato sull'input che controlla `IUnknown`. Il progetto di proprietà passa interna `IUnknown` e l'oggetto aggregato al progetto proprietario. In questo modo il progetto di proprietà per l'archiviazione interna `IUnknown`.

2. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> (metodo). Il progetto di proprietà non tutti la creazione dell'istanza quando viene chiamato questo metodo invece di chiamare `IVsProjectFactory::CreateProject` come invece accade per i progetti che non sono di proprietà. L'input `VSOWNEDPROJECTOBJECT` enumerazione viene in genere il progetto di proprietà aggregato. Il progetto di proprietà è possibile usare questa variabile per determinare se è già stato creato il relativo oggetto di progetto (cookie diverso da NULL) o deve essere creato (cookie uguale a NULL).

   Tipi di progetto vengono identificati da un GUID, simile al CLSID di un oggetto COM cocreatable univoco del progetto. In genere, gli handle di factory di un progetto creazione di istanze di un singolo tipo di progetto, anche se è possibile disporre di una factory del progetto di gestire più di un tipo di progetto GUID.

   Tipi di progetto sono associati a un'estensione particolare. Quando un utente tenta di aprire un file di progetto esistente o si tenta di creare un nuovo progetto tramite la clonazione di un modello, l'IDE Usa l'estensione per il file per determinare il GUID del progetto corrispondente.

   Non appena l'IDE determina se deve creare un nuovo progetto o aprire un progetto esistente di un determinato tipo, l'IDE Usa le informazioni nel Registro di sistema in **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]**  per individuare l'oggetto pacchetto VSPackage implementa la factory di progetto necessari. L'IDE carica questo pacchetto VSPackage. Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo, il pacchetto VSPackage deve registrare la factory del progetto con l'IDE chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> (metodo).

   Il metodo principale del `IVsProjectFactory` interfaccia è <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, che deve gestire due scenari: apertura di un progetto esistente e crea un nuovo progetto. La maggior parte dei progetti archiviano il proprio stato di progetto in un file di progetto. In genere, i nuovi progetti vengono creati tramite una copia del file del modello passata al `CreateProject` (metodo) e quindi aprendo la copia. I progetti esistenti vengono create istanze tramite direttamente l'apertura del file di progetto passato a `CreateProject` (metodo). Il `CreateProject` metodo consente di visualizzare le funzionalità dell'interfaccia utente aggiuntive all'utente in base alle esigenze.

   Un progetto può anche non usare alcun file e, invece di archiviare lo stato di progetto in un meccanismo di archiviazione diverso dal file system, ad esempio un database o un server Web. In questo caso, il parametro del nome file passato al `CreateProject` metodo non è effettivamente un percorso del file system, ma una stringa univoca, ovvero un URL, per identificare i dati del progetto. Non è necessaria copiare i file di modello che vengono passati al `CreateProject` per attivare la sequenza di costruzione appropriate da eseguire.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Elenco di controllo: Creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)