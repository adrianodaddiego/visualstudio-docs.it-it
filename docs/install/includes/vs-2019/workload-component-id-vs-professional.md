---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Professional 2019
titleSuffix: ''
description: Usare gli ID dei carichi di lavoro e dei componenti per installare Visual Studio tramite la riga di comando o per specificarli come dipendenza in un manifesto VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 05/21/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: fa8a5fb6aa1e6e1ee031026186abc550f3aa2feb
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037075"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2019"></a>Editor principale di Visual Studio (incluso in Visual Studio Professional 2019)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Descrizione:** shell di base di Visual Studio, che include un editor di codice con riconoscimento della sintassi, il controllo del codice sorgente e la gestione degli elementi di lavoro.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor principale di Visual Studio | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Pagina iniziale di Visual Studio per utenti di C++ | 16.0.28315.86 | Facoltativo

## <a name="azure-development"></a>Sviluppo di Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Descrizione:** progetti, strumenti ed SDK di Azure per sviluppare app cloud, creare risorse e compilare contenitori con supporto Docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Obbligatorio
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28714.129 | Obbligatorio
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Obbligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28516.191 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Supporto del linguaggio F# per progetti Web | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Prerequisiti per lo sviluppo per Azure | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.1.28812.146 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Obbligatorio
Microsoft.Component.Azure.DataLake.Tools | Strumenti per Azure Data Lake e analisi di flusso | 16.1.28916.169 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Consigliato
Microsoft.VisualStudio.Component.AspNet45 | Funzionalità avanzate di ASP.NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools per Kubernetes | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Strumenti di base di Azure Resource Manager | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Strumenti di Service Fabric | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Strumenti di Servizi cloud di Azure | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Strumenti di Azure Resource Manager | 16.0.28528.71 | Consigliato
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.0.28621.142 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.0.28516.191 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.0.28516.191 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.0.28516.191 | Facoltativo
Microsoft.Net.Core.Component.SDK.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28621.142 | Facoltativo
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28516.191 | Facoltativo
Microsoft.NetCore.ComponentGroup.Web.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28621.142 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy di Archiviazione di Azure | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facoltativo

## <a name="data-storage-and-processing"></a>Archiviazione ed elaborazione dei dati

**ID:** Microsoft.VisualStudio.Workload.Data

**Descrizione:** consente di connettere, sviluppare e testare soluzioni dati con SQL Server, Azure Data Lake o Hadoop.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Consigliato
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Consigliato
Microsoft.Component.Azure.DataLake.Tools | Strumenti per Azure Data Lake e analisi di flusso | 16.1.28916.169 | Consigliato
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Consigliato
Microsoft.Net.Core.Component.SDK.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.1.28811.260 | Consigliato
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.0.28621.142 | Consigliato
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.1.28811.260 | Consigliato
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Consigliato
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.1.28812.146 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Consigliato
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 16.0.28315.86 | Facoltativo

## <a name="data-science-and-analytical-applications"></a>Applicazioni analitiche e di analisi scientifica dei dati

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Descrizione:** linguaggi e strumenti per la creazione di applicazioni di data science, tra cui Python e F#.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.PythonTools | Supporto linguaggio Python | 16.0.28625.61 | Consigliato
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.0.28625.61 | Consigliato
Microsoft.Component.PythonTools.Web | Supporto Web Python | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.1.28811.260 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Consigliato
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Facoltativo
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Strumenti di sviluppo nativo Python | 16.0.28621.142 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ Build Tools (v14.00) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Facoltativo

## <a name="net-desktop-development"></a>Sviluppo per desktop .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descrizione:** consente di compilare applicazioni WPF, Windows Form e console con C#, Visual Basic e F#.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Obbligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Consigliato
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | 16.0.28315.86 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Consigliato
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | Facoltativo
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Facoltativo
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.0.28621.142 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.0.28516.191 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.0.28516.191 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.0.28516.191 | Facoltativo
Microsoft.Net.Core.Component.SDK.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28621.142 | Facoltativo
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28516.191 | Facoltativo
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28516.191 | Facoltativo
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.1.28811.260 | Facoltativo
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Facoltativo
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.1.28811.260 | Facoltativo
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.1.28812.146 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Facoltativo

## <a name="game-development-with-unity"></a>Sviluppo di giochi con Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Descrizione:** consente di creare giochi 2D e 3D con Unity, un potente ambiente di sviluppo multipiattaforma.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Strumenti di sviluppo per .NET Framework 3.5 | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools per Unity | 16.0.28315.86 | Obbligatorio
Component.UnityEngine.x64 | Editor di Unity 2018.3 a 64 bit | 16.1.28810.153 | Consigliato
Component.UnityEngine.x86 | Editor di Unity 5.6 a 32 bit | 16.1.28811.260 | Consigliato

