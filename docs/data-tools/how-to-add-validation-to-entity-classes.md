---
title: 'Procedura: Aggiungere la convalida a classi di entità'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b91fc7fb356ebd0db4a0bd7960ac060e7d152ec1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402838"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Procedura: Aggiungere la convalida a classi di entità
La *convalida* delle classi di entità rappresenta il processo mediante cui si conferma che i valori immessi negli oggetti dati sono conformi ai vincoli presenti nello schema di un oggetto e alle regole stabilite per l'applicazione. Per ridurre gli errori, è opportuno convalidare i dati prima di inviare aggiornamenti al database sottostante. La convalida consente anche di ridurre il numero potenziale di round trip tra un'applicazione e il database.

 Il [gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) vengono forniti metodi parziali che consentono agli utenti di estendere il codice generato da progettazione che viene eseguito durante l'inserimento, aggiornamento ed eliminazione di entità complete nonché durante e dopo la singola colonna modifiche.

> [!NOTE]
> Questo argomento fornisce i passaggi di base per l'aggiunta della convalida alle classi di entità usando il **O/R Designer**. Poiché potrebbe essere difficile seguire questi passaggi generici senza fare riferimento a una classe di entità specifico, viene fornita una procedura dettagliata in cui vengono usati dati effettivi.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Aggiungere la convalida per le modifiche al valore in una colonna specifica
 In questa procedura viene mostrato come convalidare i dati quando viene modificato il valore in una colonna. Dato che la convalida viene eseguita nella definizione di classe anziché nell'interfaccia utente, se il valore causa l'esito negativo della convalida, viene generata un'eccezione. Implementare la gestione degli errori per il codice nell'applicazione che tenta di modificare i valori della colonna.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Per convalidare i dati durante la modifica del valore di una colonna

1. Aprire o creare un nuovo file LINQ to SQL classi (**dbml** file) nella **O/R Designer**. (Fare doppio clic sul file **.dbml** in **Esplora soluzioni**.)

2. In **Object Relational Designer** fare clic con il pulsante destro del mouse sulla classe per cui si vuole aggiungere la convalida e quindi scegliere **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.

3. Posizionare il cursore nella classe parziale.

4. Per i progetti di Visual Basic:

    1. Espandere l'elenco **Nome metodo**.

    2. Individuare il metodo **OnNOMECOLONNAChanging** per la colonna a cui si vuole aggiungere la convalida.

    3. Viene aggiunto un metodo `OnCOLUMNNAMEChanging` alla classe parziale.

    4. Aggiungere il codice riportato di seguito per verificare innanzitutto che sia stato immesso un valore e quindi per assicurarsi che il valore immesso per la colonna sia accettabile per l'applicazione. Poiché l'argomento `value` contiene il valore proposto, aggiungere logica per confermare che si tratta di un valore valido:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Per i progetti C#:

    Poiché i progetti c# non generano automaticamente i gestori eventi, è possibile usare IntelliSense per creare i metodi parziali di modifica delle colonne. Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili. Fare clic sul metodo di modifica delle colonne relativo alla colonna per cui si desidera aggiungere la convalida. Il codice seguente è simile al codice che viene generato quando si seleziona un metodo parziale di modifica delle colonne:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Aggiungere la convalida per gli aggiornamenti a una classe di entità
 Oltre a controllare i valori durante le modifiche, è anche possibile convalidare i dati quando si tenta di aggiornare una classe di entità completa. La convalida durante un tentativo di aggiornamento consente di confrontare i valori di più colonne, se richiesto dalle regole business. Nella procedura riportata di seguito viene mostrato come eseguire la convalida quando si tenta di aggiornare una classe di entità completa.

> [!NOTE]
> Il codice di convalida per gli aggiornamenti alle classi di entità complete viene eseguito nella classe <xref:System.Data.Linq.DataContext> parziale, anziché nella classe parziale di una classe di entità specifica.

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Per convalidare i dati durante un aggiornamento a una classe di entità

1. Aprire o creare un nuovo file LINQ to SQL classi (**dbml** file) nella **O/R Designer**. (Fare doppio clic sul file **.dbml** in **Esplora soluzioni**.)

2. Fare clic con il pulsante destro del mouse su un'area vuota in **Object Relational Designer** e quindi scegliere **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per `DataContext`.

3. Posizionare il cursore nella classe parziale per `DataContext`.

4. Per i progetti di Visual Basic:

    1. Espandere l'elenco **Nome metodo**.

    2. Fare clic su **UpdateNOMECLASSEDIENTITÀ**.

    3. Viene aggiunto un metodo `UpdateENTITYCLASSNAME` alla classe parziale.

    4. Accedere ai valori delle singole colonne usando l'argomento `instance`, come mostrato nel codice seguente:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Per i progetti C#:

    Poiché i progetti c# non generano automaticamente i gestori eventi, è possibile usare IntelliSense per creare parziale `UpdateCLASSNAME` (metodo). Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili. Fare clic sul metodo di aggiornamento per la classe in cui si desidera aggiungere la convalida. Il codice seguente è simile al codice che viene generato quando si seleziona un `UpdateCLASSNAME` metodo parziale:

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Convalida dei dati](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)