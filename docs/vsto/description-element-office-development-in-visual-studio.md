---
title: '&lt;Descrizione&gt; elemento (sviluppo per Office in Visual Studio)'
titleSuffix: ''
ms.custom: secdec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ede5ac920c1d40402504544a13f8a00905b82e80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972382"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Descrizione&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `description` dello spazio dei nomi `vstov4` archivia la descrizione della soluzione Office che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.

## <a name="syntax"></a>Sintassi

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 Facoltativo. L'elemento `description` si trova nello spazio dei nomi `vstov4` . Contiene la descrizione del componente aggiuntivo che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.

 L'elemento `description` è privo di attributi o elementi.

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `description` in una soluzione a livello di applicazione distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice è parte di un esempio più esaustivo disponibile nel [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Vedere anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)