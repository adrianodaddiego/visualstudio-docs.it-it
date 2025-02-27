---
title: Attività XSD | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 742b2b1660b5a1776edca0a4b64c56222cd1c163
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777639"
---
# <a name="xsd-task"></a>XSD (attività)
Esegue il wrapping dello strumento XML Schema Definition, *xsd.exe*, che genera file di schema o di classe da un'origine.

> [!NOTE]
> A partire da Visual Studio 2017, il supporto dei progetti C++ per *xsd.exe* è deprecato. È comunque possibile usare le API **Microsoft.VisualC.CppCodeProvider** aggiungendo manualmente *CppCodeProvider.dll* alla Global Assembly Cache.

## <a name="parameters"></a>Parametri
 La tabella seguente descrive i parametri dell'attività **XSD**.

- **AdditionalOptions**

     Parametro **String** facoltativo.

     Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, /\<opzione1> /\<opzione2> /\<opzione#>. Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **XSD**.

- **GenerateFromSchema**

     Parametro **String** facoltativo.

     Specifica i tipi generati dallo schema specificato.

     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione XSD.

    - **classes** - **/classes**

    - **dataset** - **/dataset**

- **Lingua**

     Parametro **String** facoltativo.

     Specifica il linguaggio di programmazione da usare per il codice generato.

     È possibile scegliere tra **CS** (C#, il linguaggio predefinito), **VB** (Visual Basic) o **JS** (JScript). È anche possibile specificare un nome completo per una classe che implementa `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Namespace**

     Parametro **String** facoltativo.

     Specifica lo spazio dei nomi del runtime per i tipi generati.

- **Sources**

     Parametro `ITaskItem[]` obbligatorio.

     Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.

- **SuppressStartupBanner**

     Parametro **Boolean** facoltativo.

     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.

- **TrackerLogDirectory**

     Parametro **String** facoltativo.

     Specifica la directory per il log di Tracker.

## <a name="see-also"></a>Vedere anche
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)