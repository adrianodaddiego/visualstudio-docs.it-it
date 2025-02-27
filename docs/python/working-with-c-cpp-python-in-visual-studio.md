---
title: Scrivere estensioni C++ per Python
description: Procedura dettagliata per la creazione di un'estensione C++ per Python con Visual Studio, CPython e PyBind11, incluso il debug in modalità mista.
ms.date: 11/19/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9c81984e8921e44e32b58ae7f5c5c27c5fe8b12f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956950"
---
# <a name="create-a-c-extension-for-python"></a>Creare un'estensione C++ per Python

I moduli scritti in C++ (o in C) vengono comunemente usati per estendere le funzionalità di un interprete Python e anche per abilitare l'accesso alle funzionalità di basso livello del sistema operativo. Sono disponibili tre tipi primari di moduli:

- Moduli acceleratori: dato che Python è un linguaggio interpretato, determinati frammenti di codice possono essere scritti in C++ per ottenere migliori prestazioni.
- Moduli wrapper:espongono al codice Python le interfacce C/C++ esistenti o un'API più facilmente utilizzabile da Python.
- Moduli di accesso al sistema di basso livello: creati per accedere alle funzionalità di basso livello del runtime di CPython, al sistema operativo o all'hardware sottostante.

Questo articolo illustra la creazione di un modulo di estensione C++ per CPython per calcolare una tangente iperbolica. Illustra anche come chiamare il modulo da codice Python. La routine viene implementata prima in Python per illustrare il miglioramento relativo delle prestazioni dell'implementazione della routine stessa in C++.

Questo articolo illustra anche due modi per rendere C++ disponibile a Python:

