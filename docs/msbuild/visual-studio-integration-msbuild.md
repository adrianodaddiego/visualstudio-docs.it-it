---
title: Integrazione di Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d396d56aea8be3724078223261a3b6eb8835692
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445374"
---
# <a name="visual-studio-integration-msbuild"></a>Integrazione di Visual Studio (MSBuild)
Visual Studio ospita [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per caricare e compilare progetti gestiti. Poiché [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è responsabile del progetto, in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è possibile usare efficacemente praticamente qualsiasi progetto nel formato di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], anche se il progetto è stato creato da uno strumento diverso e presenta un processo di compilazione personalizzato.

 Questo articolo descrive aspetti specifici dell'hosting di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Tali aspetti devono essere tenuti in considerazione quando si esegue la personalizzazione di progetti e file con estensione *targets* da caricare e compilare in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Queste considerazioni consentono di assicurarsi che funzionalità di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] come IntelliSense e il debug funzionino con un progetto personalizzato.

 Per informazioni sui progetti C++, vedere [File di progetto](/cpp/ide/project-files).

## <a name="project-file-name-extensions"></a>Estensioni dei file di progetto
 *MSBuild.exe* riconosce qualsiasi estensione di file di progetto che corrisponda al modello *.\*proj*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] riconosce tuttavia solo un sottoinsieme di queste estensioni di file di progetto, che determinano il sistema di progetto specifico del linguaggio che caricherà il progetto. In[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è disponibile un sistema di progetto basato su [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] indipendente dal linguaggio.

 Il sistema di progetto [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], ad esempio, carica i file con estensione *csproj*, ma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è in grado di caricare un file con estensione *xxproj*. Un file di progetto per file di origine in un linguaggio arbitrario deve usare la stessa estensione dei file di progetto di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] per poter essere caricato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="well-known-target-names"></a>Nomi di destinazione noti
 Scegliendo il comando **Compila** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà eseguita la destinazione predefinita del progetto. Spesso tale destinazione viene anche denominata `Build`. Scegliendo il comando **Ricompila** o **Pulisci** verrà effettuato un tentativo di eseguire una destinazione dello stesso nome nel progetto. Scegliendo **Pubblica** verrà eseguita una destinazione denominata `PublishOnly` nel progetto.

