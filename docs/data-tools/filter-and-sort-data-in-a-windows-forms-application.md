---
title: Filtrare e ordinare i dati in un'applicazione Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 17416a3b64d6cbb5f01192440a9df735f0b9fb94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566729"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrare e ordinare i dati in un'applicazione Windows Forms

Per filtrare i dati, impostare il <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà da un'espressione stringa che restituisce i record desiderati.

Per ordinare i dati, impostare il <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà sul nome di colonna in cui si desidera eseguire l'ordinamento; accodare `DESC` per ordinare in ordine decrescente, o aggiungere `ASC` per ordinare in ordine crescente.

> [!NOTE]
> Se l'applicazione non usa <xref:System.Windows.Forms.BindingSource> componenti, è possibile filtrare e ordinare i dati utilizzando <xref:System.Data.DataView> oggetti. Per altre informazioni, vedere [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Per filtrare i dati utilizzando un BindingSource (componente)

- Impostare il <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà per l'espressione da restituire. Ad esempio, il codice seguente restituisce i clienti con una `CompanyName` che inizia con "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Per ordinare i dati utilizzando un BindingSource (componente)

- Impostare il <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà per la colonna che si desidera eseguire l'ordinamento. Ad esempio, il codice seguente Ordina i clienti sul `CompanyName` colonna in ordine decrescente:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)