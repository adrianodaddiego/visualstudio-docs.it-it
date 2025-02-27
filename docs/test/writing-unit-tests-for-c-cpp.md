---
title: Scrivere unit test per C/C++
description: Scrivere unit test C++ in Visual Studio usando vari framework di test, tra cui CTest, Boost.Test e Google Test.
ms.date: 05/06/2019
ms.topic: conceptual
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 308478bc47d62731494616a30ce320b3662de735
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461600"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Scrivere unit test per C/C++ in Visual Studio

È possibile scrivere ed eseguire gli unit test C++ usando la finestra **Esplora test**, come per altri linguaggi. Per altre informazioni sull'uso di **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Alcune funzionalità, ad esempio Live Unit Testing, i test codificati dell'interfaccia utente e IntelliTest, non sono supportate per C++.

Visual Studio include questi framework di test C++ senza richiedere download aggiuntivi:

- Framework di testing unità Microsoft per C++
- Google Test
- Boost.Test
- CTest

Oltre ai framework installati, è possibile scrivere adattatori di test personalizzati per qualsiasi framework che si desidera usare all'interno di Visual Studio. Un adattatore di test consente di integrare unit test nella finestra **Esplora test**. Sono disponibili vari adattatori di terze parti in [Visual Studio Marketplace](https://marketplace.visualstudio.com). Per altre informazioni, vedere [Installare framework di unit test di terze parti](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 e versioni successive (Professional ed Enterprise)**