## <a name="linux-development-with-c"></a>Sviluppo di applicazioni Linux con C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descrizione:** Creare ed eseguire il debug di applicazioni in ambiente Linux.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.MDD.Linux | C++ per lo sviluppo di applicazioni Linux | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Obbligatorio
Component.Linux.CMake | Strumenti CMake C++ per Linux | 16.1.28916.169 | Consigliato
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Consigliato
Component.MDD.Linux.GCC.arm | Strumenti di sviluppo Embedded e IoT | 16.1.28916.169 | Facoltativo

## <a name="desktop-development-with-c"></a>Sviluppo di applicazioni desktop con C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descrizione:** consente di compilare applicazioni desktop di Windows usando il set di strumenti Microsoft C++, ATL o MFC.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di C++ 2019 Redistributable | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funzionalità desktop di base di C++ | 16.1.28916.169 | Obbligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Consigliato
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.VC.ATL | ATL C++ per Build Tools v142 (x86 e x64) | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.VC.CMake.Project | Strumenti CMake C++ per Windows | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Adattatore di test per Boost.Test | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter for Google Test | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Consigliato
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 16.0.28528.71 | Facoltativo
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Facoltativo
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ Build Tools (v14.00) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC C++ per Build Tools v142 (x86 e x64) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.CLI.Support | Supporto C++/CLI per Build Tools v142 (14.21) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Windows için clang derleyicisi | 16.1.28916.169 | Facoltativo
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduli C++ per Build Tools v142 (x64/x86 - sperimentale) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ Build Tools x64/x86 (v14.16) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Facoltativo

## <a name="game-development-with-c"></a>Sviluppo di giochi con C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Descrizione:** consente di sfruttare tutte le funzionalità di C++ per compilare giochi professionali basati su DirectX, Unreal o Cocos2d.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di C++ 2019 Redistributable | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Consigliato
Component.Android.NDK.R16B | Android NDK (R16B) | 16.1.28916.169 | Facoltativo
Component.Android.SDK25.Private | Programma di installazione di Android SDK (livello API 25) (installazione locale per sviluppo di applicazioni per dispositivi mobili con C++) | 16.0.28625.61 | Facoltativo
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Facoltativo
Component.Cocos | Cocos | 16.0.28315.86 | Facoltativo
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 16.0.28528.71 | Facoltativo
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Facoltativo
Component.MDD.Android | Strumenti di sviluppo per app Android in C++ | 16.0.28517.75 | Facoltativo
Component.OpenJDK | OpenJDK (distribuzione Microsoft) | 16.1.28811.260 | Facoltativo
Component.Unreal | Programma di installazione di Unreal Engine | 16.1.28810.153 | Facoltativo
Component.Unreal.Android | Supporto IDE Android per Unreal Engine | 16.1.28810.153 | Facoltativo
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Facoltativo
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Facoltativo
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Facoltativo

## <a name="mobile-development-with-c"></a>Sviluppo di app per dispositivi mobili con C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Android.SDK25.Private | Programma di installazione di Android SDK (livello API 25) (installazione locale per sviluppo di applicazioni per dispositivi mobili con C++) | 16.0.28625.61 | Obbligatorio
Component.OpenJDK | OpenJDK (distribuzione Microsoft) | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Obbligatorio
Component.Android.NDK.R16B | Android NDK (R16B) | 16.1.28916.169 | Consigliato
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Consigliato
Component.MDD.Android | Strumenti di sviluppo per app Android in C++ | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (a 32 bit) | 16.1.28916.169 | Facoltativo
Component.Google.Android.Emulator.API25.Private | Emulatore Google Android (livello API 25) (installazione locale) | 16.1.28810.153 | Facoltativo
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (installazione locale) | 16.0.28528.71 | Facoltativo
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 16.0.28528.71 | Facoltativo
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Facoltativo
Component.MDD.IOS | Strumenti di sviluppo per app iOS in C++ | 16.0.28517.75 | Facoltativo

## <a name="net-core-cross-platform-development"></a>Sviluppo multipiattaforma .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descrizione:** consente di compilare applicazioni multipiattaforma con .NET Core, ASP.NET Core, HTML/JavaScript e contenitori, tra cui il supporto Docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Obbligatorio
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Obbligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28516.191 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Supporto del linguaggio F# per progetti Web | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.1.28812.146 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Obbligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Consigliato
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28714.129 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28621.142 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Strumenti cloud per lo sviluppo Web | 16.0.28621.142 | Consigliato
Microsoft.Net.Core.Component.SDK.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28621.142 | Facoltativo
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28516.191 | Facoltativo
Microsoft.NetCore.ComponentGroup.Web.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28621.142 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Supporto IIS in fase di sviluppo | 16.0.28315.86 | Facoltativo

