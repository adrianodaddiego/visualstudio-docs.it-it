---
title: Avvisi di interoperabilità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: da9651e06df0f3de046e894df747f88ac528b813
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969310"
---
# <a name="interoperability-warnings"></a>avvisi di interoperabilità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avvisi di interoperabilità supportano l'interazione con i client COM.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Regola|Descrizione|  
|----------|-----------------|  
|[CA1400: I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Un metodo pubblico o protetto è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.DllImportAttribute. Non è possibile individuare la libreria non gestita né associare il metodo a una funzione nella libreria.|  
|[CA1401: P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Un metodo pubblico o protetto in un tipo pubblico presenta l'attributo InteropServices (implementato anche dalla parola chiave Declare in Visual Basic). Questi metodi non devono essere esposti.|  
|[CA1402: Evitare gli overload nelle interfacce visibili a COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Quando i metodi sottoposti a overload vengono esposti ai client COM, solo il primo overload di metodo conserva il proprio nome. Gli overload successivi vengono rinominati in modo univoco aggiungendo al nome un carattere di sottolineatura (_) e un numero intero che corrisponde all'ordine di dichiarazione dell'overload.|  
|[CA1403: I tipi layout automatici non devono essere visibili a COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Un tipo di valore visibile a COM è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.StructLayoutAttribute impostato su LayoutKind.Auto. Il layout di tali tipi può variare a seconda delle versioni di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], con conseguente compromissione delle funzionalità dei client COM che prevedono un layout specifico.|  
|[CA1404: Chiamare GetLastError immediatamente dopo P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Viene eseguita una chiamata al metodo Marshal.GetLastWin32Error o l'equivalente [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] funzione GetLastError e la chiamata immediatamente precedente non è una piattaforma metodo invoke.|  
|[CA1405: Tipi di base di tipo visibile a COM devono essere visibili a COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Un tipo visibile a COM deriva da un tipo non visibile a COM.|  
|[CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|I client COM Visual Basic 6 non è possibile accedere a numeri interi a 64 bit.|  
|[CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|COM non supporta i metodi statici.|  
|[CA1408: Non utilizzare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|I tipi che utilizzano un'interfaccia duale consentono l'associazione dei client a uno specifico layout di interfaccia. Eventuali modifiche apportate in una versione futura al layout del tipo o ai tipi base interromperanno l'associazione dei client COM all'interfaccia. Per impostazione predefinita, se l'attributo ClassInterfaceAttribute non è specificato, viene utilizzata un'interfaccia di solo invio.|  
|[CA1409: Tipi visibili a COM devono essere creabili](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Un tipo di riferimento contrassegnato specificatamente come visibile a COM contiene un costruttore con parametri pubblico, ma non contiene un costruttore predefinito pubblico senza parametri. Un tipo senza un costruttore predefinito pubblico non può essere creato da client COM.|  
|[CA1410: I metodi di registrazione COM devono corrispondere](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Un tipo dichiara un metodo contrassegnato utilizzando il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attributo ma non dichiara un metodo contrassegnato utilizzando il <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attributo, o viceversa.|  
|[CA1411: Metodi di registrazione COM non devono essere visibili](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Un metodo contrassegnato utilizzando l'attributo System.Runtime.InteropServices.ComRegisterFunctionAttribute o ComUnregisterFunctionAttribute è visibile esternamente.|  
|[CA1412: Contrassegnare le interfacce ComSource come IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Un tipo è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.ComSourceInterfacesAttribute e almeno una delle interfacce specificate non è contrassegnata utilizzando l'attributo System.Runtime.InteropServices.InterfaceTypeAttribute impostato su ComInterfaceType.InterfaceIsIDispatch.|  
|[CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|I campi di istanza non pubblici di tipi di valori visibili a COM sono visibili ai client COM. Esaminare il contenuto dei campi alla ricerca di informazioni che non devono essere esposte o che avranno un impatto non previsto sulla progettazione o la sicurezza.|  
|[CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Per il tipo di dati booleano sono disponibili più rappresentazioni nel codice non gestito.|  
|[CA1415: Dichiarare correttamente i P/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md)|Questa regola è simile per le dichiarazioni di metodo di richiamo piattaforma destinate [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] parametro di struttura le funzioni che hanno un puntatore a un OVERLAPPED e il cui parametro gestito corrispondente non è un puntatore a un <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struttura.|
