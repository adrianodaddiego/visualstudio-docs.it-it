---
title: Pagina Applicazione delle proprietà del progetto C#
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 18527e9b45726dbd76f1e76f5d63976278800f6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62791071"
---
# <a name="application-page-project-designer-c"></a>Applicazione (pagina), Creazione progetti (C#)

Usare la pagina **Applicazione** di **Creazione progetti** per specificare le impostazioni e le proprietà dell'applicazione del progetto.

Per accedere alla pagina **Applicazione**, scegliere un nodo del progetto (non il nodo **Soluzione**) in **Esplora soluzioni**. Scegliere quindi **Progetto** > **Proprietà** sulla barra dei menu. Quando si apre **Creazione progetti**, fare clic sulla scheda **Applicazione**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Impostazioni generali dell'applicazione

Le opzioni seguenti consentono di configurare le impostazioni generali per l'applicazione.

**Nome assembly**

Specifica il nome del file di output che conterrà il manifesto dell'assembly. Modificando questa proprietà viene modificata anche la proprietà **Nome output**.

È anche possibile apportare questa modifica dalla riga di comando usando [/out (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Spazio dei nomi predefinito**

Specifica lo spazio dei nomi di base per i file aggiunti al progetto.

Per altre informazioni sulla creazione di spazi dei nomi nel codice, vedere [namespace](/dotnet/csharp/language-reference/keywords/namespace).

Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Framework di destinazione**

Specifica la versione di .NET Framework a cui è destinata l'applicazione. Questa opzione può avere valori diversi a seconda delle versioni di .NET Framework installate nel computer in uso.

Per impostazione predefinita il valore corrisponde al framework di destinazione selezionato al momento della creazione del progetto.

> [!NOTE]
> I pacchetti dei prerequisiti elencati nella [finestra di dialogo Prerequisiti](../../ide/reference/prerequisites-dialog-box.md) vengono impostati automaticamente alla prima apertura della finestra di dialogo. In caso di modifiche successive al framework di destinazione del progetto, sarà necessario selezionare manualmente i prerequisiti in modo che vi sia corrispondenza.

Per altre informazioni, vedere [Procedura: Scegliere una versione di .NET Framework di destinazione](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) e [Panoramica del multitargeting di Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).

**Tipo di output**

Specifica il tipo di applicazione da compilare. I valori sono diversi a seconda del tipo di progetto. Ad esempio, per un progetto **App console** è possibile specificare **Applicazione Windows**, **Applicazione console** o **Libreria di classi** come tipo di output.

Per il progetto di un'applicazione Web è necessario specificare **Libreria di classi**.

Per altre informazioni sulla proprietà **Tipo di output**, vedere [/target (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Per informazioni su come accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.OutputType%2A>.

**Genera automaticamente reindirizzamenti di binding**

I reindirizzamenti di binding vengono aggiunti al progetto se l'app o i relativi componenti fanno riferimento a più di una versione dello stesso assembly. Se si vuole definire manualmente i reindirizzamenti di binding nel file di progetto, deselezionare **Genera automaticamente reindirizzamenti di binding**.

Per altre informazioni sul reindirizzamento, vedere [Reindirizzamento delle versioni di assembly](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Oggetto di avvio**

Definisce il punto di ingresso da chiamare durante il caricamento dell'applicazione. In genere è impostato sul modulo principale dell'applicazione o sulla procedura `Main` da eseguire all'avvio dell'applicazione. Poiché le librerie di classi non hanno un punto di ingresso, l'unica opzione disponibile per questa proprietà è **(Non impostato)**.

Per impostazione predefinita, in un progetto di app WPF il valore di questa opzione è **(Non impostato)**. L'altra opzione è \[nomeprogetto].App. In un progetto WPF è necessario impostare l'URI di avvio per caricare una risorsa interfaccia utente all'avvio dell'applicazione. A tale scopo, aprire il file *Application.xaml* nel progetto e impostare la proprietà `StartupUri` su un file con estensione *xaml* nel progetto, ad esempio *Window1.xaml*. Per un elenco di elementi radice accettabili, vedere <xref:System.Windows.Application.StartupUri%2A>. È necessario definire anche un metodo `public static void Main()` in una classe del progetto. Questa classe verrà visualizzata nell'elenco **Oggetto di avvio** come *NomeProgetto.NomeClasse*. Sarà quindi possibile selezionare la classe come oggetto di avvio.

Per altre informazioni, vedere [/main (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) (/main (opzioni del compilatore C#)). Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

**Informazioni assembly**

Questo pulsante apre la finestra di dialogo [Informazioni assembly](../../ide/reference/assembly-information-dialog-box.md).

## <a name="resources"></a>Risorse

Le opzioni **Risorse** consentono di configurare le impostazioni delle risorse per l'app.

**Icona e manifesto**

Per impostazione predefinita, questo pulsante di opzione è selezionato e sono abilitate le opzioni **Icona** e **Manifesto**. Ciò consente di selezionare un'icona personalizzata o diverse opzioni di generazione del manifesto. Deselezionare questo pulsante di opzione solo se si specifica un file di risorse per il progetto.

**Icona**

Consente di impostare il file con estensione *ico* che si vuole usare come icona di programma. Fare clic su **Sfoglia** per cercare un elemento grafico esistente o digitare il nome del file che si sta cercando. Per altre informazioni, vedere [/win32icon (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) (/win32icon (opzioni del compilatore C#)).

Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

**Manifest**

Consente di selezionare un'opzione di generazione del manifesto quando l'applicazione viene eseguita in Windows Vista sotto Controllo dell'account utente. Questa opzione può avere i valori seguenti:

- **Incorpora manifesto con impostazioni predefinite**. Supporta la modalità di funzionamento tipica di Visual Studio in Windows Vista, che prevede l'incorporazione delle informazioni di sicurezza nel file eseguibile dell'applicazione, specificando che `requestedExecutionLevel` deve essere `AsInvoker`. Questa è l'opzione predefinita.

- **Crea applicazione senza manifesto**. Questo metodo è noto come *virtualizzazione*. Usare questa opzione per mantenere la compatibilità con applicazioni precedenti.

- **Properties\app.manifest**. Questa opzione è obbligatoria per le applicazioni distribuite da ClickOnce o COM senza registrazione. Se si pubblica un'applicazione tramite la distribuzione ClickOnce, questa opzione viene impostata automaticamente su **Manifesto**.

**File di risorse**

Selezionare questo pulsante di opzione se si specifica un file di risorse per il progetto. Se si seleziona questa opzione, le opzioni **Icona** e **Manifesto** vengono disabilitate.

Immettere un nome di percorso o usare il pulsante Sfoglia (**...** ) per aggiungere un file di risorse Win32 al progetto.