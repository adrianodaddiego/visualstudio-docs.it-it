---
title: Esercitazione sugli unit test C#
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 173cc6711f46d7fddad92c3ac871809dda100f36
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704673"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Procedura dettagliata: Creare ed eseguire unit test per codice gestito

Questo articolo illustra come creare, eseguire e personalizzare una serie di unit test usando il framework di unit test di Microsoft per il codice gestito ed **Esplora test** di Visual Studio. Verrà illustrato prima di tutto il progetto C# in fase di sviluppo, quindi saranno creati i test in cui verrà usato il codice e saranno esaminati i risultati. Sarà infine possibile modificare il codice del progetto ed eseguire nuovamente i test.

## <a name="create-a-project-to-test"></a>Creare un progetto da sottoporre a test

::: moniker range="vs-2017"

1. Aprire Visual Studio.

2. Nel menu **File** scegliere **Nuovo** > **Progetto**.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Nell categoria **Visual C#** > **.NET Core** scegliere il modello di progetto **App console (.NET Core)** .

4. Denominare il progetto **Bank**, quindi fare clic su **OK**.

   Il progetto Bank viene creato e visualizzato in **Esplora soluzioni** con il file *Program.cs* aperto nell'editor del codice.

   > [!NOTE]
   > Se il file *Program.cs* non fosse aperto nell'editor, fare doppio clic sul file *Program.cs* in **Esplora soluzioni** per aprirlo.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio.

2. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

3. Cercare e selezionare il modello di progetto **App console (.NET Core)** C# e quindi fare clic su **Avanti**.

4. Denominare il progetto **Bank**, quindi fare clic su **Crea**.

   Il progetto Bank viene creato e visualizzato in **Esplora soluzioni** con il file *Program.cs* aperto nell'editor del codice.

   > [!NOTE]
   > Se il file *Program.cs* non fosse aperto nell'editor, fare doppio clic sul file *Program.cs* in **Esplora soluzioni** per aprirlo.

::: moniker-end

5. Sostituire il contenuto del file *Program.cs* con il codice C# seguente che definisce una classe *BankAccount*:

   ```csharp
   using System;

   namespace BankAccountNS
   {
       /// <summary>
       /// Bank account demo class.
       /// </summary>
       public class BankAccount
       {
           private readonly string m_customerName;
           private double m_balance;

           private BankAccount() { }

           public BankAccount(string customerName, double balance)
           {
               m_customerName = customerName;
               m_balance = balance;
           }

           public string CustomerName
           {
               get { return m_customerName; }
           }

           public double Balance
           {
               get { return m_balance; }
           }

           public void Debit(double amount)
           {
               if (amount > m_balance)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount; // intentionally incorrect code
           }

           public void Credit(double amount)
           {
               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount;
           }

           public static void Main()
           {
               BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

               ba.Credit(5.77);
               ba.Debit(11.22);
               Console.WriteLine("Current balance is ${0}", ba.Balance);
           }
       }
   }
   ```

6. Rinominare il file *BankAccount.cs* facendo clic con il pulsante destro del mouse e scegliendo **Rinomina** in **Esplora soluzioni**.

7. Scegliere **Compila soluzione** dal menu **Compila**.

È ora disponibile un progetto che include metodi da testare. In questo articolo i test sono incentrati sul metodo `Debit`. Il metodo `Debit` viene chiamato quando si preleva denaro da un conto.

## <a name="create-a-unit-test-project"></a>Creare un progetto di unit test

1. Nel menu **File** selezionare **Aggiungi** > **Nuovo progetto**.

   > [!TIP]
   > È anche possibile fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**.

::: moniker range="vs-2017"

2. Nella finestra di dialogo **Nuovo progetto** espandere **Installato**, **Visual C#** e quindi scegliere **Test**.

3. Nell'elenco dei modelli selezionare **Progetto di test MSTest (.NET Core)** .

4. Nella casella **Nome** immettere `BankTests`, quindi scegliere **OK**.

   Il progetto **BankTests** viene aggiunto alla soluzione **Bank**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Cercare e selezionare il modello di progetto **Progetto di test MSTest (.NET Core)** C# e quindi fare clic su **Avanti**.

3. Denominare il progetto **BankTests**.

4. Scegliere **Crea**.

   Il progetto **BankTests** viene aggiunto alla soluzione **Bank**.

::: moniker-end

5. Nel progetto **BankTests** aggiungere un riferimento al progetto **Bank**.

   In **Esplora soluzioni** selezionare **Dipendenze** nel progetto **BankTests** e quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida.

6. Nella finestra di dialogo **Gestione riferimenti** espandere **Progetti**, selezionare **Soluzione** e quindi l'elemento **Bank**.

7. Scegliere **OK**.

## <a name="create-the-test-class"></a>Creare la classe di test

Creare una classe di test per verificare la classe `BankAccount`. È possibile usare il file *UnitTest1.cs* generato dal modello del progetto, fornendo nomi più descrittivi per il file e la classe. È possibile eseguire questa operazione in un unico passaggio rinominando il file in **Esplora soluzioni**.