## <a name="mobile-development-with-net"></a>Sviluppo di applicazioni per dispositivi mobili con .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con Xamarin.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (distribuzione Microsoft) | 16.1.28811.260 | Obbligatorio
Component.Xamarin | Xamarin | 16.1.28810.153 | Obbligatorio
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.0.28315.86 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Obbligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28516.191 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.Merq | Strumenti interni comuni Xamarin | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.MonoDebugger | Debugger di Mono | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Motore di creazione modello ASP.NET | 16.0.28315.86 | Obbligatorio
Component.Android.SDK27 | Programma di installazione di Android SDK (livello API 27) | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato

## <a name="aspnet-and-web-development"></a>Sviluppo ASP.NET e Web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Descrizione:** consente di compilare applicazioni Web con ASP.NET, ASP.NET Core, HTML/JavaScript e contenitori, tra cui il supporto Docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Obbligatorio
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Obbligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28516.191 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Supporto del linguaggio F# per progetti Web | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.1.28812.146 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Obbligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Consigliato
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28714.129 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Consigliato
Microsoft.VisualStudio.Component.AspNet45 | Funzionalità avanzate di ASP.NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28621.142 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Strumenti cloud per lo sviluppo Web | 16.0.28621.142 | Consigliato
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.0.28621.142 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.0.28516.191 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.0.28516.191 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.0.28516.191 | Facoltativo
Microsoft.Net.Core.Component.SDK.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28621.142 | Facoltativo
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28516.191 | Facoltativo
Microsoft.NetCore.ComponentGroup.Web.2.2 | Strumenti di sviluppo per .NET Core 2.2 | 16.0.28621.142 | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Modelli di progetto aggiuntivi (versioni precedenti) | 16.0.28621.142 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Supporto IIS in fase di sviluppo | 16.0.28315.86 | Facoltativo

## <a name="nodejs-development"></a>Sviluppo Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Descrizione:** consente di compilare applicazioni di rete scalabili con Node.js, un runtime JavaScript asincrono basato su eventi. 

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.Node.Tools | Strumenti di sviluppo Node.js | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Obbligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Facoltativo
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.1.28829.92 | Facoltativo

## <a name="officesharepoint-development"></a>Sviluppo per Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Descrizione:** consente di creare componenti aggiuntivi per Office e SharePoint, soluzioni SharePoint e componenti aggiuntivi VSTO usando C#, VB e JavaScript.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Obbligatorio
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Obbligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools per Visual Studio | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.1.28812.146 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools per Office (VSTO) | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.0.28621.142 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.0.28516.191 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.0.28516.191 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.0.28516.191 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Facoltativo

## <a name="python-development"></a>Sviluppo Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Descrizione:** modifica, debug, sviluppo interattivo e controllo del codice sorgente per Python.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.PythonTools | Supporto linguaggio Python | 16.0.28625.61 | Obbligatorio
Component.CPython3.x64 | Python 3 a 64 bit (3.7.3) | 3.7.3 | Consigliato
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.182 | Consigliato
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.0.28625.61 | Consigliato
Microsoft.Component.PythonTools.Web | Supporto Web Python | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.1.28811.260 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.3.4 | TypeScript 3.4 SDK | 16.0.28829.92 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Consigliato
Component.CPython2.x64 | Python 2 a 64 bit (2.7.16) | 2.7.16 | Facoltativo
Component.CPython2.x86 | Python 2 a 32 bit (2.7.16) | 2.7.16 | Facoltativo
Component.CPython3.x86 | Python 3 a 32 bit (3.7.3) | 3.7.3 | Facoltativo
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Facoltativo
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Facoltativo
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Facoltativo
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Facoltativo
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Strumenti di sviluppo nativo Python | 16.0.28621.142 | Facoltativo
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Facoltativo
Microsoft.Net.Core.Component.SDK.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Facoltativo
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.0.28621.142 | Facoltativo
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Facoltativo
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.1.28811.260 | Facoltativo
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ Build Tools (v14.00) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.1.28812.146 | Facoltativo

## <a name="universal-windows-platform-development"></a>Sviluppo della piattaforma UWP (Universal Windows Platform)

**ID:** Microsoft.VisualStudio.Workload.Universal

**Descrizione:** consente di creare applicazioni per la piattaforma UWP (Universal Windows Platform) con C#, VB o facoltativamente C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.0.28315.86 | Obbligatorio
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | 16.0.28315.86 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Strumenti di sviluppo per .NET Core 2.1 | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Obbligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.0.28625.61 | Obbligatorio
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native e .NET Standard | 16.0.28516.191 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Strumenti della piattaforma UWP (Universal Windows Platform) | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Strumenti della piattaforma UWP (Universal Windows Platform) per Xamarin | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Supporto della piattaforma UWP (Universal Windows Platform) C++ per Build Tools v142 (ARM64) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di C++ 2019 Redistributable | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 - VS 2019 C++ Build Tools ARM (v14.21) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 - VS 2019 C++ Build Tools ARM64 (v14.21) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ Build Tools ARM (v14.16) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ Build Tools ARM64 (v14.16) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ Build Tools x64/x86 (v14.16) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Connettività dispositivi USB | 16.0.28320.51 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funzionalità desktop di base di C++ | 16.1.28916.169 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Strumenti della piattaforma UWP (Universal Windows Platform) per C++ (v142) | 16.1.28811.260 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Strumenti della piattaforma UWP (Universal Windows Platform) per C++ (v141) | 16.1.28810.153 | Facoltativo

