---
title: Proprietà di visualizzazione griglia | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38f22323f9201a40090a1aec0aeb1b8698c08b0e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311005"
---
# <a name="properties-display-grid"></a>Griglia di visualizzazione delle proprietà

Il **proprietà** finestra Visualizza i campi all'interno di una griglia. La colonna a sinistra contiene i nomi delle proprietà; la colonna a destra contiene i valori delle proprietà.

## <a name="work-with-the-grid"></a>Utilizzare la griglia

Nell'elenco di due colonne sono proprietà indipendenti dalla configurazione che può essere modificata in fase di progettazione e le relative impostazioni correnti. Si noti che tutte le proprietà potrebbero non essere visualizzate. Una proprietà può essere impostata come nascosta, ad esempio, implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> (metodo). In particolare, per nascondere le proprietà con proprietà figlio:

1. Impostare il `pfDisplay` nel parametro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> a `FALSE`.

2. Impostare il `pfHide` nel parametro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> a `TRUE`.

Per inserire informazioni per il **delle proprietà** finestra, l'IDE Usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene chiamato dai pacchetti VSPackage per ogni finestra che contiene oggetti selezionabili con le proprietà correlate da visualizzare nella **proprietà** finestra. **Esplora soluzioni**dell'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> chiamate `GetProperty` usando [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) nella gerarchia di progetto per acquisire gli oggetti visualizzabili nella gerarchia.

Se il pacchetto VSPackage non supporta [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), tenta di usare l'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> usando il valore per [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) che specifichino l'elemento della gerarchia o gli elementi.

Il progetto non è necessario creare VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> perché il pacchetto della finestra fornito dall'IDE che implementa (ad esempio, **Esplora soluzioni**) costruisce <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per suo conto.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> è costituito da tre metodi che vengono chiamati dall'IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene il numero di oggetti selezionati deve essere visualizzato nei **proprietà** finestra.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Restituisce il `IDispatch` gli oggetti selezionati deve essere visualizzato nei **proprietà** finestra.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> rende possibile per gli oggetti restituiti da <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> per essere selezionato dall'utente. In questo modo il pacchetto VSPackage aggiornare in modo visivo la selezione visualizzata all'utente nell'interfaccia utente.

Il **delle proprietà** finestra consente di estrarre informazioni dal `IDispatch` oggetti per recuperare le proprietà in fase di esplorazione. Usa il browser delle proprietà `IDispatch` per porre l'oggetto quali proprietà supporta eseguendo una query `ITypeInfo`, che viene ottenuto da `IDispatch::GetTypeInfo`. Il browser Usa quindi questi valori per popolare la **proprietà** finestra e modifica i valori per le singole proprietà visualizzati nella griglia. Le informazioni di proprietà viene mantenute all'interno dell'oggetto stesso.

Poiché supportano gli oggetti restituiti `IDispatch`, il chiamante può ottenere informazioni quali il nome dell'oggetto tramite la chiamata a `IDispatch::Invoke` o `ITypeInfo::Invoke` con ID predefiniti dispatch (DISPID) che rappresenta le informazioni desiderate. DISPID dichiarati sono negativo per verificare che non entrino in conflitto con identificatori definiti dall'utente.

Il **proprietà** finestra vengono visualizzati diversi tipi di campi in base gli attributi delle proprietà specifiche di un oggetto selezionato. Questi campi includono le caselle di modifica, elenchi a discesa e collegamenti a finestre di dialogo editor personalizzato.

- I valori contenuti in un elenco enumerato vengono recuperati da un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> eseguire una query da `IDispatch`. I valori ottenuti da un elenco enumerato possono essere modificati nella griglia delle proprietà facendo doppio clic sul nome del campo o facendo clic su valore e selezionando il nuovo valore dall'elenco a discesa. Per le proprietà che hanno già impostazioni dagli elenchi enumerati, fare doppio clic sul nome della proprietà nell'elenco delle proprietà consente di scorrere le scelte disponibili. Per le proprietà predefinite con solo due opzioni, ad esempio true/false, fare doppio clic sul nome della proprietà da passare tra le scelte.

- Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> è `false`, che indica che il valore è stato modificato, il valore viene visualizzato in grassetto. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> Consente di determinare se il valore può essere reimpostato sul valore originale. Se, pertanto, è possibile modificare il valore predefinito il valore di facendo clic e scegliendo **reimpostare** dal menu visualizzato. In caso contrario, è necessario modificare manualmente il valore sul valore predefinito. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> consente inoltre di localizzare e nascondere i nomi delle proprietà visualizzate durante la fase di progettazione, ma non influisce sui nomi delle proprietà visualizzate durante la fase di esecuzione.

- Facendo clic sui puntini di sospensione (...) consente di visualizzare un elenco di valori di proprietà da cui l'utente può selezionare (ad esempio, una selezione colori o un elenco del tipo di carattere). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> Questi valori vengono forniti.

## <a name="see-also"></a>Vedere anche

- [Estendere le proprietà](../../extensibility/internals/extending-properties.md)