### <a name="rename-a-file-and-class"></a>Rinominare un file e una classe

1. Per rinominare un file, in **Esplora soluzioni** selezionare il file *UnitTest1.cs* nel progetto BankTests. Dal menu di scelta rapida scegliere **Rinomina** e quindi rinominare il file come *BankAccountTests.cs*.

   ::: moniker range="vs-2017"

   Scegliere **No** nella finestra di dialogo visualizzata.

   ::: moniker-end

2. Per rinominare la classe, posizionare il cursore su `UnitTest1` nell'editor del codice e premere **F2** (o fare clic con il pulsante destro del mouse e scegliere **Rinomina**). Digitare **BankAccountTests** e quindi premere **INVIO**.

Il file *BankAccountTests.cs* contiene ora il codice seguente:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

### <a name="add-a-using-statement"></a>Aggiungere un'istruzione using

Aggiungere un'[istruzione `using`](/dotnet/csharp/language-reference/keywords/using-statement) alla classe di test per consentire di effettuare chiamate nel progetto sottoposto a test senza usare nomi completi. All'inizio del file di classe aggiungere:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Requisiti della classe di test

I requisiti minimi per una classe di test sono i seguenti:

- L'attributo `[TestClass]` è obbligatorio per qualsiasi classe che contiene metodi di unit test da eseguire in Esplora test.

- Ogni metodo di test che si vuole venga riconosciuto in Esplora test deve avere l'attributo `[TestMethod]`.

È possibile avere altre classi in un progetto di unit test che non presentano l'attributo `[TestClass]` ed è possibile avere altri metodi nelle classi di test che non presentano l'attributo `[TestMethod]` . È possibile chiamare questi altri metodi e classi dai metodi di test.

## <a name="create-the-first-test-method"></a>Creare il primo metodo di test

In questa procedura si scriveranno metodi di unit test per verificare il comportamento del metodo `Debit` della classe `BankAccount`.

È necessario controllare almeno tre comportamenti:

- Il metodo genera un oggetto <xref:System.ArgumentOutOfRangeException> se la quantità di debito è superiore al saldo.

- Il metodo genera <xref:System.ArgumentOutOfRangeException> se la quantità di debito è minore di zero.

- Se l'importo del debito è valido, il metodo sottrae l'importo dal saldo del conto.

> [!TIP]
> È possibile eliminare il metodo `TestMethod1` predefinito, in quanto non verrà usato in questa procedura dettagliata.

### <a name="to-create-a-test-method"></a>Per creare un metodo di test

Il primo test verifica che un importo valido (minore del saldo del conto e maggiore di zero) prelevi l'importo corretto dal conto. Aggiungere il metodo seguente alla classe `BankAccountTests` :

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Il metodo è semplice poiché configura un nuovo oggetto `BankAccount` con un saldo iniziale e quindi preleva un importo valido. Usa il metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> per verificare che il saldo finale sia quello previsto.

### <a name="test-method-requirements"></a>Requisiti del metodo di test

Un metodo di test deve soddisfare i seguenti requisiti:

- È decorato con l'attributo `[TestMethod]`.

- Restituisce `void`.

- Non può avere parametri.

## <a name="build-and-run-the-test"></a>Compilare ed eseguire il test

1. Scegliere **Compila soluzione** dal menu **Compila**.

2. Se **Esplora test** non è aperto, scegliere **Test** > **Finestre** > **Esplora test** dalla barra dei menu in alto.

3. Scegliere **Esegui tutto** per eseguire il test.

   Mentre il test è in esecuzione, la barra di stato nella parte superiore della finestra **Esplora test** viene animata. Al termine del test, la barra diventa verde se tutti i metodi di test vengono superati oppure rossa se almeno uno dei test ha esito negativo.

   In questo caso il test non riesce.

4. Selezionare il metodo in **Esplora test** per visualizzare i dettagli nella parte inferiore della finestra.

## <a name="fix-your-code-and-rerun-your-tests"></a>Correggere il codice e rieseguire i test

Il risultato del test contiene un messaggio che descrive l'errore. Per il metodo `AreEqual`, il messaggio visualizza ciò che era previsto e ciò che è stato effettivamente ricevuto. Si prevedeva una diminuzione del saldo, ma questo è aumentato di un valore pari alla somma prelevata.

Lo unit test ha rivelato un bug: la quantità da ritirare viene *aggiunta* al saldo del conto anziché essere *sottratta*.

### <a name="correct-the-bug"></a>Correggere il bug

Per correggere l'errore, nel file *BankAccount.cs* sostituire la riga:

```csharp
m_balance += amount;
```

con:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Eseguire nuovamente il test

In **Esplora test** scegliere **Esegui tutto** per rieseguire il test. La barra verde/rossa diventa verde per indicare che il test è stato superato.

