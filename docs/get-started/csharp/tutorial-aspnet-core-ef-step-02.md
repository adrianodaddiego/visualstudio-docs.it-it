---
title: 'Passaggio 2: Creare la prima app Web ASP.NET Core'
description: Creare la prima app Web ASP.NET Core con questa esercitazione video e le istruzioni dettagliate.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 5e9cc4f579b5913d5be3030828cad1a799efcd72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840423"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Passaggio 2: Creare la prima app Web ASP.NET Core

Creare la prima app Web ASP.NET Core con questa esercitazione video e le istruzioni dettagliate.

_Guardare questo video e seguire le indicazioni per creare la prima app ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Avviare Visual Studio 2019 e creare un nuovo progetto

Avviare Visual Studio 2019 e fare clic su **Crea nuovo progetto**. Scegliere **Applicazione Web ASP.NET Core**. Scegliere il modello **Applicazione Web** e mantenere il nome e il percorso del progetto predefiniti. Scegliere **Crea**. Per istruzioni più dettagliate, vedere [il video precedente in questa serie di esercitazioni](tutorial-aspnet-core-ef-step-01.md).

![Visual Studio 2019 - Scegliere le opzioni per il progetto ASP.NET Core](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="explore-the-new-project"></a>Esplorare il nuovo progetto

Nella finestra Esplora soluzioni a destra è possibile visualizzare il contenuto del nuovo progetto. Il contenuto è descritto di seguito.

![Progetto ASP.NET Core di Visual Studio 2019](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

La cartella *wwwroot* contiene i file statici che saranno pubblicamente accessibili dall'applicazione Web. In genere contiene fogli di stile, file di script lato client e immagini.

### <a name="pages"></a>Pages

La cartella *Pages* contiene le pagine Razor del sito. Il modello predefinito offre diverse pagine, tra cui la pagina *Index.cshtml* che è la home page dell'applicazione, nonché le pagine About, Contact e così via.

### <a name="appsettingsjson"></a>appsettings.json

Questo file contiene le impostazioni di configurazione per il sito, in formato JSON.

### <a name="programcs"></a>Program.cs

Questo file opera come punto di ingresso dell'applicazione. Quando l'app viene eseguita, il metodo Main è il primo metodo che viene eseguito ed è responsabile della creazione dell'host Web che conterrà l'applicazione.

### <a name="startupcs"></a>Startup.cs

L'host Web creato in *Program.cs* fa riferimento alla classe Startup e chiama i relativi metodi per configurare l'applicazione. Il metodo ConfigureServices è responsabile della configurazione di tutti i servizi che verranno usati dall'app. Il metodo `Configure` configura la pipeline delle richieste HTTP dell'app. Ogni richiesta viene inviata tramite questa pipeline, interagendo con ciascun componente *middleware* nel corso di tale processo.

### <a name="indexcshtml"></a>Index.cshtml

La home page del sito include markup HTML e codice Razor lato server. Usa Razor per specificare il modello di pagina, `IndexModel`, che si trova nel file *Index.cshtml.cs* associato. Imposta inoltre il titolo della pagina, impostando un valore in ViewData. Questo valore di ViewData viene letto nel file *\_Layout.cshtml*, che si trova nella cartella Shared all'interno della cartella Pages. Il file Layout è condiviso da molte pagine Razor e fornisce le caratteristiche comuni per l'aspetto dell'applicazione. Il rendering del contenuto di ogni pagina viene eseguito all'interno del codice HTML del file Layout.

## <a name="run-the-application"></a>Esecuzione dell'applicazione

Eseguire l'applicazione e visualizzarla nel browser. È possibile eseguire l'applicazione usando **CTRL**+**F5** o scegliendo **Debug** > **Avvia senza eseguire debug** dal menu di Visual Studio.

## <a name="customize-the-application"></a>Personalizzare l'applicazione

Aggiungere una proprietà al file *Index.cshtml.cs* e impostarne il valore sull'ora corrente nel gestore `OnGet`:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Sostituire il contenuto `<div>` in *Index.cshtml* con il markup seguente:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Eseguire di nuovo l'applicazione. Ora nella pagina dovrebbe essere visualizzata l'ora corrente, ma risulta sempre mezzanotte. Questo non è corretto.

![Progetto ASP.NET Core di Visual Studio 2019 nel browser](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Eseguire il debug dell'applicazione

Aggiungere un punto di interruzione al metodo `OnGet` assegnando un valore a `Time` e avviare il debug dell'applicazione.

L'esecuzione si interrompe in corrispondenza della riga e si può osservare che `DateTime.Today` comprende la data, ma l'ora è sempre la mezzanotte perché non sono inclusi dati sull'ora. 

![Progetto ASP.NET Core di Visual Studio 2019 nel browser](media/vs-2019/vs2019-breakpoint.png)

Modificare il codice in modo da usare `DateTime.Now` e continuare l'esecuzione. Il nuovo codice per `OnGet` dovrebbe essere:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Adesso nel browser verrà visualizzata l'ora effettiva del server quando si passa all'app.

![Progetto ASP.NET Core di Visual Studio 2019 nel browser](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Passaggi successivi

Nel prossimo video si apprenderà come aggiungere il supporto dei dati per l'app.

[Esercitazione: Uso dei dati nell'app ASP.NET Core](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Vedere anche

- [Esercitazione: Creare un'app web Razor Pages con ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