## <a name="configurations-and-platforms"></a>Configurazioni e piattaforme
 Le configurazioni sono rappresentate nei progetti di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] da proprietà raggruppate in un elemento `PropertyGroup` che contiene un attributo `Condition` . In[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono analizzate queste condizioni per creare un elenco di configurazioni di progetto e piattaforme da visualizzare. Per estrarre correttamente tale elenco, le condizioni devono avere un formato simile a quello riportato di seguito:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 A tale scopo, in[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono analizzate le condizioni negli elementi `PropertyGroup`, `ItemGroup`, `Import`, Property e Item.

## <a name="additional-build-actions"></a>Altre azioni di compilazione
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di modificare il nome del tipo di elemento di un file in un progetto tramite la proprietà **Azione di compilazione** della finestra **Proprietà file**. I nomi dei tipi di elemento **Compile**, **EmbeddedResource**, **Content** e **None** sono sempre elencati in questo menu, insieme a tutti gli altri nomi di tipi di elemento già presenti nel progetto. Per accertarsi che tutti i nomi dei tipi di elementi personalizzati siano sempre disponibili in questo menu, è possibile aggiungerli a un tipo di elemento denominato `AvailableItemName`. Aggiungendo, ad esempio, il codice riportato di seguito al file di progetto si aggiunge il tipo personalizzato **JScript** a questo menu per tutti i progetti che lo importano:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Alcuni nomi di tipi di elementi sono specifici di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ma non sono inclusi in questo elenco a discesa.

## <a name="in-process-compilers"></a>Compilatori In-Process
 Quando possibile, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene eseguito un tentativo di usare la versione in-process del compilatore di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] per offrire prestazioni migliori. Non si applica a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Affinché questo tentativo abbia esito positivo, è necessario che siano soddisfatte le condizioni riportate di seguito:

- In una destinazione del progetto, deve essere presente un'attività denominata `Vbc` per i progetti di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

- Il parametro `UseHostCompilerIfAvailable` dell'attività deve essere impostato su true.

## <a name="design-time-intellisense"></a>IntelliSense in fase di progettazione
 Per ottenere il supporto di IntelliSense in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prima della creazione di un assembly di output nella compilazione, è necessario che vengano soddisfatte le condizioni seguenti:

- Deve essere presente una destinazione denominata `Compile`.

- La destinazione `Compile` o una delle relative dipendenze deve chiamare l'attività del compilatore per il progetto, ad esempio `Csc` o `Vbc`.

- Tramite la destinazione `Compile` o una delle relative dipendenze è necessario che il compilatore riceva tutti i parametri necessari per IntelliSense, in particolare tutti i riferimenti.

- È necessario soddisfare le condizioni elencate nella sezione [Compilatori in-process](#in-process-compilers).

## <a name="build-solutions"></a>Compilare soluzioni
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]il file di soluzione e l'ordine di compilazione dei progetti sono controllati dallo stesso [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Quando si compila una soluzione con *msbuild.exe* dalla riga di comando, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] analizza il file di soluzione e dispone la compilazione dei progetti nell'ordine corretto. In entrambi i casi i progetti vengono compilati singolarmente in ordine di dipendenza, senza attraversare i riferimenti progetto per progetto. Al contrario, quando si esegue la compilazione di progetti singoli con *msbuild.exe*, i riferimenti da progetto a progetto vengono attraversati.

 Quando si esegue le compilazione all'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la proprietà `$(BuildingInsideVisualStudio)` è impostata su `true`. Questa impostazione può essere usata nel progetto o nei file con estensione *targets* per modificare il comportamento della compilazione.

## <a name="display-properties-and-items"></a>Visualizzare proprietà ed elementi
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] riconosce alcuni nomi e valori delle proprietà. Ad esempio, la proprietà riportata di seguito determinerà la visualizzazione di **Applicazione Windows** nella casella **Tipo di applicazione** in **Progettazione progetti**.

```xml
<OutputType>WinExe</OutputType>
```

 Il valore della proprietà può essere modificato in **Progettazione progetti** e salvato nel file di progetto. Se a tale proprietà viene assegnato un valore non valido tramite modifica manuale, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene visualizzato un avviso al caricamento del progetto e il valore non valido viene sostituito con un valore predefinito.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] riconosce i valori predefiniti per alcune proprietà. Queste proprietà non verranno mantenute nel file di progetto a meno che non presentino valori non predefiniti.

 Le proprietà con nomi arbitrari non vengono visualizzate in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per modificare le proprietà arbitrarie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è necessario aprire il file di progetto nell'editor XML e modificarle manualmente. Per altre informazioni, vedere la sezione [Modificare file di progetto in Visual Studio](#edit-project-files-in-visual-studio) più avanti in questo argomento.

 Gli elementi definiti nel progetto con nomi di tipi di elemento arbitrari vengono visualizzati per impostazione predefinita in **Esplora soluzioni** nel rispettivo nodo del progetto. Per nascondere un elemento, impostare i metadati `Visible` su `false`. L'elemento riportato di seguito, ad esempio, parteciperà al processo di compilazione ma non verrà visualizzato in **Esplora soluzioni**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

 Per impostazione predefinita, gli elementi dichiarati nei file importati nel progetto non vengono visualizzati. Gli elementi creati nel corso del processo di compilazione non vengono mai visualizzati in **Esplora soluzioni**.

