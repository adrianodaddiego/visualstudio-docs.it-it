---
title: Attività RC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a69649a7babacb0fe08b483380214f17f2e582f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974657"
---
# <a name="rc-task"></a>RC (attività)
Esegue il wrapping dello strumento Compilatore di risorse di Microsoft Windows, *rc.exe*. L'attività **RC** compila le risorse, ad esempio cursori, icone, bitmap, finestre di dialogo e tipi di carattere, in un file di risorse *(RES)*. Per altre informazioni, vedere [-resource (opzioni del compilatore C#)](https://docs.microsoft.com/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parametri
 Nella tabella che segue vengono descritti i parametri dell'attività RC. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.

|Parametro|Description|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parametro **String[]** facoltativo.<br /><br /> Aggiunge una directory all'elenco delle directory in cui vengono cercati i file di inclusione.<br /><br /> Per altre informazioni, vedere l'opzione **/I** in [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730).|
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Un elenco di opzioni della riga di comando, ad esempio, /\<opzione1> /\<opzione2> /\<opzione#>. Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività **RC**.<br /><br /> Per altre informazioni, vedere le opzioni in [ Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730).|
|**Impostazioni cultura**|Parametro **String** facoltativo.<br /><br /> Specifica un ID impostazioni locali che rappresenta le impostazioni cultura usate nelle risorse.<br /><br /> Per altre informazioni, vedere l'opzione **/l** in [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Uso di RC (riga di comando RC)).|
|**IgnoreStandardIncludePath**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, impedisce al compilatore di risorse di verificare la variabile di ambiente INCLUDE durante la ricerca di file di intestazione o file di risorse.<br /><br /> Per altre informazioni, vedere l'opzione **/x** in [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Uso di RC (riga di comando RC)).|
|**NullTerminateStrings**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, fa terminare con Null tutte le stringhe nella tabella di stringhe.<br /><br /> Per altre informazioni, vedere l'opzione **/n** in [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Uso di RC (riga di comando RC)).|
|**PreprocessorDefinitions**|Parametro **String[]** facoltativo.<br /><br /> Definire uno o più simboli del preprocessore per il compilatore di risorse. Specificare un elenco di simboli di macro.<br /><br /> Per altre informazioni, vedere l'opzione **/d** in [ Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Uso di RC (riga di comando RC)). Vedere anche **UndefinePreprocessorDefinitions** in questa tabella.|
|**ResourceOutputFileName**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del file di risorse. Specificare un nome di file di risorse.<br /><br /> Per altre informazioni, vedere l'opzione **/fo** in [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Uso di RC (riga di comando RC)).|
|**ShowProgress**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, visualizza messaggi che segnalano lo stato di avanzamento del compilatore.<br /><br /> Per altre informazioni, vedere l'opzione **/v**  in [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Uso di RC (riga di comando RC)).|
|**Origine**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|
|**SuppressStartupBanner**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, digitare l'opzione della riga di comando **/?** e quindi visualizzare l'opzione **/nologo**.|
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory log di Tracker.|
|**UndefinePreprocessorDefinitions**|Rimuove la definizione di un simbolo del preprocessore.<br /><br /> Per altre informazioni, vedere l'opzione **/v** in [Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730) (Uso di RC (riga di comando RC)). Vedere anche **PreprocessorDefinitions** in questa tabella.|

## <a name="see-also"></a>Vedere anche
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)