---
title: Pagina Applicazione, Creazione progetti (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: f13701a8-4e2e-4474-9d60-bb43decbe0c1
caps.latest.revision: 61
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2744dabdb79d777661c1ed73e8a85b05b5308624
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704772"
---
# <a name="application-page-project-designer-c"></a>Applicazione (pagina), Creazione progetti (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usare la pagina **Applicazione** di **Creazione progetti** per specificare le impostazioni e le proprietà dell'applicazione del progetto.  
  
 Per accedere alla pagina **Applicazione**, scegliere un nodo del progetto (non il nodo **Soluzione**) in **Esplora soluzioni**. Quindi scegliere **Progetto**, **Proprietà** sulla barra dei menu. Quando compare Creazione progetti, fare clic sulla scheda **Applicazione**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>Impostazioni generali dell'applicazione  
 Le opzioni seguenti consentono di configurare le impostazioni generali per l'applicazione.  
  
 **Nome assembly**  
 Specifica il nome del file di output che conterrà il manifesto dell'assembly. Modificando questa proprietà verrà modificata anche la proprietà **Nome output**. È anche possibile apportare questa modifica dalla riga di comando usando [/out (opzioni del compilatore C#)](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5). Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Spazio dei nomi predefinito**  
 Specifica lo spazio dei nomi di base per i file aggiunti al progetto.  
  
 Per altre informazioni sulla creazione di spazi dei nomi nel codice, vedere [namespace](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f).  
  
 Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Framework di destinazione**  
 Specifica la versione di .NET Framework a cui è destinata l'applicazione. Questa opzione può avere valori diversi a seconda delle versioni di .NET Framework installate nel computer in uso.  
  
 Per impostazione predefinita, il valore corrisponde al framework di destinazione selezionato nella finestra di dialogo **Nuovo progetto**.  
  
> [!NOTE]
> I pacchetti dei prerequisiti elencati nella [finestra di dialogo Prerequisiti](../../ide/reference/prerequisites-dialog-box.md) vengono impostati automaticamente alla prima apertura della finestra di dialogo. In caso di modifiche successive al framework di destinazione del progetto, sarà necessario selezionare manualmente i prerequisiti in modo che vi sia corrispondenza.  
  
 Per altre informazioni, vedere [How to: Target a Version of the .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) (Procedura: Destinare una versione di .NET Framework) e [Visual Studio Multi-Targeting Overview](../../ide/visual-studio-multi-targeting-overview.md) (Cenni preliminari sul multitargeting di Visual Studio).  
  
 **Tipo di applicazione**  
 Specifica il tipo di applicazione da compilare. Per app di [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] è possibile specificare **App di Windows Store**, **Libreria di classi** o **File WinMD**. Per la maggior parte degli altri tipi di applicazione, è possibile specificare **Applicazione Windows**, **Applicazione console**, **Libreria di classi**, **Servizio Windows** o **Libreria di controlli Web**.  
  
 Per il progetto di un'applicazione Web è necessario specificare **Libreria di classi**.  
  
 Se si specifica l'opzione **File WinMD**, i tipi possono essere inseriti nel progetto in un qualsiasi linguaggio di programmazione Windows Runtime. Creando un pacchetto dell'output del progetto nel formato File WinMD, è possibile codificare un'applicazione in più linguaggi e fare in modo che il codice interagisca come se fosse stato scritto tutto nello stesso linguaggio. È possibile specificare questa opzione per le soluzioni destinate alle librerie Windows Runtime, tra cui le app di [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]. Per altre informazioni, vedere [Creazione di componenti Windows Runtime in C# e Visual Basic](http://go.microsoft.com/fwlink/?LinkId=231895).  
  
> [!NOTE]
> Windows Runtime può fare in modo che i tipi appaiano come oggetti nativi in qualsiasi linguaggio siano usati. Ad esempio, le applicazioni JavaScript che interagiscono con Windows Runtime usano quest'ultimo come un set di oggetti JavaScript, mentre le applicazioni C# usano la libreria come una raccolta di oggetti .NET. Creando un pacchetto dell'output del progetto nel formato File WinMD, è possibile sfruttare la stessa tecnologia usata da Windows Runtime.  
  
 Per altre informazioni sulla proprietà **Tipo di applicazione**, vedere [/target (C# Compiler Options)](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f) (/target (opzioni del compilatore C#)). Per informazioni su come accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Informazioni assembly**  
 Se si fa clic su questo pulsante viene visualizzata la [finestra di dialogo Informazioni assembly](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Oggetto di avvio**  
 Definisce il punto di ingresso da chiamare durante il caricamento dell'applicazione. In genere è impostato sul modulo principale dell'applicazione o sulla procedura `Main` da eseguire all'avvio dell'applicazione. Poiché le librerie di classi non hanno un punto di ingresso, l'unica opzione disponibile per questa proprietà è **(Non impostato)**.  
  
 Per impostazione predefinita, nel progetto di un'applicazione browser WPF, il valore di questa opzione è **(Non impostato)**. L'altra opzione è *NomeProgetto*.App. In questo tipo di progetto è necessario impostare l'URI di avvio per caricare una risorsa interfaccia utente all'avvio dell'applicazione. A tale scopo, aprire il file Application.xaml nel progetto e impostare la proprietà `StartupUri` su un file con estensione xaml del progetto, ad esempio Window1.xaml. Per un elenco di elementi radice accettabili, vedere <xref:System.Windows.Application.StartupUri%2A>. È anche necessario definire un metodo `public static void Main()` in una classe del progetto. Questa classe verrà visualizzata nell'elenco **Oggetto di avvio** come *NomeProgetto.NomeClasse*. Sarà quindi possibile selezionare la classe come oggetto di avvio.  
  
 Per altre informazioni, vedere [/main (C# Compiler Options)](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049) (/main (opzioni del compilatore C#)). Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
## <a name="resources"></a>Risorse  
 Le opzioni seguenti consentono di configurare le impostazioni generali per l'applicazione.  
  
 **Icona e manifesto**  
 Per impostazione predefinita, questo pulsante di opzione è selezionato e sono abilitate le opzioni **Icona** e **Manifesto**. Ciò consente di selezionare un'icona personalizzata o diverse opzioni di generazione del manifesto. Deselezionare questo pulsante di opzione solo se si specifica un file di risorse per il progetto.  
  
 **Icona**  
 Consente di impostare il file con estensione ico che si vuole usare come icona di programma. Fare clic sul pulsante con i puntini di sospensione per cercare un elemento grafico esistente o digitare il nome del file voluto. Per altre informazioni, vedere [/win32icon (C# Compiler Options)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138) (/win32icon (opzioni del compilatore C#)). Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Manifest**  
 Consente di selezionare un'opzione di generazione del manifesto quando l'applicazione viene eseguita in Windows Vista sotto Controllo dell'account utente. Questa opzione può avere i valori seguenti:  
  
- **Incorpora manifesto con impostazioni predefinite**. Supporta la modalità di funzionamento tipica di Visual Studio in Windows Vista, che prevede l'incorporazione delle informazioni di sicurezza nel file eseguibile dell'applicazione, specificando che `requestedExecutionLevel` deve essere `AsInvoker`. Questa è l'opzione predefinita.  
  
- **Crea applicazione senza manifesto**. Questo metodo è noto come *virtualizzazione*. Usare questa opzione per mantenere la compatibilità con applicazioni precedenti.  
  
- **Properties\app.manifest**. Questa opzione è obbligatoria per le applicazioni distribuite da ClickOnce o COM senza registrazione. Se si pubblica un'applicazione tramite la distribuzione ClickOnce, questa opzione viene impostata automaticamente su **Manifesto**.  
  
  **File di risorse**  
  Selezionare questo pulsante di opzione se si specifica un file di risorse per il progetto. Se si seleziona questa opzione, le opzioni **Icona** e **Manifesto** vengono disabilitate.  
  
  Immettere un nome di percorso o usare il pulsante Sfoglia (**...** ) per aggiungere un file di risorse Win32 al progetto.  
  
## <a name="see-also"></a>Vedere anche  
[Managing Application Properties](../../ide/application-properties.md) (Gestione delle proprietà delle applicazioni)  
 [Scrittura di codice nelle soluzioni Office](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0) 