## <a name="conditions-on-items-and-properties"></a>Condizioni per elementi e proprietà
 Durante una compilazione, tutte le condizioni sono completamente rispettate.

 Quando vengono determinati i valori delle proprietà da visualizzare, le proprietà considerate da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] come dipendenti dalla configurazione vengono valutate in modo diverso rispetto alle proprietà considerate indipendenti dalla configurazione. Per le proprietà considerate dipendenti dalla configurazione, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono impostate le proprietà `Configuration` e `Platform` in modo appropriato e viene richiesta la rivalutazione del progetto da parte di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . Per le proprietà considerate indipendenti dalla configurazione, la modalità di valutazione delle condizioni non è determinata.

 Le espressioni condizionali per gli elementi vengono sempre ignorate al momento di decidere se l'elemento deve essere visualizzato in **Esplora soluzioni**.

## <a name="debugging"></a>Debug
 Per trovare e avviare l'assembly di output e connettere il debugger, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è necessario che le proprietà `OutputPath`, `AssemblyName`e `OutputType` siano definite correttamente. La connessione del debugger non riesce se con il processo di compilazione il compilatore non ha generato un file con estensione *pdb*.

## <a name="design-time-target-execution"></a>Esecuzione delle destinazioni in fase di progettazione
 In[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene effettuato un tentativo di eseguire le destinazioni con determinati nomi al momento del caricamento di un progetto. Tali destinazioni includono `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` e `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] esegue tali destinazioni in modo da consentire l'inizializzazione del compilatore per fornire IntelliSense, l'inizializzazione del debugger e la risoluzione dei riferimenti visualizzati in Esplora soluzioni. Se tali destinazioni non sono presenti, il progetto verrà caricato e compilato correttamente, ma la fase di progettazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non sarà completamente funzionale.

## <a name="edit-project-files-in-visual-studio"></a>Modificare file di progetto in Visual Studio
 Per modificare direttamente un progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] , è possibile aprire il file di progetto nell'editor XML di Visual Studio.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Per scaricare e modificare un file di progetto in Visual Studio

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto e scegliere **Scarica progetto**.

     Il progetto verrà contrassegnato come **(non disponibile)**.

2. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto non disponibile e scegliere **Modifica \<File progetto>**.

     Il file del progetto verrà aperto nell'editor XML di Visual Studio.

3. Modificare, salvare e chiudere il file di progetto.

4. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto non disponibile e scegliere **Ricarica progetto**.

## <a name="intellisense-and-validation"></a>IntelliSense e convalida
 Quando si usa l'editor XML per modificare i file di progetto, IntelliSense e la convalida si basano sui file di schema di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . Tali file vengono installati nella cache dello schema, che si trova in *\<Directory di installazione di Visual Studio>Xml\Schemas\1040\MSBuild*.

 I tipi di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] principali sono definiti in *Microsoft.Build.Core.xsd* e i tipi comuni usati da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sono definiti in *Microsoft.Build.CommonTypes.xsd*. Per personalizzare gli schemi in modo da avere IntelliSense e la funzionalità di convalida per attività, proprietà e nomi di tipi di elementi personalizzati, è possibile modificare *Microsoft.Build.xsd* oppure creare uno schema personalizzato che includa lo schema CommonTypes o Core. Se viene creato uno schema personalizzato, è necessario indicare all'editor XML come individuarlo tramite la finestra **Proprietà** .

## <a name="edit-loaded-project-files"></a>Modificare i file di progetto caricati
 In[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il contenuto dei file di progetto e dei file importati dai file di progetto viene memorizzato nella cache. Se si modifica un file di progetto caricato, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene automaticamente richiesto di ricaricare il progetto in modo da rendere effettive le modifiche. Tuttavia, se si modifica un file importato da un progetto caricato, non verrà richiesto il ricaricamento e sarà necessario scaricare e ricaricare manualmente il progetto per rendere effettive le modifiche.

## <a name="output-groups"></a>Gruppi di output
 Diverse destinazioni definite in *Microsoft.Common.targets* hanno nomi che terminano con `OutputGroups` o `OutputGroupDependencies`. In[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] queste destinazioni vengono chiamate per ottenere elenchi specifici di output di progetto. Ad esempio, la destinazione `SatelliteDllsProjectOutputGroup` crea un elenco di tutti gli assembly satellite che verranno creati da una compilazione. Tali gruppi di output vengono usati da funzionalità come la pubblicazione, la distribuzione e i riferimenti progetto per progetto. I progetti per i quali tali gruppi non sono definiti vengono caricati e compilati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ma alcune funzionalità potrebbero non funzionare correttamente.

## <a name="reference-resolution"></a>Risoluzione dei riferimenti
 La risoluzione dei riferimenti è il processo di utilizzo degli elementi di riferimento archiviati in un file di progetto per individuare gli assembly effettivi. In[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è necessario attivare la risoluzione dei riferimenti per visualizzare proprietà dettagliate per ogni riferimento nella finestra **Proprietà** . Nell'elenco riportato di seguito vengono descritti tre tipi di riferimenti e le relative modalità di risoluzione.

- Riferimenti dell'assembly:

   Il sistema di progetto chiama una destinazione con il nome noto `ResolveAssemblyReferences`. Tale destinazione deve produrre elementi con il nome di tipi di elementi `ReferencePath`. Ognuno di questi elementi deve avere una specifica dell'elemento (il valore dell'attributo `Include` di un elemento) che contiene il percorso completo del riferimento. Gli elementi devono disporre di tutti i metadati derivati dagli elementi di input passati, oltre ai nuovi metadati riportati di seguito:

  - `CopyLocal`, che indica se l'assembly deve essere copiato nella cartella di output, impostato su true o false.

  - `OriginalItemSpec`, che contiene la specifica dell'elemento originale del riferimento.

  - `ResolvedFrom`, impostato su "{TargetFrameworkDirectory}" se è stato risolto dalla directory [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] .

- Riferimenti COM:

   Il sistema di progetto chiama una destinazione con il nome noto `ResolveCOMReferences`. Tale destinazione deve produrre elementi con il nome di tipi di elementi `ComReferenceWrappers`. Ognuno di questi elementi deve avere una specifica dell'elemento che contiene il percorso completo dell'assembly di interoperabilità per il riferimento COM. Gli elementi devono avere tutti i metadati derivati dagli elementi di input passati, oltre ai nuovi metadati con il nome `CopyLocal`, che indica se l'assembly deve essere copiato nella cartella di output e che può essere impostato su true o false.

- Riferimenti nativi

   Il sistema di progetto chiama una destinazione con il nome noto `ResolveNativeReferences`. Tale destinazione deve produrre elementi con il nome di tipi di elementi `NativeReferenceFile`. Gli elementi devono disporre di tutti i metadati derivati dagli elementi di input passati, oltre a un nuovo metadato singolo denominato `OriginalItemSpec`, che contiene la specifica dell'elemento originale del riferimento.

## <a name="performance-shortcuts"></a>Collegamenti alle prestazioni
 Se si avvia il debug nell'interfaccia utente di Visual Studio (premendo F5 o scegliendo **Debug** > **Avvia debug** sulla barra dei menu), il processo di compilazione usa un controllo di aggiornamento rapido per migliorare le prestazioni. In alcuni casi in cui le compilazioni personalizzate consentono di creare file che vengono a loro volta compilati, il controllo di aggiornamento rapido non identifica correttamente i file modificati. Per i progetti che necessitano di controlli di aggiornamento più approfonditi, è possibile disattivare il controllo rapido impostando la variabile di ambiente `DISABLEFASTUPTODATECHECK=1`. In alternativa, questo oggetto può essere impostato come proprietà MSBuild nel progetto o in un file importato dal progetto.

 Per le compilazioni normali in Visual Studio, il controllo di aggiornamento rapido non viene applicato e il progetto viene compilato come se la compilazione fosse richiamata a un prompt dei comandi.

## <a name="see-also"></a>Vedere anche
- [Procedura: Estendere il processo di compilazione di Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Avviare una compilazione all'interno dell'IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Registrare estensioni di .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)
- [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Attività Csc](../msbuild/csc-task.md)
- [Attività Vbc](../msbuild/vbc-task.md)