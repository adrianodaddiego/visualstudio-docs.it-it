---
title: Funzione CvEnterSpan | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvEnterSpanVA
- cvmarkers/CvEnterSpanW
- cvmarkers/CvEnterSpanExW
- cvmarkers/CvEnterSpanA
- cvmarkers/CvEnterSpanExVW
- cvmarkers/CvEnterSpanExA
- cvmarkers/CvEnterSpanVW
helpviewer_keywords:
- CvEnterSpanVW method
- CvEnterSpanVA method
- CvEnterSpanExA method
- CvEnterSpanW method
- CvEnterSpanA method
- CvEnterSpanExVW method
- CvEnterSpanExW method
ms.assetid: 91689e9c-6733-44b9-b36a-8b9b2eef7d1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d501f7c1e75f5b63c82c34f2dc0a4913d7a88c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552632"
---
# <a name="cventerspan-function"></a>Funzione CvEnterSpan
Segna l'inizio di una nuova sezione.

## <a name="syntax"></a>Sintassi

```C
HRESULT CvEnterSpanW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvEnterSpanA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvEnterSpanVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    _In_ va_list argList
    );

HRESULT CvEnterSpanVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    _In_ va_list argList
    );

HRESULT CvEnterSpanExW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvEnterSpanExA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvEnterSpanExVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvEnterSpanExVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    _In_ va_list argList);

```

#### <a name="parameters"></a>Parametri
 `argList` Elenco di argomenti.

 `category` Categoria dello span

 `level` Livello di importanza dello span.

 `pMarkerSeries` Contesto della serie di marcatori valido. Non può essere NULL.

 `pMessage` Stringa formato messaggio. Non può essere NULL.

 `ppSpan` Indirizzo della variabile che conterrà l'oggetto span risultante. L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.

## <a name="return-value"></a>Valore restituito
 S_OK quando il messaggio è stato scritto correttamente. Codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkers.h*

 **Unicode:** CvEnterSpanW, CvEnterSpanVW, CvEnterSpanExW, CvEnterSpanExVW

 **ANSI:** CvEnterSpanA, CvEnterSpanVA, CvEnterSpanExA, CvEnterSpanExVW

## <a name="see-also"></a>Vedere anche
- [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)