![Esplora test in Visual Studio 2019 che indica che il test è stato superato](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Usare gli unit test per migliorare il codice

In questa sezione viene descritto come un processo iterativo di analisi, di sviluppo di unit test e di refactoring può aiutare a rendere il codice di produzione più affidabile ed efficace.

### <a name="analyze-the-issues"></a>Analizzare i problemi

È stato creato un metodo di test per confermare che un importo valido viene detratto correttamente nel metodo `Debit`. Ora verificare che il metodo generi un oggetto <xref:System.ArgumentOutOfRangeException> se la quantità di debito è

- superiore al saldo o
- minore di zero.

### <a name="create-and-run-new-test-methods"></a>Creare ed eseguire nuovi metodi di test

Creare un metodo di test per verificare il comportamento corretto quando la quantità di debito è minore di zero:

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Usare l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> per confermare che è stata generata l'eccezione appropriata. L'attributo causa l'esito negativo del test a meno che non venga generata un'eccezione <xref:System.ArgumentOutOfRangeException> . Se si modifica temporaneamente il metodo sottoposto a test in modo che generi un'eccezione <xref:System.ApplicationException> più generica quando la quantità di debito è minore di zero, il test funziona correttamente, ovvero si verifica un errore.

Per sottoporre a test il caso in cui l'importo prelevato è maggiore del saldo, seguire questa procedura:

1. Creare un nuovo metodo di test denominato `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Copiare il corpo del metodo da `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` nel nuovo metodo.

3. Impostare `debitAmount` su un numero maggiore del saldo.

L'esecuzione dei due metodi di test dimostra che i test funzionano correttamente.

### <a name="continue-the-analysis"></a>Continuare l'analisi

Tuttavia, gli ultimi due metodi di test presentano alcuni problemi. Non è possibile determinare con certezza quale condizione nel metodo sottoposto a test genera l'eccezione quando si esegue uno dei due test. La possibilità di differenziare le due condizioni, ovvero una quantità di debito negativa o un importo superiore al saldo, renderebbe più affidabili i test.

Tornare ad osservare il metodo sottoposto a test. Notare che entrambe le istruzioni condizionali usano un costruttore `ArgumentOutOfRangeException` che accetta come parametro solo il nome dell'argomento:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

È possibile usare un altro costruttore, che include informazioni molto più complete: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> include il nome dell'argomento, il valore dell'argomento e un messaggio definito dall'utente. È possibile effettuare il refactoring del metodo sottoposto a test per usare questo costruttore. Ancor meglio, è possibile usare membri di tipo pubblico per specificare gli errori.

### <a name="refactor-the-code-under-test"></a>Effettuare il refactoring del codice sottoposto a test

Prima è necessario definire due costanti per i messaggi di errore nell'ambito di classe. Inserire le costanti nella classe sottoposta a test `BankAccount`:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Quindi modificare le due istruzioni condizionali nel metodo `Debit`:

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>Eseguire il refactoring dei metodi di test

Rimuovere l'attributo del metodo di test `ExpectedException` e invece rilevare l'eccezione generata e verificare il messaggio associato. Il metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> offre la possibilità di confrontare due stringhe.

Ora `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` può assumere l'aspetto seguente:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Rieseguire il test, riscrivere e rianalizzare

Si supponga che sia presente un bug nel metodo sottoposto a test e che il metodo `Debit` non generi una <xref:System.ArgumentOutOfRangeException> né tantomeno restituisca il messaggio corretto con l'eccezione. Attualmente, il metodo di test non gestisce questa situazione. Se il valore `debitAmount` è valido, ovvero è minore del saldo ma maggiore di zero, non sarà intercettata alcuna eccezione e quindi non verrà mai attivata l'asserzione. Tuttavia il metodo supera il test. Questo non è il risultato desiderato, perché si vuole che il metodo di test abbia esito negativo se non viene generata alcuna eccezione.

È presente un bug nel metodo di test. Per risolvere il problema, aggiungere un'asserzione <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> alla fine del metodo di test per gestire il caso in cui non viene generata alcuna eccezione.

Una nuova esecuzione dimostra che a questo punto il test *ha esito negativo* se viene rilevata l'eccezione corretta. Il blocco `catch` rileva l'eccezione, ma il metodo continua l'esecuzione e ha esito negativo in corrispondenza della nuova asserzione <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>. Per risolvere il problema, aggiungere un'istruzione `return` dopo `StringAssert` nel blocco `catch`. Rieseguire il test per verificare che il problema è stato risolto. La versione finale di `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` è simile alla seguente:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

### <a name="conclusion"></a>Conclusione

I miglioramenti al codice di test hanno creato metodi di test più affidabili e informativi. Il risultato più importante, tuttavia, è il miglioramento del codice sottoposto a test.

> [!TIP]
> Questa procedura dettagliata usa il framework di unit test di Microsoft per il codice gestito. **Esplora test** consente anche di eseguire test da framework di unit test di terze parti che possiedono adapter per **Esplora test**. Per altre informazioni, vedere [Installare framework di unit test di terze parti](../test/install-third-party-unit-test-frameworks.md)

## <a name="see-also"></a>Vedere anche

Per informazioni su come eseguire i test dalla riga di comando, vedere [Opzioni della riga di comando di VSTest.Console.exe](vstest-console-options.md).
