---
title: Avvisi di globalizzazione
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b61b0f10e4231ce1970a55cf352490cbf02a42d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816531"
---
# <a name="globalization-warnings"></a>Avvisi di globalizzazione
Avvisi di globalizzazione supportano applicazioni e librerie internazionalizzate.

## <a name="in-this-section"></a>In questa sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1300: Specificare MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Per visualizzare correttamente una finestra di messaggio per le impostazioni cultura che utilizzano un ordine di lettura da destra a sinistra, è necessario passare i membri RightAlign e RtlReading dell'enumerazione MessageBoxOptions al metodo Show.|
|[CA1301: Evitare tasti di scelta rapida duplicati](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Un tasto di scelta o tasto di scelta rapida consente l'accesso da tastiera a un controllo mediante ALT. Quando più controlli presentano tasti di scelta duplicati, il comportamento della chiave di accesso non è ben definito.|
|[CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|L'enumerazione System.Environment.SpecialFolder contiene membri che fanno riferimento a cartelle di sistema speciali. I percorsi di queste cartelle possono presentare valori diversi in sistemi operativi diversi. I percorso possono essere modificati e sono localizzati. Il metodo GetFolderPath restituisce i percorsi associati con l'enumerazione Environment. SpecialFolder, localizzato e appropriato per il computer in uso.|
|[CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Un metodo visibile esternamente passa una stringa letterale come parametro a un costruttore o un metodo nella libreria di classi .NET Framework e tale stringa deve essere localizzabile.|
|[CA1304: Specificare CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)|Un metodo o un costruttore chiama un membro che presenta un overload che accetta un parametro System.Globalization.CultureInfo e tale metodo o costruttore non chiama l'overload che accetta il parametro CultureInfo. Quando non viene fornito un oggetto CultureInfo o System.IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali.|
|[CA1305: Specificare IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Un metodo o un costruttore chiama uno o più membri con overload che accettano un parametro System.IFormatProvider e tale metodo o costruttore non chiama l'overload che accetta il parametro IFormatProvider. Quando non viene fornito un oggetto System.Globalization.CultureInfo o IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali.|
|[CA1306: Specificare le impostazioni locali per i tipi di dati](../code-quality/ca1306-set-locale-for-data-types.md)|Le impostazioni locali determinano elementi di presentazione specifici delle impostazioni cultura per i dati, ad esempio la formattazione utilizzata per valori numerici, simboli di valuta e criterio di ordinamento. Quando si crea un oggetto DataTable o DataSet, è opportuno definire in modo esplicito le impostazioni locali.|
|[CA1307: Specificare StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|Un'operazione di confronto tra stringhe utilizza un overload del metodo che non imposta un parametro StringComparison.|
|[CA1308: Normalizzare le stringhe in lettere maiuscole](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Le stringhe devono essere normalizzate in maiuscolo. Un piccolo gruppo di caratteri non è in grado di completare un round trip in caso di conversione in lettere minuscole.|
|[CA1309: Utilizza StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)|In un'operazione di confronto tra stringhe di tipo non linguistico il parametro StringComparison non viene impostato su Ordinal o OrdinalIgnoreCase. L'impostazione esplicita del parametro su StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase consente spesso di rendere il codice più veloce, corretto e affidabile.|
|[CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Un platform invoke membro consente chiamanti parzialmente attendibili, ha un parametro di stringa e non esegue in modo esplicito il marshalling della stringa. Questo può comportare una potenziale vulnerabilità di sicurezza.|