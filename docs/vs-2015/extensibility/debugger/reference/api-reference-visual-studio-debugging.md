---
title: Riferimento all'API (debug di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f3e95200cf29c8561798c858635c3864d635fb40
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424509"
---
# <a name="api-reference-visual-studio-debugging"></a>Riferimenti API (debug di Visual Studio)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La sezione di riferimento include una panoramica concettuale dell'API, una Guida che illustra la sintassi e sull'utilizzo per tutti gli elementi di API e un'ampia gamma di esempi di codice. Tutti i riferimenti sono elencati in ordine alfabetico per categoria.  
  
 La tabella seguente illustra i comuni `HRESULT` valori restituiti dai metodi.  
  
|Nome|Descrizione|Value|  
|----------|-----------------|-----------|  
|S_OK|Operazione completata.|0x00000000|  
|E_UNEXPECTED|Errore imprevisto.|0x8000FFFF|  
|E_NOTIMPL|Non implementato.|0x80004001|  
|E_OUTOFMEMORY|Memoria insufficiente per completare l'operazione.|0x8007000E|  
|E_INVALIDARG|Uno o più argomenti non sono validi.|0x80070057|  
|E_NOINTERFACE|Interfaccia non supportata.|0x80004002|  
|E_POINTER|Puntatore non valido.|0x80004003|  
|E_HANDLE|Handle non valido.|0x80070006|  
|E_ABORT|Operazione interrotta.|0x80004004|  
|E_FAIL|Errore imprevisto.|0x80004005|  
|E_ACCESSDENIED|Errore di accesso generale negato.|0x80070005|  
  
> [!NOTE]
> Quando un [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debug metodo restituisce `S_OK`, si presuppone che tutte le risorse sono validi i puntatori di parametro, vale a dire, alcuna convalida non viene effettuata in orizzontale i puntatori di parametro quando `S_OK` viene restituito.  
  
> [!NOTE]
> Non è valido o `NULL` [parametri out] può causare l'IDE di arresto anomalo del sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Helper SDK per eseguire il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