- Le estensioni CPython standard, illustrate nella [documentazione di Python](https://docs.python.org/3/c-api/).
- [PyBind11](https://github.com/pybind/pybind11), scelta consigliata per C++ 11 per la sua semplicità.

Un confronto tra questi e altri approcci viene illustrato in [Approcci alternativi](#alternative-approaches) alla fine di questo articolo.

L'esempio completato di questa procedura dettagliata è disponibile in [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio 2017 o versioni successive con i carichi di lavoro **Sviluppo di applicazioni desktop con C++** e **Sviluppo Python** installati con le opzioni predefinite.
- Nel carico di lavoro **Sviluppo Python** selezionare anche la casella **Strumenti di sviluppo nativo Python** a destra. Questa opzione imposta la maggior parte della configurazione descritta in questo articolo. Questa opzione include automaticamente anche il carico di lavoro C++.

    ![Selezione dell'opzione Strumenti di sviluppo nativo Python](media/cpp-install-native.png)

    > [!Tip]
    > L'installazione del carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati** include anche Python e l'opzione **Strumenti di sviluppo nativi Python** per impostazione predefinita.

Per altre informazioni, vedere [Installare il supporto di Python per Visual Studio](installing-python-support-in-visual-studio.md), che illustra l'uso di altre versioni di Visual Studio. Se si installa Python separatamente, assicurarsi di selezionare **Download debugging symbols** (Scarica i simboli di debug) e **Download debug binaries** (Scarica file binari di debug) nella sezione **Opzioni avanzate** del programma di installazione. Questa opzione consente di avere a disposizione le librerie di debug necessarie se si sceglie di eseguire una build di debug.

## <a name="create-the-python-application"></a>Creare un'applicazione Python

1. Creare un nuovo progetto di Python in Visual Studio selezionando **File** > **Nuovo** > **Progetto**. Cercare "Python", selezionare il modello **Applicazione Python**, assegnare a questo un nome e un percorso appropriati e selezionare **OK**.

1. L'utilizzo di C++ richiede l'uso di un interprete Python a 32 bit. È consigliato Python 3.6 o versioni successive. Nella finestra **Esplora soluzioni** di Visual Studio espandere il nodo del progetto e quindi il nodo **Ambienti Python**. Se come impostazione predefinita non viene visualizzato un ambiente a 32 bit (in grassetto o con etichetta **impostazioni globali predefinite**), seguire le istruzioni in [Selezionare un ambiente Python per un progetto](selecting-a-python-environment-for-a-project.md). Se non è installato alcun interprete a 32 bit, vedere [Installare interpreti Python](installing-python-interpreters.md).

1. Nel file *.py* del progetto, incollare il codice seguente che effettua il benchmark del calcolo di una tangente iperbolica, implementato senza usare la libreria matematica per un confronto più semplice. È anche possibile immettere il codice manualmente per provare alcune delle [funzionalità di modifica Python](editing-python-code-in-visual-studio.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Eseguire il programma usando **Debug** > **Avvia senza eseguire debug** (**CTRL**+**F5**) per visualizzare i risultati. È possibile cambiare la variabile `COUNT` per modificare il tempo impiegato per l'esecuzione del benchmark. Ai fini di questa procedura dettagliata, impostare il conteggio in modo che il benchmark richieda circa due secondi.

> [!TIP]
> Durante l'esecuzione di benchmark usare sempre **Debug** > **Avvia senza eseguire debug** per evitare l'overhead generato quando si esegue codice nel debugger di Visual Studio.

## <a name="create-the-core-c-projects"></a>Creare i progetti C++ di base

Seguire le istruzioni in questa sezione per creare due progetti C++ identici denominato "superfastcode" e "superfastcode2". In un secondo momento si useranno metodi diversi in ogni progetto per rendere disponibile il codice C++ a Python.

1. Assicurarsi che la variabile di ambiente `PYTHONHOME` venga impostata sull'interprete Python da usare. I progetti C++ in Visual Studio si basano su questa variabile per trovare file come *python.h*, usati durante la creazione di un'estensione Python.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione, quindi scegliere **Aggiungi** > **Nuovo progetto**. Una soluzione Visual Studio può contenere progetti Python e C++ contemporaneamente. Questo è uno dei vantaggi offerti dall'uso di Visual Studio per Python.

1. Cercare "C++", selezionare **Progetto vuoto**, specificare il nome "superfastcode" ("superfastcode2" per il secondo progetto) e selezionare **OK**.

    > [!Tip]
    > Con gli **strumenti di sviluppo nativo Python** installati in Visual Studio è possibile iniziare con il modello **Modulo di estensione Python**, che include gran parte degli elementi descritti di seguito. Questa procedura dettagliata, tuttavia, inizia da un progetto vuoto e illustra la creazione del modulo di estensione in modo dettagliato. Dopo che si è compreso il processo, il modello consente di risparmiare tempo durante la scrittura di estensioni personalizzate.

1. Creare un file C++ nel nuovo progetto facendo clic con il pulsante destro del mouse sul nodo **File di origine**, quindi scegliere **Aggiungi** > **Nuovo elemento**, selezionare **File C++**, assegnare al file il nome `module.cpp` e fare clic su **OK**.

    > [!Important]
    > Un file con estensione *cpp* è necessario per attivare le pagine delle proprietà C++ nei passaggi che seguono.

1. Fare clic con il pulsante destro del mouse sul progetto C++ in **Esplora soluzioni** e scegliere **Proprietà**.

1. Nella parte superiore della finestra di dialogo **Pagine delle proprietà** visualizzata impostare **Configurazione** su **Tutte le configurazioni** e **Piattaforma** su **Win32**.

1. Impostare le proprietà specifiche, come descritto nella tabella seguente e quindi selezionare **OK**.

    | Scheda | Proprietà | Value |
    | --- | --- | --- |
    | **Generale** | **Generale** > **Nome di destinazione** | Specificare il nome del modulo quando si vuole fare riferimento a esso da Python in istruzioni `from...import`. Questo stesso nome viene usato in C++ quando si definisce il modulo per Python. Se si vuole usare il nome del progetto come nome del modulo, lasciare il valore predefinito di **$(ProjectName)**. |
    | | **Generale** > **Estensione di destinazione** | **.pyd** |
    | | **Impostazioni predefinite progetto** > **Tipo di configurazione** | **Libreria dinamica (.dll)** |
    | **C/C++** > **Generale** | **Directory di inclusione aggiuntive** | Aggiungere la cartella *include* di Python nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\include`.  |
    | **C/C++** > **Preprocessore** | **Definizioni del preprocessore** | **Solo CPython**: aggiungere `Py_LIMITED_API;` all'inizio della stringa (incluso il punto e virgola). Questa definizione limita alcune delle funzioni che è possibile chiamare da Python e rende il codice più portatile tra versioni diverse di Python. Se si lavora con PyBind11, non aggiungere questa definizione. In caso contrario, verranno generati errori di compilazione. |
    | **C/C++** > **Generazione codice** | **Libreria di runtime** | **DLL multithread (/MD)** (vedere l'avviso più avanti) |
    | **Linker** > **Generale** | **Directory librerie aggiuntive** | Aggiungere la cartella *libs* di Python che include i file con estensione *lib* nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\libs`. Assicurarsi di indicare la cartella *libs* che contiene i file con estensione *lib* e *non* la cartella *Lib* che contiene i file con estensione *py*. |

    > [!Tip]
    > Se la scheda C/C++ non è visualizzata nelle proprietà del progetto, il progetto non include alcun file identificato come file di origine C/C++. Questa condizione può verificarsi se si crea un file di origine senza un'estensione *c* o *cpp*. Ad esempio, se viene digitato per errore `module.coo` invece di `module.cpp` nella precedente finestra di dialogo del nuovo elemento, Visual Studio crea il file ma non imposta il tipo di file su "Codice C/C+," che attiva la scheda delle proprietà C/C++. Tale errore di identificazione permane anche se si rinomina il file con l'estensione `.cpp`. Per impostare correttamente il tipo di file, fare clic con il pulsante destro del mouse sul file in **Esplora soluzioni**, scegliere **Proprietà** e quindi impostare **Tipo di file** su **Codice C/C++**.

    > [!Warning]
    > Impostare sempre l'opzione **C/C++** > **Generazione codice** > **Libreria di runtime** su **DLL multithread (/MD)**, anche per una configurazione di debug, poiché questa è l'impostazione usata per compilare i file binari Python non di debug. Con CPython, se si imposta l'opzione **DLL di debug multithread (/MDd)**, la creazione di una configurazione **Debug** genera l'errore **C1189: Py_LIMITED_API non è compatibile con Py_DEBUG, Py_TRACE_REFS, e Py_REF_DEBUG**. Inoltre, se si rimuove `Py_LIMITED_API` (obbligatorio con CPython, ma non con PyBind11) per evitare l'errore di compilazione, l'esecuzione di Python si arresta in modo anomalo durante il tentativo di importare il modulo. L'arresto anomalo del sistema si verifica all'interno della chiamata della DLL a `PyModule_Create`, come descritto più avanti, con il messaggio di output **Fatal Python error: PyThreadState_Get: no current thread** (Errore irreversibile di Python: PyThreadState_Get: nessun thread corrente).
    >
    > L'opzione /MDd viene usata per compilare file binari di debug di Python (ad esempio *python_d.exe*), ma la selezione di questa opzione per una DLL di estensione causa sempre un errore di compilazione con `Py_LIMITED_API`.

1. Fare clic con il pulsante destro del mouse sul progetto C++ e selezionare **Compila** per testare le configurazioni sia di **Debug** che di **Release**. I file con estensione *pyd* si trovano nella cartella **solution** all'interno delle sottocartelle **Debug** e **Release**, non nella cartella del progetto C++.

1. Aggiungere il codice seguente al file *module.cpp* del progetto C++:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Compilare di nuovo il progetto C++ per confermare che il codice sia corretto.

1. Se non già stato fatto, ripetere i passaggi precedenti per creare un secondo progetto denominato "superfastcode2" con contenuto identico.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Convertire i progetti C++ in estensioni per Python

Per rendere disponibile la DLL C++ in un'estensione per Python, modificare prima i metodi esportati in modo che interagiscano con i tipi di Python. Aggiungere quindi una funzione che esporti il modulo, insieme alle definizioni dei metodi del modulo.

Le sezioni seguenti illustrano come eseguire questi passaggi con le estensioni CPython e con PyBind11.

### <a name="cpython-extensions"></a>Estensioni CPython

Per informazioni di background su quanto illustrato in questa sezione per Python 3.x, fare riferimento a [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) (Manuale di riferimento dell'API Python/C) e in particolare a [Module Objects](https://docs.python.org/3/c-api/module.html) (Oggetti modulo) in python.org. Ricordarsi di selezionare la versione di Python in uso nell'elenco a discesa in alto a destra per visualizzare la documentazione corretta.

Se si lavora con Python 2.7, fare invece riferimento a [Extending Python 2.7 with C or C++](https://docs.python.org/2.7/extending/extending.html) (Estensione di Python 2.7 con C o C++) e a [Porting Extension Modules to Python 3](https://docs.python.org/2.7/howto/cporting.html) (Conversione dei moduli di estensione per Python 3) (python.org).

1. All'inizio di *module.cpp* includere *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Modificare il metodo `tanh_impl` in modo che accetti e restituisca tipi di Python (ovvero un `PyOjbect*`):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Aggiungere una struttura che definisca come la funzione `tanh_impl` di C++ viene presentata a Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Aggiungere una struttura che definisca il modulo come si vuole farvi riferimento nel codice Python, in particolare quando si usa l'istruzione `from...import`. Fare in modo che questo corrisponda al valore nelle proprietà del progetto in **Proprietà di configurazione** > **Generale** > **Nome di destinazione**. Nell'esempio seguente, il nome di modulo "superfastcode" significa che è possibile usare `from superfastcode import fast_tanh` in Python, perché `fast_tanh` è definito all'interno di `superfastcode_methods`. I nomi di file interni del progetto C++, come *module.cpp*, sono irrilevanti.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Aggiungere un metodo che verrà chiamato da Python quando carica il modulo, che deve essere denominato `PyInit_<module-name>`, dove &lt;module-name&gt; corrisponde esattamente alla proprietà **Generale** > **Nome di destinazione** del progetto C++, ovvero corrisponde al nome del file con estensione *pyd* compilato dal progetto.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Impostare la configurazione di destinazione su **Release** e compilare di nuovo il progetto C++ per verificare il codice. Se si verificano errori, vedere la sezione [Risoluzione dei problemi](#troubleshooting) di seguito.

### <a name="pybind11"></a>PyBind11

Se è stata completata la procedura della sezione precedente, si sarà notato l'uso di una grande quantità di codice boilerplate per creare le strutture di modulo necessarie per il codice C++. PyBind11 semplifica il processo tramite macro in un file di intestazione C++ che ottiene lo stesso risultato con un volume di codice molto più ridotto. Per informazioni generali su quanto illustrato in questa sezione, vedere [PyBind11 basics](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (Informazioni di base su PyBind11) in github.com.

1. Installare PyBind11 usando pip: `pip install pybind11` o `py -m pip install pybind11`.

1. All'inizio di *module.cpp* includere *pybind11.h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. Alla fine di *module.cpp* usare la macro `PYBIND11_MODULE` per definire il punto di ingresso per la funzione C++:

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Impostare la configurazione di destinazione su **Release** e compilare il progetto C++ per verificare il codice. Se si verificano errori, vedere la sezione Risoluzione dei problemi di seguito.

### <a name="troubleshooting"></a>Risoluzione dei problemi

La compilazione del modulo C++ potrebbe non riuscire per i motivi seguenti:

- Impossibile individuare *Python.h* (**E1696: cannot open source file "Python.h"** (E1696: impossibile aprire il file di origine) e/o **C1083: Cannot open include file: "Python.h": No such file or directory** (Impossibile aprire il file di inclusione "Python.h: directory del file inesistente): verificare che il percorso in **C/C++** > **Generale** > **Directory di inclusione aggiuntive** nelle proprietà del progetto punti alla cartella *di inclusione* dell'installazione di Python. Vedere il passaggio 6 in [Creare un progetto di base C++](#create-the-core-c-projects).

- Non è possibile individuare le librerie Python: verificare che il percorso in **Linker** > **Generale** > **Directory librerie aggiuntive** nelle proprietà del progetto punti alla cartella *libs* dell'installazione di Python in uso. Vedere il passaggio 6 in [Creare un progetto di base C++](#create-the-core-c-projects).

- Errori del linker correlati all'architettura di destinazione: modificare l'architettura di progetto della destinazione C++ in modo che corrisponda a quella dell'installazione di Python in uso. Ad esempio, se il progetto C++ è destinato a x64, ma l'installazione di Python è x86, impostare x86 come destinazione del progetto C++.

## <a name="test-the-code-and-compare-the-results"></a>Testare il codice e confrontare i risultati

Ora che la libreria è strutturata con le estensioni per Python, è possibile fare riferimento a tali estensioni dal progetto Python, importare il modulo e usare i metodi delle estensioni.

### <a name="make-the-dll-available-to-python"></a>Rendere disponibile la DLL per Python

Ci sono due modi per rendere disponibile la DLL per Python.

Il primo metodo funziona se il progetto Python e il progetto C++ sono nella stessa soluzione. Passare a **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nodo **Riferimenti** nel progetto Python e quindi scegliere **Aggiungi riferimento**. Nella finestra di dialogo visualizzata selezionare la scheda **Progetti**, selezionare il progetto **superfastcode** e il progetto **superfastcode2**, quindi fare clic su **OK**.

![Aggiunta di un riferimento al progetto superfastcode](media/cpp-add-reference.png)

Il metodo alternativo, descritto nei passaggi seguenti, consente di installare il modulo nell'ambiente di Python globale, rendendolo disponibile anche per altri progetti Python. Questo in genere richiede di aggiornare il database di completamento IntelliSense per tale ambiente in Visual Studio 2017 versione 15.5 e versioni successive. L'aggiornamento è necessario anche quando si rimuove il modulo dall'ambiente.

1. Se si usa Visual Studio 2017 o versioni successive eseguire il programma di installazione di Visual Studio, selezionare **Modifica**, selezionare **Singoli componenti** > **Compilatori, strumenti di compilazione e runtime** > **Set di strumenti di Visual C++ 2015.3 v140**. Questo passaggio è necessario perché Python (per Windows) è esso stesso compilato con Visual Studio 2015 (versione 14.0) e richiede la disponibilità di questi strumenti quando compila un'estensione tramite il metodo descritto in questo argomento. Si noti che può essere necessario installare una versione a 32 bit di Python e usare come destinazione della DLL Win32 e non x64.

1. Creare un file denominato *setup.py* nel progetto C++ facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Aggiungi** > **Nuovo elemento**. Selezionare quindi **File di C++ (.cpp)**, assegnare il nome `setup.py` al file e selezionare **OK**. L'assegnazione di un nome al file con estensione *py* consente di fare in modo che Visual Studio lo riconosca come Python nonostante l'uso del modello di file C++. Quando il file viene visualizzato nell'editor, incollare nel file il codice seguente in base al metodo di estensione:

    **Estensioni CPython (progetto superfastcode):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Per documentazione su questo script, vedere [Building C and C++ Extensions](https://docs.python.org/3/extending/building.html) (Compilazione di estensioni C e C++) in python.org.

    **PyBind11 (progetto superfastcode2):**

    ```python
    import os, sys

    from distutils.core import setup, Extension
    from distutils import sysconfig

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2', sources = ['module.cpp'],
        include_dirs=['pybind11/include'],
        language='c++',
        extra_compile_args = cpp_args,
        )

    setup(
        name = 'superfastcode2',
        version = '1.0',
        description = 'Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules = [sfc_module],
    )
    ```

1. Il codice *setup.py* indica a Python di compilare l'estensione usando il set di strumenti di Visual Studio 2015 C++ dalla riga di comando. Aprire un prompt dei comandi con privilegi elevati, passare alla cartella contenente il progetto C++, ovvero la cartella contenente *setup.py*, e immettere il comando seguente:

    ```command
    pip install .
    ```

    oppure:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Chiamare la DLL da Python

Dopo aver reso disponibili a Python le DLL come descritto nella sezione precedente, è ora possibile chiamare le funzioni `superfastcode.fast_tanh` e `superfastcode2.fast_tanh2` dal codice Python e confrontarne le prestazioni con l'implementazione Python:

1. Aggiungere le righe seguenti al file con estensione *py* per chiamare i metodi esportati dalle DLL e visualizzarne l'output:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Eseguire il programma Python (**Debug** > **Avvia senza eseguire debug** o **CTRL**+**F5**) e osservare che le routine C++ vengono eseguite da 5 a 20 volte più velocemente dell'implementazione Python. In genere l'output ha l'aspetto seguente:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Se il comando **Avvia senza eseguire debug** è disabilitato, fare clic con il pulsante destro del mouse sul progetto Python in **Esplora soluzioni** e scegliere **Imposta come progetto di avvio**.

1. Provare a incrementare la variabile `COUNT` in modo che le differenze siano più evidenti. Una build di **Debug** del modulo C++ viene anche eseguita più lentamente rispetto a una build di **Release** perché la build di **Debug** è meno ottimizzata e contiene vari controlli degli errori. È possibile alternare liberamente queste configurazioni ai fini del confronto.

> [!NOTE]
> Nell'output si noterà che l'estensione PyBind11 non è veloce come l'estensione CPython, pur essendo comunque molto più veloce dell'implementazione diretta di Python. La differenza è dovuta a una piccola quantità di overhead per ogni chiamata che PyBind11 introduce per semplificare notevolmente l'interfaccia di C++. Questa differenza per ogni chiamata è di fatto quasi trascurabile, ma il codice di test chiama le funzioni di estensione 500.000 volte, per cui i risultati registrati in questo contesto permettono di notare l'overhead. In genere una funzione di C++ esegue molte più operazioni rispetto ai semplici metodi `fast_tanh[2]` usati qui, per cui l'overhead diventa irrilevante. Se tuttavia si implementano metodi che possono essere chiamati migliaia di volte al secondo, l'approccio CPython può far registrare prestazioni migliori rispetto a PyBind11.

## <a name="debug-the-c-code"></a>Eseguire il debug del codice C++

Visual Studio supporta il debug di codice Python e C++ insieme. Questa sezione illustra il processo usando il progetto **superfastcode**. I passaggi sono identici per il progetto **superfastcode2**.

1. Fare clic con il pulsante destro del mouse sul progetto Python in **Esplora soluzioni**, scegliere **Proprietà**, selezionare la scheda **Debug** e quindi selezionare l'opzione **Debug** > **Abilita debug codice nativo**.

    > [!Tip]
    > Quando si abilita il debug del codice nativo, è possibile che la finestra di output di Python venga chiusa quando il programma avrà terminato l'operazione, senza che venga visualizzato il consueto messaggio **Premere un tasto qualsiasi per continuare**. Per specificare una pausa, aggiungere l'opzione `-i` al campo **Esegui** > **Argomenti dell'interprete** della scheda **Debug** quando si abilita il debug del codice nativo. Questo argomento fa passare l'interprete di Python in modalità interattiva al termine del codice e attende che vengano premuti **CTRL**+**Z** > **INVIO** per uscire. In alternativa, se si vuole modificare il codice Python, è possibile aggiungere le istruzioni `import os` e `os.system("pause")` alla fine del programma. Questo codice duplica la richiesta di pausa originale.

1. Selezionare **File** > **Salva** per salvare le modifiche delle proprietà.

1. Impostare la configurazione della build su **Debug** sulla barra degli strumenti di Visual Studio.

    ![Impostazione della configurazione di build su Debug](media/cpp-set-debug.png)

1. Dato che l'esecuzione del codice richiede in genere più tempo nel debugger, può essere utile modificare la variabile `COUNT` nel file con estensione *py* impostando un valore inferiore di circa cinque volte, ad esempio modificarlo da `500000` a `100000`.

1. Nel codice C++ impostare un punto di interruzione nella prima riga del metodo `tanh_impl` e quindi avviare il debugger (**F5** o **Debug** > **Avvia debug**). Il debugger interrompe l'esecuzione quando viene chiamato tale codice. Se non viene raggiunto il punto di interruzione, controllare che la configurazione sia impostata su **Debug** e di aver salvato il progetto, operazione che non viene eseguita automaticamente all'avvio del debugger.

    ![Interruzione in un punto del codice C++](media/cpp-debugging.png)

1. A questo punto è possibile eseguire il codice C++ istruzione per istruzione, esaminare le variabili e così via. Queste funzionalità sono descritte in dettaglio in [Debug contemporaneo di codice Python e C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Approcci alternativi

Esistono svariati modi per creare estensioni di Python, come descritto nella tabella seguente. Le prime due voci relative a CPython e PyBind11 sono state oggetto di discussione in questo articolo.

| Approccio | Anno | Utenti rappresentanti | Vantaggi | Svantaggi |
| --- | --- | --- | --- | --- |
| Moduli di estensione C/C++ per CPython | 1991 | Libreria standard | [Documentazione ampia ed esercitazioni](https://docs.python.org/3/c-api/). Controllo totale. | Compilazione, portabilità, gestione dei riferimenti. Conoscenza elevata di C. |
| [PyBind11](https://github.com/pybind/pybind11) (scelta consigliata per C++) | 2015 |  | Libreria leggera, di sola intestazione per la creazione di associazioni Python di codice C++ esistente. Poche dipendenze. Compatibilità PyPy. | Più recente, meno maturo. Uso intenso di funzionalità C++11. Breve elenco di compilatori supportati (Visual Studio è incluso). |
| Cython (consigliato per C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Simile a Python. Altamente maturo. Prestazioni elevate. | Compilazione, nuova sintassi, nuova toolchain. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Funziona con quasi tutti i compilatori C++. | Gruppo di librerie complesso e di grandi dimensioni. Contiene molte soluzioni alternative per i compilatori non recenti. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Nessuna compilazione, ampia disponibilità. | Accesso e modifica di strutture C complesse e soggette a errori. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Genera associazioni per molte lingue contemporaneamente. | Sovraccarico eccessivo se Python è l'unica destinazione. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](https://pypy.org/) | Facilità di integrazione, compatibilità PyPy. | Più recente, meno maturo. |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | Simile a cffi con l'uso di C++. | Più recente, potrebbero verificarsi alcuni problemi con Visual Studio 2017. |

## <a name="see-also"></a>Vedere anche

L'esempio completato di questa procedura dettagliata è disponibile in [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
