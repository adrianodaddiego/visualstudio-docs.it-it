---
title: 'Generazione nuovo progetto: Dietro le quinte, parte 2 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6643c52ff8e5801c562524e99c4e3f03c00f74b9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687501"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generazione nuovo progetto: Dietro le quinte, seconda parte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [nuova generazione progetto: Dietro le quinte, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) abbiamo visto come il **nuovo progetto** inserite nella finestra di dialogo. Si supponga di aver selezionato una **applicazione di Windows Visual c#**, compilati il **Name** e **percorso** caselle di testo e fa clic su OK.  
  
## <a name="generating-the-solution-files"></a>Per generare i file di soluzione  
 Scelta di un modello di applicazione indirizza [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per decomprimere e aprire il file con estensione vstemplate corrispondente e per avviare un modello per interpretare i comandi XML in questo file. Questi comandi creano progetti ed elementi del progetto nella soluzione nuova o esistente.  
  
 Il modello decompresso il file di origine, denominato modelli di elementi, dalla stessa cartella con estensione zip che contiene il file con estensione vstemplate. Il modello consente di copiare questi file per il nuovo progetto di personalizzazione di conseguenza questi. Per una panoramica dei modelli di progetto ed elemento, vedere [NIB: Modelli di Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Sostituzione dei parametri di modello  
 Quando il modello copia un modello di elemento in un nuovo progetto, i parametri del modello viene sostituito con stringhe di personalizzare il file. Un parametro di modello è un token speciali che è preceduto o seguito da un segno di dollaro, ad esempio, $ $date.  
  
 Verrà ora esaminato un modello di elemento di progetto tipico. Estrarre ed esaminare Program.cs nella cartella 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip Program Files\Microsoft Visual Studio.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Se si crea un nuovo progetto di applicazione Windows denominato "semplice", il modello sostituisce la `$safeprojectname$` parametro con il nome del progetto.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Uno sguardo all'interno di una. File con estensione VSTemplate  
 Questo formato è un file vstemplate di base  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 È stata esaminata la \<TemplateData > sezione la [nuova generazione progetto: Dietro le quinte, parte uno](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). I tag in questa sezione vengono usati per controllare l'aspetto del **nuovo progetto** nella finestra di dialogo.  
  
 I tag nel \<TemplateContent > sezione controllo la generazione di nuovi progetti ed elementi del progetto. Di seguito è riportato il \<TemplateContent > sezione dal file nella cartella \Programmi\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip cswindowsapplication.vstemplate.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 Il \<progetto > tag controlla la generazione di un progetto e il \<ProjectItem > tag controlla la generazione di un elemento del progetto. Se il parametro ReplaceParameters è true, il modello personalizzerà tutti i parametri del modello nel file di progetto o elemento. In questo caso, tutti gli elementi di progetto personalizzati, ad eccezione di Settings. Settings.  
  
 Il parametro TargetFileName specifica il nome e percorso relativo del file di progetto risultante o dell'elemento. Ciò consente di creare una struttura di cartelle per il progetto. Se non si specifica questo argomento, l'elemento del progetto avrà lo stesso nome di modello di elemento di progetto.  
  
 La struttura di cartelle dell'applicazione di Windows risulta è simile alla seguente:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 Il primo e unico \<progetto > tag in legge il modello:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Così facendo, il modello nuovo progetto per creare il file di progetto Simple.csproj copiando e personalizzazione windowsapplication.csproj l'elemento modello.  
  
### <a name="designers-and-references"></a>Finestre di progettazione e riferimenti  
 È possibile visualizzare in Esplora soluzioni che nella cartella proprietà sia presente e che contiene i file previsti. Ma per quanto riguarda progetto fa riferimento e dipendenze di file di progettazione, ad esempio Resources.Designer.cs a Resources. resx e Form1.Designer.cs per Form1.cs?  Questi vengono impostati nel file Simple.csproj quando vengono generati.  
  
 Di seguito è riportato il \<ItemGroup > da Simple.csproj che crea i riferimenti al progetto:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Si noterà che questi sono i riferimenti al sei progetto che vengono visualizzati in Esplora soluzioni. Di seguito è riportata una sezione da un altro \<ItemGroup >. Numero di righe di codice è stati eliminati per maggiore chiarezza. In questa sezione fa Settings.Designer.cs dipenda da Settings. Settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Generazione di un nuovo progetto: dietro le quinte, prima parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)
