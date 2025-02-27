---
title: Creazione di un sistema di progetto di base, parte 1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19c73e47e8c07ebcf7c1124e6e59d80f76101458
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341648"
---
# <a name="create-a-basic-project-system-part-1"></a>Creare un sistema di progetto di base, parte 1
In Visual Studio, i progetti sono contenitori utilizzati dagli sviluppatori per organizzare file di codice sorgente e altre risorse. I progetti vengono visualizzati come figli di soluzioni nel **Esplora soluzioni**. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente e creare riferimenti a servizi Web, database e altre risorse.

 I progetti sono definiti nei file di progetto, ad esempio un *file con estensione csproj* file per un progetto Visual c#. È possibile creare un proprio tipo di progetto che ha il proprio estensione nome file di progetto. Per altre informazioni sui tipi di progetto, vedere [tipi di progetto](../extensibility/internals/project-types.md).

> [!NOTE]
> Se è necessario estendere Visual Studio con un tipo di progetto personalizzati, è consigliabile sfruttare il [sistema di progetto di Visual Studio](https://github.com/Microsoft/VSProjectSystem) (vsp) che offre numerosi vantaggi rispetto alla creazione di un sistema di progetto da zero:
>
> - Processo di onboarding più semplice.  Anche un sistema di progetto di base richiede decine di migliaia di righe di codice.  Sfruttando VSPS riduce i costi di onboarding a pochi clic prima che si è pronti per personalizzarlo in base alle esigenze.
> - Maggiore facilità di manutenzione.  Sfruttando VSPS, è sufficiente mantenere i propri scenari.  Noi la gestione di manutenzione di tutta l'infrastruttura di sistema di progetto.
>
>   Se è necessario destinate alle versioni di Visual Studio precedenti a Visual Studio 2013, non sarà in grado di sfruttare VSPS in un'estensione di Visual Studio.  Se è questo il caso, questa procedura dettagliata è ideale per iniziare.

 Questa procedura dettagliata illustra come creare un tipo di progetto che ha l'estensione del file di progetto *.myproj*. Questa procedura dettagliata Usa il sistema di progetto Visual c# esistente.

> [!NOTE]
> Per altri esempi di progetti di estensione, vedere [esempi di VSSDK](https://aka.ms/vs2015sdksamples).

 Questa procedura dettagliata illustra come eseguire queste attività:

- Creare un tipo di progetto di base.

- Creare un modello di progetto di base.

- Registrare il modello di progetto con Visual Studio.

- Creare un'istanza del progetto, aprire il **nuovo progetto** nella finestra di dialogo e quindi usando il modello.

- Creare una factory di progetto per il sistema di progetto.

- Creare un nodo del progetto per il sistema di progetto.

- Aggiungere icone personalizzate per il sistema di progetto.

- Implementare la sostituzione dei parametri di modello di base.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

 È inoltre necessario scaricare il codice sorgente per il [Framework di pacchetto gestito per progetti](https://github.com/tunnelvisionlabs/MPFProj10). Estrarre il file in una posizione accessibile per la soluzione che si intende creare.

## <a name="create-a-basic-project-type"></a>Creare un tipo di progetto di base
 Creare un progetto VSIX c# denominato **SimpleProject**. (**File** > **nuova** > **progetto** e quindi **Visual C#**  >   **Estendibilità** > **progetto VSIX**). Aggiungere un modello di elemento di progetto di pacchetto di Visual Studio (nelle **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**, quindi passare alla **Estendibilità** > **pacchetto Visual Studio**). Denominare il file *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Creazione di un modello di progetto di base
 A questo punto, è possibile modificare questo VSPackage di base per implementare le nuove *.myproj* tipo di progetto. Per creare un progetto basato sul *.myproj* tipo di progetto, Visual Studio è da sapere quali file, risorse e riferimenti da aggiungere al nuovo progetto. Per fornire questa informazione, inserire i file di progetto in una cartella di modello di progetto. Quando un utente utilizza il *.myproj* progetto per creare un progetto, i file vengono copiati nel nuovo progetto.

### <a name="to-create-a-basic-project-template"></a>Per creare un modello di progetto di base

1. Aggiungere al progetto, uno dopo le altre tre cartelle: *Templates\Projects\SimpleProject*. (In **Esplora soluzioni**, fare doppio clic sul **SimpleProject** nodo del progetto, scegliere **Add**, quindi fare clic su **nuova cartella**. Denominare la cartella *modelli*. Nel *modelli* cartella, aggiungere una cartella denominata *progetti*. Nel *progetti* cartella, aggiungere una cartella denominata *SimpleProject*.)

2. Nel *Templates\Projects\SimpleProject* cartella, aggiungere un file di immagine Bitmap da utilizzare come icona denominata *SimpleProject.ico*. Quando fa clic su **Add**, viene aperto l'editor di icona.

3. Verificare l'icona distintivo. Questa icona verrà visualizzata nel **nuovo progetto** finestra di dialogo in un secondo momento nella procedura dettagliata.

    ![Simple Project Icon](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. L'icona di salvare e chiudere l'editor di icona.

5. Nel *Templates\Projects\SimpleProject* cartella, aggiungere un **classe** elemento denominato *Program.cs*.

6. Sostituire il codice esistente con le righe seguenti.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > Non è il formato finale del *Program.cs* codice; la sostituzione verranno gestiti con i parametri in un passaggio successivo. È possibile visualizzare errori di compilazione, ma fino a quando il file **BuildAction** viene **contenuto**, dovrebbe essere possibile compilare ed eseguire il progetto come di consueto.

7. Salvare il file.

8. Copia il *AssemblyInfo.cs* del file dal *delle proprietà* cartella in cui il *Projects\SimpleProject* cartella.

9. Nel *Projects\SimpleProject* cartella aggiungere un file XML denominato *SimpleProject.myproj*.

   > [!NOTE]
   > L'estensione per tutti i progetti di questo tipo viene *.myproj*. Se si desidera modificarlo, è necessario modificarlo ovunque che viene citata nella procedura dettagliata.

10. Sostituire il contenuto esistente con le righe seguenti.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. Salvare il file.

12. Nel **delle proprietà** impostare nella finestra di **azione di compilazione** di *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico* , e *SimpleProject.myproj* al **contenuto**e impostare i **Includi in VSIX** proprietà **True**.

    Questo modello descrive un progetto Visual c# base con una configurazione di Debug e una configurazione di rilascio. Il progetto include due file di origine, *AssemblyInfo.cs* e *Program.cs*e i riferimenti ad assembly diversi. Quando viene creato un progetto dal modello, il valore ProjectGuid verrà automaticamente sostituito da un nuovo GUID.

    Nelle **Esplora soluzioni**, espanso **modelli** cartella apparirà come segue:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Creare una factory di progetto di base
 È necessario indicare a Visual Studio il percorso della cartella dei modelli di progetto. A tale scopo, aggiungere un attributo alla classe VSPackage che implementa la factory del progetto in modo che il percorso del modello viene scritto nel Registro di sistema quando viene compilato il pacchetto VSPackage. Iniziare creando una factory di progetto di base che è identificata da un GUID della factory progetto. Usare la <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo per la connessione alla factory progetto il `SimpleProjectPackage` classe.

### <a name="to-create-a-basic-project-factory"></a>Per creare una factory di progetto di base

1. Crea GUID della factory di progetto (nelle **strumenti** menu, fare clic su **Crea GUID**), o usare quello nell'esempio seguente. Aggiungere i GUID per il `SimpleProjectPackage` classe quasi la sezione con l'oggetto già definito `PackageGuidString`. Il GUID deve essere in formato GUID sia sotto forma di stringa. Il codice risultante dovrebbe essere simile al seguente.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Aggiungere una classe nella parte superiore *SimpleProject* cartella denominata *SimpleProjectFactory.cs*.

3. Aggiungere quanto segue usando istruzioni:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Aggiungere un attributo GUID per il `SimpleProjectFactory` classe. Il valore dell'attributo è il nuovo GUID della factory progetto.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   A questo punto è possibile registrare il modello di progetto.

### <a name="to-register-the-project-template"></a>Per registrare il modello di progetto

1. Nella *SimpleProjectPackage.cs*, aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo di `SimpleProjectPackage` classe, come indicato di seguito.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Ricompilare la soluzione e verificare che la compilazione senza errori.

    La ricompilazione registra il modello di progetto.

   I parametri `defaultProjectExtension` e `possibleProjectExtensions` configurati per l'estensione del file di progetto ( *.myproj*). Il `projectTemplatesDirectory` parametro è impostato per il percorso relativo del *modelli* cartella. Durante la compilazione, questo percorso verrà convertito in una build completa e aggiunto al Registro di sistema per registrare il sistema del progetto.

## <a name="test-the-template-registration"></a>La registrazione di un modello di test
 Registrazione di un modello indica a Visual Studio il percorso della cartella dei modelli di progetto in modo che Visual Studio può visualizzare il nome del modello e l'icona nel **nuovo progetto** nella finestra di dialogo.

### <a name="to-test-the-template-registration"></a>Per testare la registrazione di un modello

1. Premere **F5** per avviare il debug di un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, creare un nuovo progetto del tipo di progetto appena creato. Nel **nuovo progetto** della finestra di dialogo dovrebbe **SimpleProject** sotto **modelli installati**.

   Ora si dispone di una factory di progetto che è registrata. Tuttavia, ancora non è possibile creare un progetto. Il pacchetto del progetto e la factory di progetto interagiscono per creare e inizializzare un progetto.

## <a name="add-the-managed-package-framework-code"></a>Aggiungere il codice del Framework di pacchetto gestito
 Implementare la connessione tra il pacchetto del progetto e la factory del progetto.

- Importare i file di codice sorgente per il Framework di pacchetto gestito.

    1. Scaricare il progetto SimpleProject (in **Esplora soluzioni**, selezionare il nodo del progetto e scegliere il menu di scelta rapida **Scarica progetto**.) e aprire il file di progetto nell'editor XML.

    2. Aggiungere i seguenti blocchi del file di progetto (di sopra di \<Import > blocchi). Impostare `ProjectBasePath` al percorso del *ProjectBase.files* file nel codice gestito Framework di pacchetto appena scaricato. Potrebbe essere necessario aggiungere una barra rovesciata per il nome del percorso. In caso contrario, il progetto potrebbe non riuscire a trovare il codice sorgente di Framework di pacchetto gestito.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Non dimenticare la barra rovesciata alla fine del percorso.

    3. Ricaricare il progetto.

    4. Aggiungere riferimenti agli assembly riportati di seguito:

        - `Microsoft.VisualStudio.Designer.Interfaces` (in  *\<install VSSDK > \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Per inizializzare la factory del progetto

1. Nel *SimpleProjectPackage.cs* del file, aggiungere il codice seguente `using` istruzione.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Derivare la `SimpleProjectPackage` classe `Microsoft.VisualStudio.Package.ProjectPackage`.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registrare la factory del progetto. Aggiungere la riga seguente per il `SimpleProjectPackage.Initialize` metodo, subito dopo `base.Initialize`.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementa la proprietà astratta `ProductUserContext`:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. Nelle *SimpleProjectFactory.cs*, aggiungere il codice seguente `using` istruzione dopo esistente `using` istruzioni.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Derivare la `SimpleProjectFactory` classe `ProjectFactory`.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Aggiungere il seguente metodo fittizio per il `SimpleProjectFactory` classe. Questo metodo è implementato in una sezione successiva.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Aggiungere il seguente campo e al costruttore il `SimpleProjectFactory` classe. Ciò `SimpleProjectPackage` riferimento viene memorizzato nella cache in un campo privato, in modo che può essere utilizzato nell'impostazione di un sito del provider di servizio.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Ricompilare la soluzione e verificare che la compilazione senza errori.

## <a name="test-the-project-factory-implementation"></a>L'implementazione di factory di progetto di test
 Verificare se viene chiamato il costruttore per l'implementazione di factory di progetto.

### <a name="to-test-the-project-factory-implementation"></a>Per testare l'implementazione di factory di progetto

1. Nel *SimpleProjectFactory.cs* del file, impostare un punto di interruzione nella riga seguente all'interno di `SimpleProjectFactory` costruttore.

    ```csharp
    this.package = package;
    ```

2. Premere **F5** per avviare un'istanza sperimentale di Visual Studio.

3. Nell'istanza sperimentale, iniziare a creare un nuovo progetto. Nel **nuovo progetto** finestra di dialogo, seleziona la **SimpleProject** tipo di progetto e quindi fare clic su **OK**. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.

4. Rimuovere il punto di interruzione e arrestare il debug. Poiché non è stata creata ancora un nodo del progetto, il codice di creazione del progetto continua a generare eccezioni.

## <a name="extend-the-projectnode-class"></a>Estendere la classe ProjectNode
 A questo punto è possibile implementare il `SimpleProjectNode` classe che deriva dal `ProjectNode` classe. Il `ProjectNode` classe di base gestisce le attività seguenti della creazione del progetto:

- Copia il file di modello di progetto, *SimpleProject.myproj*, nella nuova cartella di progetto. La copia è stata rinominata in base al nome immesso nella **nuovo progetto** nella finestra di dialogo. Il `ProjectGuid` proprietà valore viene sostituito con un nuovo GUID.

- Gli elementi di MSBuild del file di modello di progetto, attraversa *SimpleProject.myproj*e Cerca `Compile` elementi. Per ogni `Compile` file di destinazione, viene copiato nella nuova cartella di progetto.

  Derivata `SimpleProjectNode` classe gestisce queste attività:

- Abilita le icone per i nodi di progetto e file in **Esplora soluzioni** può essere creato o selezionato.

- Abilita sostituzioni di parametro di modello di progetto aggiuntivi specificare.

### <a name="to-extend-the-projectnode-class"></a>Per estendere la classe ProjectNode

1. Aggiungere una classe denominata `SimpleProjectNode.cs`.

2. Sostituire il codice esistente con quello seguente.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   Ciò `SimpleProjectNode` implementazione della classe dispone di questi metodi sottoposti a override:

- `ProjectGuid`, che restituisce il GUID della factory progetto.

- `ProjectType`, che restituisce il nome localizzato del tipo di progetto.

- `AddFileFromTemplate`, che copia i file selezionati dalla cartella di modello per il progetto di destinazione. Inoltre, questo metodo viene implementato in una sezione successiva.

  Il `SimpleProjectNode` costruttore, ad esempio il `SimpleProjectFactory` memorizza nella cache di costruttore, un `SimpleProjectPackage` riferimento in un campo privato per un uso successivo.

  Per connettersi il `SimpleProjectFactory` classe per il `SimpleProjectNode` (classe), è necessario creare un'istanza di un nuovo `SimpleProjectNode` nel `SimpleProjectFactory.CreateProject` (metodo) e lo memorizza nella cache in un campo privato per un uso successivo.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Per connettere la classe factory di progetto e la classe del nodo

1. Nel *SimpleProjectFactory.cs* del file, aggiungere il codice seguente `using` istruzione:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Sostituire il `SimpleProjectFactory.CreateProject` metodo usando il codice seguente.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Ricompilare la soluzione e verificare che la compilazione senza errori.

## <a name="test-the-projectnode-class"></a>Testare la classe ProjectNode
 La factory di progetto per verificare se crea una gerarchia del progetto di test.

### <a name="to-test-the-projectnode-class"></a>Per testare la classe ProjectNode

1. Premere **F5** per avviare il debug. Nell'istanza sperimentale, creare un nuovo SimpleProject.

2. Visual Studio deve chiamare la factory di progetto per creare un progetto.

3. Chiudere l'istanza sperimentale di Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Aggiungere un'icona del nodo di progetto personalizzati
 L'icona del nodo di progetto nella sezione precedente è un'icona predefinita. È possibile modificarlo per un'icona personalizzata.

### <a name="to-add-a-custom-project-node-icon"></a>Per aggiungere un'icona di nodo di progetto personalizzati

1. Nel **le risorse** cartella, aggiungere un file di mappa di bit denominato *SimpleProjectNode.bmp*.

2. Nel **proprietà** windows, ridurre la bitmap da 16x16 pixel. Rendere la bitmap distintivo.

    ![Simple Project Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. Nel **delle proprietà** finestra Modifica il **azione di compilazione** della bitmap da **risorsa incorporata**.

4. Nelle *SimpleProjectNode.cs*, aggiungere il codice seguente `using` istruzioni:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Aggiungere il seguente campo statico e un costruttore di `SimpleProjectNode` classe.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Aggiungere la proprietà seguente all'inizio del `SimpleProjectNode` classe.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Sostituire il costruttore di istanza con il codice seguente.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   Durante la costruzione statica, `SimpleProjectNode` recupera la bitmap di nodo di progetto dalle risorse del manifesto dell'assembly e li inserisce in un campo privato per un uso successivo. Si noti che la sintassi del <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> percorso dell'immagine. Per visualizzare i nomi delle risorse di manifesto incorporate in un assembly, usare il <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> (metodo). Quando questo metodo viene applicato a di `SimpleProject` assembly, i risultati dovrebbero essere come segue:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Durante la costruzione dell'istanza, il `ProjectNode` caricamenti di classi di base *Resources.imagelis.bmp*, in cui sono incorporati comunemente usato le bitmap di 16x16 dalla *Resources\imagelis.bmp*. Questo elenco bitmap viene resa disponibile per `SimpleProjectNode` come `ImageHandler.ImageList`. `SimpleProjectNode` Accoda la bitmap di nodo di progetto all'elenco. L'offset della bitmap di nodo di progetto nell'elenco delle immagini viene memorizzato nella cache per usarlo come valore della popolazione `ImageIndex` proprietà. Visual Studio Usa questa proprietà per determinare quali bitmap da visualizzare come icona di nodo del progetto.

## <a name="test-the-custom-project-node-icon"></a>Testare l'icona di nodo di progetto personalizzati
 Testare la factory di progetto per verificare se crea una gerarchia del progetto con l'icona di nodo di progetto personalizzato.

### <a name="to-test-the-custom-project-node-icon"></a>Per testare l'icona di nodo di progetto personalizzati

1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.

2. Nel progetto appena creato, si noti che *SimpleProjectNode.bmp* viene utilizzata come icona di nodo del progetto.

     ![Progetto semplice nuovo progetto di nodo](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Aprire *Program.cs* nell'editor del codice. Dovrebbe essere il codice sorgente che è simile al codice seguente.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     Si noti che i parametri del modello $nameSpace$ e $ $className$ non è nuovi valori. Si apprenderà come implementare la sostituzione dei parametri di modello nella sezione successiva.

## <a name="substitute-template-parameters"></a>Sostituire i parametri di modello
 In una sezione precedente, è registrato il modello di progetto in Visual Studio usando il `ProvideProjectFactory` attributo. Registrare il percorso di una cartella di modello in questo modo consente di abilitare la sostituzione dei parametri di modello di base viene sottoposto a override ed espandendo il `ProjectNode.AddFileFromTemplate` classe. Per altre informazioni, vedere [nuova generazione progetto: Dietro le quinte, parte 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 A questo punto aggiungere il codice di sostituzione per il `AddFileFromTemplate` classe.

### <a name="to-substitute-template-parameters"></a>Sostituire i parametri di modello

1. Nel *SimpleProjectNode.cs* del file, aggiungere il codice seguente `using` istruzione.

   ```csharp
   using System.IO;
   ```

2. Sostituire il `AddFileFromTemplate` metodo usando il codice seguente.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. Impostare un punto di interruzione nel metodo, subito dopo il `className` istruzione di assegnazione.

   Le istruzioni di assegnazione determinano i valori ragionevoli per uno spazio dei nomi e un nuovo nome di classe. I due `ProjectNode.FileTemplateProcessor.AddReplace` chiamate al metodo sostituire i valori di parametro di modello corrispondenti con questi nuovi valori.

## <a name="test-the-template-parameter-substitution"></a>Testare la sostituzione dei parametri di modello
 È ora possibile testare la sostituzione dei parametri di modello.

### <a name="to-test-the-template-parameter-substitution"></a>Per testare la sostituzione dei parametri di modello

1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.

2. Esecuzione si arresta nel punto di interruzione il `AddFileFromTemplate` (metodo).

3. Esaminare i valori per il `nameSpace` e `className` parametri.

   - `nameSpace` viene assegnato il valore dei \<RootNamespace > elemento il *\Templates\Projects\SimpleProject\SimpleProject.myproj* file modello di progetto. In questo caso il valore è `MyRootNamespace`.

   - `className` viene assegnato il valore del nome della classe source file, senza l'estensione del nome file. In questo caso, è il primo file da copiare nella cartella di destinazione *AssemblyInfo.cs*; pertanto, il valore di className è `AssemblyInfo`.

4. Rimuovere il punto di interruzione e premere **F5** per continuare l'esecuzione.

    Visual Studio deve completare la creazione di un progetto.

5. Aprire *Program.cs* nell'editor del codice. Dovrebbe essere il codice sorgente che è simile al codice seguente.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    Si noti che lo spazio dei nomi è ora `MyRootNamespace` e il nome della classe è ora `Program`.

6. Avviare il debug del progetto. Il nuovo progetto deve compilare, eseguire e visualizzare "Hello VSX!!!" nella finestra della console.

    ![Comando progetto semplice](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   La procedura è stata completata. È stato implementato un sistema di progetto gestito.