---
title: Elemento di simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 303d13d94a413ad3ce17e0bd2b56fe95455e9f54
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316655"
---
# <a name="symbols-element"></a>Elemento Symbols
Definisce i GUID e gli ID usati da altri elementi VSCT. Per codice non gestito, queste informazioni provengono in genere dai file di intestazione specificati da [elemento Extern](../extensibility/extern-element.md). Il codice gestito utilizza gli elementi figlio dell'elemento simboli per definire queste informazioni.

 Se si crea un file con estensione vsct da un file CTO esistente, i simboli verranno generati come elementi figlio dell'elemento di simboli. Per altre informazioni, vedere [Procedura: Creare una. File Vsct da un oggetto esistente. File CTO](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 L'elemento di simboli non deve essere confuso con il [definire elemento](../extensibility/define-element.md), che definisce le coppie nome-valore per l'utilizzo dal preprocessore.

## <a name="syntax"></a>Sintassi

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|nessuno||

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|GuidSymbol|Definisce un simbolo GUID. GuidSymbol ha due attributi obbligatori: nome e valore. Il nome è il nome del simbolo e il valore è il valore del GUID sotto forma di stringa.<br /><br /> For example:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Definisce un simbolo. IDSymbol ha due attributi obbligatori: nome e valore. Il nome è il nome del simbolo e il valore è il valore del simbolo sotto forma di stringa.<br /><br /> Ad esempio:\<IDSymbol name = "MyMenuGroup" value = "0x1020" / >|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|L'elemento radice del file con estensione vsct.|

## <a name="example"></a>Esempio

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)