---
title: Creazione di stringhe di filtro per Progettazione tabelle | Documentazione Microsoft
description: Creazione di stringhe di filtro per Progettazione tabelle
services: visual-studio-online
author: ghogen
manager: douge
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
origin.date: 11/18/2016
ms.date: 09/10/2018
ms.author: v-junlch
ms.openlocfilehash: d19084e9cfc9813434f5e68829345440763df7e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572236"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Creazione di stringhe di filtro per Progettazione tabelle
## <a name="overview"></a>Panoramica
Per filtrare i dati in una tabella di Azure visualizzata in **Progettazione tabelle**di Visual Studio, creare una stringa di filtro e immetterla nel campo del filtro. La sintassi della stringa di filtro è definita da WCF Data Services ed è simile a una clausola WHERE SQL, ma viene inviata al servizio tabelle con una richiesta HTTP. **Progettazione tabelle** gestisce automaticamente la codifica appropriata, quindi per filtrare in base a un valore di proprietà desiderato, è necessario immettere solo il nome della proprietà, l'operatore di confronto, il valore dei criteri e, facoltativamente, l'operatore booleano nel campo del filtro. Non è necessario includere l'opzione di query $filter come quando si crea un URL per eseguire la query della tabella in base alle [Informazioni di riferimento sulle API REST dei servizi di archiviazione](http://go.microsoft.com/fwlink/p/?LinkId=400447).

WCF Data Services si basa su [Open Data Protocol](http://go.microsoft.com/fwlink/p/?LinkId=214805) (OData). Per i dettagli sull'opzione di query del sistema di filtro (**$filter**), vedere la [specifica sulle convenzioni URI OData](http://go.microsoft.com/fwlink/p/?LinkId=214806).

## <a name="comparison-operators"></a>Operatori di confronto
Gli operatori logici seguenti sono supportati per tutti i tipi di proprietà:

| Operatore logico | DESCRIZIONE | Stringa di filtro di esempio |
| --- | --- | --- |
| eq |Uguale |Città eq "Redmond" |
| gt |Maggiore di |Prezzo gt 20 |
| ge |Maggiore o uguale a |Prezzo ge 10 |
| lt |Minore di |Prezzo lt 20 |
| le |Minore o uguale |Prezzo le 100 |
| ne |Diverso |Città ne "Londra" |
| e |e |Prezzo le 200 and Prezzo gt 3,5 |
| oppure |Or |Prezzo le 3,5 or Prezzo gt 200 |
| not |not |not isAvailable |

Quando si crea una stringa di filtro, tenere presente le regole seguenti:

- Usare gli operatori logici per confrontare una proprietà con un valore. Si noti che non è possibile confrontare una proprietà con un valore dinamico. Un elemento dell'espressione deve essere una costante.
- Viene effettuata la distinzione tra maiuscole e minuscole per tutte le parti della stringa di filtro.
- Il valore costante deve essere dello stesso tipo di dati della proprietà affinché il filtro restituisca risultati validi. Per altre informazioni sui tipi di proprietà supportati, vedere [Informazioni sul modello di dati del servizio tabelle](http://go.microsoft.com/fwlink/p/?LinkId=400448).

## <a name="filtering-on-string-properties"></a>Applicazione di filtri alle proprietà della stringa
Quando si applicano filtri alle proprietà della stringa, includere la costante di stringa tra virgolette singole.

L'esempio seguente applica filtri alle proprietà **PartitionKey** e **RowKey**. Alla stringa di filtro possono essere aggiunte anche altre proprietà non chiave:

    PartitionKey eq 'Partition1' and RowKey eq '00001'

Anche se non è necessario, è possibile racchiudere ogni espressione di filtro tra parentesi:

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

Si noti che le query con caratteri jolly non sono supportate né nel servizio tabelle né in Progettazione tabelle. Tuttavia, è possibile eseguire la corrispondenza di prefissi usando gli operatori di confronto sul prefisso desiderato. L'esempio seguente restituisce le entità con una proprietà LastName che inizia con la lettera "A":

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>Applicazione di filtri alle proprietà numeriche
Per applicare filtri a un numero intero o a virgola mobile, specificare il numero senza virgolette.

Questo esempio restituisce tutte le entità con una proprietà Age il cui valore è maggiore di 30:

    Age gt 30

Questo esempio restituisce tutte le entità con una proprietà AmountDue il cui valore è minore o uguale a 100,25:

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>Applicazione di filtri alle proprietà booleane
Per applicare filtri a un valoppuree booleano, specificare **true** oppure **false** senza virgolette.

L'esempio seguente restituisce tutte le entità in cui la proprietà IsActive è impostata su **true**:

    IsActive eq true

Questa espressione di filtro può essere scritta anche senza operatore logico. Nell'esempio seguente il servizio tabelle restituirà anche tutte le entità in cui IsActive è **true**:

    IsActive

Per restituire tutte le entità in cui IsActive è false, è possibile usare l'operatore not:

    not IsActive

## <a name="filtering-on-datetime-properties"></a>Applicazione di filtri alle proprietà DateTime
Per applicare filtri a un valore DateTime, specificare la parola chiave **datetime** , seguita dalla costante data/ora tra virgolette singole. La costante data/ora tra virgolette singole deve essere nel formato UTC combinato, come descritto in [Formattazione di valori della proprietà DateTime](http://go.microsoft.com/fwlink/p/?LinkId=400449).

L'esempio seguente restituisce le entità in cui la proprietà CustomerSince è uguale a 10 luglio 2008:

    CustomerSince eq datetime'2008-07-10T00:00:00Z'

<!-- Update_Description: update metedata properties -->