## <a name="visual-studio-extension-development"></a>Sviluppo di estensioni di Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descrizione:** consente di creare componenti aggiuntivi ed estensioni per Visual Studio, inclusi nuovi comandi, analizzatori del codice e finestre degli strumenti.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.0.28517.75 | Obbligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.1.28811.260 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.1.28829.92 | Obbligatorio
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Prerequisiti per lo sviluppo di estensioni di Visual Studio | 16.0.28621.142 | Obbligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Consigliato
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Consigliato
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | Facoltativo
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 16.0.28625.61 | Facoltativo
Microsoft.Component.VC.Runtime.OSSupport | Runtime della piattaforma UWP (Universal Windows Platform) C++ per Build Tools v142 | 16.1.28811.260 | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.1.28917.181 | Facoltativo
Microsoft.VisualStudio.Component.ClassDesigner | Progettazione classi | 16.0.28528.71 | Facoltativo
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATL | ATL C++ per Build Tools v142 (x86 e x64) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC C++ per Build Tools v142 (x86 e x64) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.1.28829.92 | Facoltativo

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | nome | Versione
--- | --- | ---
Component.GitHub.VisualStudio | Estensione GitHub per Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 16.0.28707.177
Microsoft.Component.HelpViewer | Help Viewer | 16.0.28625.61
Microsoft.NetCore.1x.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 1.0-1.1 per il Web | 16.0.28621.142
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Integrazione di Office con Azure DevOps | 16.0.28625.61
Microsoft.VisualStudio.Component.DependencyValidation.Community | Convalida delle dipendenze | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | GIT per Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Strumenti di LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ Build Tools ARM (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM VS 2019 C++ (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ Build Tools ARM64 (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM64 VS 2019 C++ (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL | ATL C++ v14.20 per Build Tools v142 (x86 e x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | ATL C++ v14.20 per Build Tools v142 (ARM) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | ATL C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | ATL C++ v14.20 per Build Tools v142 (ARM64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | ATL C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | ATL C++ v14.20 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | Supporto C++/CLI per Build Tools v142 (14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC | MFC C++ v14.20 per Build Tools v142 (x86 e x64) | 16.1.28916.169
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | MFC C++ v14.20 per Build Tools v142 (ARM) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | MFC C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | MFC C++ v14.20 per Build Tools v142 (ARM64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | MFC C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | MFC C++ v14.20 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - Librerie con mitigazione Spectre x64/x86 VS 2019 C++ (v14.20) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.ATL.ARM | ATL C++ per Build Tools v142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | ATL C++ per Build Tools v142 con mitigazioni Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | ATL C++ per Build Tools v142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | ATL C++ per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.Spectre | ATL C++ per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | MFC C++ per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM | MFC C++ per Build Tools v142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | MFC C++ per Build Tools v142 con mitigazioni Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | MFC C++ per Build Tools v142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | MFC C++ per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Redist.MSM | MSM di C++ 2019 Redistributable | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM VS 2019 C++ (v14.21) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM64 VS 2019 C++ (v14.21) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 - Librerie con mitigazione Spectre x64/x86 VS 2019 C++ (v14.21)  | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 - Librerie con mitigazione Spectre ARM VS 2017 C++ (v14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 - Librerie con mitigazione Spectre ARM64 VS 2017 C++ (v14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ATL | ATL C++ per Build Tools v141 (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | ATL C++ per Build Tools v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | ATL C++ per Build Tools v141 con mitigazioni Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | ATL C++ per Build Tools v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | ATL C++ per Build Tools v141 con mitigazioni Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | ATL C++ per Build Tools v141 con mitigazioni Spectre (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | Supporto C++/CLI per Build Tools v141 (14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.MFC | MFC C++ per Build Tools v141 (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | MFC C++ per Build Tools v141 (ARM) | 16.1.28916.169
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | MFC C++ per Build Tools v141 con mitigazioni Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | MFC C++ per Build Tools v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | MFC C++ per Build Tools v141 con mitigazioni Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | MFC C++ per Build Tools v141 con mitigazioni Spectre (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 - Librerie con mitigazione Spectre x64/x86 VS 2017 C++ (v14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Supporto di Windows XP C++ per strumenti VS 2017 (v141) [deprecato] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
