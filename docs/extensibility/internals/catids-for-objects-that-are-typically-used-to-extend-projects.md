---
title: CATID per gli oggetti che sono in genere usati per estendere i progetti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a9a5643a217fb9be3147417ffd0405ab9b0cc9f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324254"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATID per gli oggetti che sono in genere usati per estendere i progetti
La tabella seguente elenca i CATID vengono utilizzati per estendere `Project` e `ProjectItem` gli oggetti di automazione per [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti. Questi CATID sono definiti in *VSLangProj.olb*.

## <a name="listing-of-catids"></a>Elenco di CATID

|Nome|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>CATID di Visual Basic
 La tabella seguente elenca i CATID vengono utilizzati per estendere [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] visualizzare gli oggetti. Sono tutti definiti in *VSLangProj.olb*.

|nome|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>CATID di Visual c#
 Il CATID seguenti possono essere utilizzate per estendere [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] visualizzare gli oggetti. Sono tutti definiti in *VSLangProj.olb*.

|nome|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>CATID di C++
 Quanto segue [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] CATID non sono esposti nelle librerie dei tipi nel sistema di progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 e deve essere incluso nel codice ogni volta che si vuole estendere questi oggetti del progetto. Le librerie dei tipi nelle versioni successive di includerà questi CATID [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|Nome|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 Esempio di codice seguente viene illustrato come programmare questi CATID nel codice.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Quanto segue [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] CATID non sono inoltre esposte nelle librerie di tipo sistema del progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 e deve essere incluso nel codice ogni volta che si vuole estendere questi oggetti del progetto. Sono disponibili solo in questi CATID [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 e non sarà disponibile nelle versioni successive di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|Nome|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 Esempio di codice seguente viene illustrato come programmare questi CATID nel codice:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 I GUID per il [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipi di progetto vengono visualizzati nella tabella seguente.

| Tipo di progetto | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>Vedere anche
- [Aggiungere al progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)