I progetti di unit test C++ supportano [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 e versioni successive (tutte le edizioni)**

- L'**adattatore per Google Test** è incluso come componente predefinito del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Questo adattatore include un modello di progetto che è possibile aggiungere a una soluzione tramite il menu di scelta rapida **Aggiungi nuovo progetto** nel nodo della soluzione in **Esplora soluzioni** e opzioni configurabili tramite **Strumenti** > **Opzioni**. Per altre informazioni, vedere [How to use Google Test for C++ in Visual Studio](how-to-use-google-test-for-cpp.md) (Come usare Google Test per C++ in Visual Studio).

- **Boost.Test** è incluso come componente predefinito del carico di lavoro **Sviluppo di applicazioni desktop con C++**. È integrato in **Esplora test** ma attualmente non include un modello di progetto, pertanto è necessario configurarlo manualmente. Per altre informazioni, vedere [How to use Boost.Test for C++ in Visual Studio](how-to-use-boost-test-for-cpp.md) (Come usare Boost.Test per C++ in Visual Studio).

- Il supporto per **CTest** è incluso nel componente [CMake Tools per Visual Studio](/cpp/ide/cmake-tools-for-visual-cpp) che fa parte del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Tuttavia, CTest non è ancora completamente integrato con **Esplora test**. Per altre informazioni, vedere [How to: use CTest in Visual Studio](how-to-use-ctest-for-cpp.md) (Come usare CTest in Visual Studio).

**Visual Studio 2015 e versioni precedenti**

È possibile scaricare le estensioni degli adattatori per Google Test e Boost.Test Adapter in Visual Studio Marketplace nelle pagine [Test Adapter for Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) e [Test Adapter for Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Flusso di lavoro di test di base

Le sezioni seguenti illustrano i passaggi di base per iniziare con il testing unità in C++. La configurazione di base è molto simile per i framework di Microsoft e Google Test. Per Boost.Test è necessario creare manualmente un progetto di test.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Creare un progetto di test in Visual Studio 2019

I test vengono definiti ed eseguiti all'interno di uno o più progetti di test inclusi nella stessa soluzione del codice da testare. Per aggiungere un nuovo progetto di test a una soluzione esistente, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**. Impostare **Linguaggio** su C++ e digitare "test" nella casella di ricerca. La figura seguente mostra i progetti di test disponibili quando sono installati i carichi di lavoro **Sviluppo di applicazioni desktop con C++** e **Sviluppo per la piattaforma UWP**:

![Progetti di test C++ in Visual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Creare un progetto di test in Visual Studio 2017

I test vengono definiti ed eseguiti all'interno di uno o più progetti di test inclusi nella stessa soluzione del codice da testare. Per aggiungere un nuovo progetto di test a una soluzione esistente, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**. Nel riquadro sinistro scegliere **Progetto di test Visual C++** e scegliere uno dei tipi di progetto nel riquadro centrale. La figura seguente mostra i progetti di test disponibili quando è installato il carico di lavoro **Sviluppo di applicazioni desktop con C++**:

![Progetti di test C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Creare riferimenti ad altri progetti nella soluzione

Per abilitare il codice di test per l'accesso alle funzioni nel progetto da testare, aggiungere un riferimento al progetto nel progetto di test. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Aggiungi** > **Riferimento**. Nella finestra di dialogo scegliere quindi i progetti da testare.

![Aggiungi riferimento](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Eseguire il collegamento a file oggetto o di libreria

Se il codice di test non esporta le funzioni che si vuole testare, è possibile aggiungere i file con estensione obj o lib di output alle dipendenze del progetto di test. Vedere [Per collegare i test all'oggetto o a file di libreria](https://docs.microsoft.com/visualstudio/test/unit-testing-existing-cpp-applications-with-test-explorer?view=vs-2015#objectRef).

### <a name="add-include-directives-for-header-files"></a>Aggiungere direttive #include per il file di intestazione

Nel file con estensione *cpp* dell'unit test aggiungere quindi una direttiva `#include` per tutti i file di intestazione che dichiarano i tipi e le funzioni da testare. Digitare `#include "`. Verrà attivato IntelliSense per facilitare la scelta. Ripetere per eventuali intestazioni aggiuntive.

![Aggiungere direttive include](media/cpp-add-includes-test-project.png)

### <a name="write-test-methods"></a>Scrivere i metodi di test

> [!NOTE]
> Questa sezione mostra la sintassi per il framework di testing unità Microsoft per C/C++. È documentata di seguito: [Informazioni di riferimento sulle API di Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Per la documentazione di Google Test, vedere [Google Test primer](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) (Introduzione a Google Test). Per Boost.Test, vedere [Boost Test library: The unit test framework](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html) (Libreria di test Boost: framework di unit test).

Il file con estensione *cpp* nel progetto di test include una classe stub e un metodo definiti come esempio per la scrittura del codice di test. Si noti che le firme usano le macro TEST_CLASS e TEST_METHOD, che rendono individuabili i metodi dalla finestra **Esplora test**.

![Aggiungere direttive include](media/cpp-write-test-methods.png)

TEST_CLASS e TEST_METHOD fanno parte del [framework di test nativo Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Esplora test** consente di individuare i metodi di test in altri framework supportati in modo analogo.

TEST_METHOD restituisce void. Per produrre un risultato di test, usare i metodi statici nella classe `Assert` per testare i risultati effettivi rispetto a quanto previsto. Nell'esempio seguente si presuppone che `MyClass` includa un costruttore che accetta `std::string`. È possibile verificare che il costruttore inizializzi la classe come previsto in questo modo:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Nell'esempio precedente, il risultato della chiamata `Assert::AreEqual` determina l'esito positivo o negativo del test. La classe Assert contiene molti altri metodi per il confronto dei risultati previsti con quelli effettivi.

È possibile aggiungere *tratti* ai metodi di test per specificare il proprietario, la priorità e altre informazioni per i test. È quindi possibile usare questi valori per ordinare e raggruppare i test in **Esplora test**. Per altre informazioni, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Eseguire i test

1. Nel menu **Test** scegliere **Finestre** > **Esplora test**. La figura seguente illustra un progetto di test con test non ancora eseguiti.

   ![Esplora test prima dell'esecuzione dei test](media/cpp-test-explorer.png)

   > [!NOTE]
   > L'integrazione di CTest con **Esplora test** non è ancora disponibile. Eseguire test CTest dal menu principale di CMake.

1. Se non è visibile alcun test nella finestra, compilare il progetto di test facendo clic con il pulsante destro del mouse sul relativo nodo in **Esplora soluzioni** e scegliendo **Compila** o **Ricompila**.

1. In **Esplora test** scegliere **Esegui tutto** o selezionare i test specifici da eseguire. Fare clic con il pulsante destro del mouse su un test per le altre opzioni, inclusa l'esecuzione in modalità di debug con i punti di interruzione abilitati. Dopo aver eseguito tutti i test, la finestra mostra i test superati e quelli non superati:

![Esplora test dopo l'esecuzione dei test](media/cpp-test-explorer-passed.png)

Per i test non superati, il messaggio include dettagli utili per diagnosticare la causa. È possibile fare clic con il pulsante destro del mouse sul test non superato e scegliere **Esegui debug test selezionati** per esaminare la funzione in cui si è verificato l'errore.

Per altre informazioni sull'uso di **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

Per le procedure consigliate associate agli unit test, vedere [Nozioni fondamentali sugli unit test](unit-test-basics.md).

## <a name="use-codelens"></a>Usare CodeLens

**Visual Studio 2017 e versioni successive (edizioni Professional ed Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) consente di visualizzare rapidamente lo stato di uno unit test senza uscire dall'editor di codice. È possibile inizializzare CodeLens per un progetto di unit test C++ in uno dei modi seguenti:

- Modificare e compilare la soluzione o il progetto di test.
- Ricompilare la soluzione o il progetto.
- Eseguire i test dalla finestra **Esplora test**.

Dopo l'inizializzazione di **CodeLens**, è possibile visualizzare le icone di stato dei test sopra ogni unit test.

![Icone CodeLens C++](media/cpp-test-codelens-icons.png)

Fare clic sull'icona per altre informazioni o per eseguire lo unit test o eseguirne il debug:

![Esecuzione e debug in CodeLens C++](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Vedere anche

- [Eseguire unit test del codice](unit-test-your-code.md)
