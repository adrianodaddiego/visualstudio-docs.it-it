---
title: Informazioni sull'esercitazione Flask in Visual Studio, passaggio 3, file statici e pagine
titleSuffix: ''
description: Procedura dettagliata sui concetti di base relativi a Flask nel contesto dei progetti di Visual Studio, che illustra, in particolare, come rendere disponibili file statici, aggiungere pagine all'app e usare l'ereditarietà dei modelli
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d9d6f94a81eb97cb06820381ba09e13d4bdeb9d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62957188"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Passaggio 3: Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli

**Passaggio precedente: [Creare un'app Flask con visualizzazioni e modelli di pagina](learn-flask-visual-studio-step-02-create-app.md)**

Nei passaggi precedenti di questa esercitazione si è appreso come creare un'app Flask di base con una singola pagina di codice HTML autonomo. Le app Web moderne, tuttavia, sono in genere costituite da numerose pagine e usano risorse condivise, come file CSS e JavaScript, per offrire un comportamento e uno stile coerenti.

In questo passaggio viene descritto come:

> [!div class="checklist"]
> - Usare i modelli di elementi di Visual Studio per aggiungere rapidamente nuovi file di tipi diversi con un comodo codice boilerplate (passaggio 3-1)
> - Usare i file statici dal codice (passaggio 3-2, facoltativo)
> - Aggiungere altre pagine all'app (passaggio 3-3)
> - Usare l'ereditarietà dei modelli per creare un'intestazione e una barra di spostamento usate in più pagine (passaggio 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Passaggio 3-1: Acquisire familiarità con i modelli di elementi

Quando si sviluppa un'app Flask, si aggiungono in genere molti altri file Python, HTML, CSS e JavaScript. Per ogni tipo di file (come pure per altri file, come *web.config*, che potrebbero essere necessari per la distribuzione), Visual Studio offre comodi [modelli di elementi](python-item-templates.md) da cui iniziare.

Per visualizzare i modelli disponibili, passare a **Esplora soluzioni**, fare clic con il pulsante destro del mouse sulla cartella in cui si vuole creare l'elemento e scegliere **Aggiungi** > **Nuovo elemento**:

![Finestra di dialogo Aggiungi nuovo elemento in Visual Studio](media/flask/step03-add-new-item-dialog.png)

Per usare un modello, selezionare il modello desiderato, specificare un nome per il file e selezionare **OK**. Aggiungendo un elemento in questo modo il file viene aggiunto automaticamente al progetto di Visual Studio e vengono contrassegnate le modifiche per il controllo del codice sorgente.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Domanda: In che modo Visual Studio individua i modelli di elementi da offrire?

Risposta: Il file di progetto di Visual Studio (con estensione *pyproj*) contiene un identificatore del tipo di progetto che lo contrassegna come progetto Python. Visual Studio usa questo identificatore di tipo per mostrare solo i modelli di elementi appropriati per il tipo di progetto. In questo modo, Visual Studio può fornire un set completo di modelli di elementi per numerosi tipi di progetti senza che sia necessario che l'utente li esamini tutti ogni volta.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Passaggio 3-2: Rendere disponibili file statici dall'app

In un'app Web compilata con Python (usando qualsiasi framework), i file Python vengono sempre eseguiti nel server dell'host Web e non vengono mai trasmessi al computer dell'utente. Altri file, tuttavia, ad esempio CSS e JavaScript, vengono usati esclusivamente dal browser, quindi il server host si limita a fornirli così come sono ogni volta che vengono richiesti. Tali file sono detti file "statici" e Flask può renderli automaticamente disponibili senza che sia necessario scrivere codice. All'interno dei file HTML, ad esempio, è possibile fare riferimento ai file statici usando un percorso relativo nel progetto. Nella prima sezione di questo passaggio viene aggiunto un file CSS al modello di pagina esistente.

Se è necessario rendere disponibile un file statico dal codice, ad esempio tramite l'implementazione di un endpoint API, Flask offre un metodo pratico che consente di far riferimento ai file usando percorsi relativi all'interno di una cartella denominata *static* (nella radice del progetto). La seconda sezione di questo passaggio illustra tale metodo usando un file di dati statico semplice.

In ogni caso è possibile organizzare i file in *static* come si vuole.

### <a name="use-a-static-file-in-a-template"></a>Usare un file statico in un modello

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla cartella **HelloFlask** nel progetto di Visual Studio, selezionare **Aggiungi** > **Nuova cartella** e assegnare alla cartella il nome `static`.

1. Fare clic con il pulsante destro del mouse sulla cartella **static** e scegliere **Aggiungi** > **Nuovo elemento**. Nella finestra di dialogo visualizzata selezionare il modello **Foglio di stile**, assegnare al file il nome `site.css` e selezionare **OK**. Il file **site.css** viene visualizzato nel progetto e aperto nell'editor. La struttura di cartelle dovrebbe essere simile a quella nella figura seguente:

    ![Struttura di file statici come visualizzato in Esplora soluzioni](media/flask/step03-static-file-structure.png)

1. Sostituire il contenuto di *site.css* con il codice seguente e salvare il file:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Sostituire il contenuto del file *templates/index.html* dell'app con il codice seguente che sostituisce l'elemento `<strong>` usato nel passaggio 2 con un elemento `<span>` che fa riferimento alla classe di stile `message`. L'uso di una classe di stile in questo modo offre maggiore flessibilità nell'applicazione degli stili all'elemento.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Eseguire il progetto per osservare i risultati. Al termine, arrestare l'app ed eseguire il commit delle modifiche nel controllo del codice sorgente, se necessario (come illustrato nel [passaggio 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Usare un file statico dal codice

Flask offre una funzione denominata `serve_static_file` che può essere chiamata dal codice per fare riferimento a qualsiasi file all'interno della cartella *static* del progetto. Il processo seguente crea un endpoint API semplice che restituisce un file di dati statico.

1. Se non è già stato fatto, creare una cartella *static*: in **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla cartella **HelloFlask** nel progetto di Visual Studio, selezionare **Aggiungi** > **Nuova cartella** e assegnare alla cartella il nome `static`.

1. Nella cartella *static* creare un file di dati JSON statico denominato *data.json* con il contenuto seguente (sono dati di esempio senza significato):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. In *views.py* aggiungere una funzione con la route /api/data che restituisce il file di dati statico usando il metodo `send_static_file`:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Eseguire l'app e passare all'endpoint /api/data per verificare che venga restituito il file statico. Al termine, arrestare l'app.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Domanda: Ci sono convenzioni per organizzare i file statici?

Risposta: È possibile aggiungere altri file CSS, JavaScript e HTML nella cartella *static* a propria discrezione. Un modo tipico per organizzare i file statici consiste nel creare sottocartelle denominate *fonts*, *scripts* e *content* (per i fogli di stile e qualsiasi altro file).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Domanda: Come si gestiscono le variabili di URL e i parametri di query in un'API?

Risposta: Vedere la risposta nel passaggio 1-4 per la [Domanda: Come funziona Flask con route di URL e parametri di query variabili?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Passaggio 3-3: Aggiungere una pagina all'app

L'aggiunta di un'altra pagina all'app comporta quanto segue:

- Aggiunta di una funzione Python che definisce la visualizzazione.
- Aggiunta di un modello per il markup della pagina.
- Aggiunta del routing necessario al file *urls.py* del progetto Flask.

I passaggi seguenti aggiungono una pagina "About" al progetto "HelloFlask", nonché collegamenti a tale pagina dalla home page:

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla cartella **templates**, selezionare **Aggiungi** > **Nuovo elemento**, selezionare il modello di elemento **Pagina HTML**, assegnare al file il nome `about.html` e selezionare **OK**.

    > [!Tip]
    > Se il comando **Nuovo elemento** non è visualizzato nel menu **Aggiungi**, verificare di aver arrestato l'app in modo che Visual Studio esca dalla modalità di debug.

1. Sostituire il contenuto di *about.html* con il markup seguente (il collegamento esplicito alla home page viene sostituito con una barra di spostamento semplice nel passaggio 3-4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Aprire il file *views.py* dell'app e aggiungere una funzione denominata `about` che usa il modello:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Aprire il file *templates/index.html* e aggiungere la riga seguente all'interno dell'elemento `<body>` per inserire un collegamento alla pagina About (anche in questo caso il collegamento viene sostituito con una barra di spostamento nel passaggio 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Salvare tutti i file con il comando di menu **File** > **Salva tutto** oppure premere **CTRL**+**MAIUSC**+**S**. Tecnicamente, questo passaggio non è necessario in quanto eseguendo il progetto in Visual Studio i file vengono salvati automaticamente. Ciononostante, si tratta di un comando utile da conoscere.

1. Eseguire il progetto per osservare i risultati e controllare lo spostamento tra le pagine. Al termine, arrestare l'app.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Domanda: Il nome di una funzione di pagina è rilevante per Flask?

Risposta: No, perché è l'elemento Decorator `@app.route` che determina gli URL per cui Flask chiama la funzione per generare una risposta. Gli sviluppatori in genere fanno corrispondere il nome della funzione alla route, ma tale corrispondenza non è obbligatoria.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Passaggio 3-4: Usare l'ereditarietà dei modelli per creare un'intestazione e una barra di spostamento

Invece di usare collegamenti di spostamento espliciti in ogni pagina, le app Web moderne usano in genere un'intestazione personalizzata e una barra di spostamento che fornisce i collegamenti alle pagine più importanti, i menu di scelta rapida e così via. Per assicurarsi che l'intestazione e la barra di spostamento siano uguali in tutte le pagine, tuttavia, non è necessario ripetere lo stesso codice in ogni modello di pagina. È invece possibile definire le parti comuni di tutte le pagine in un'unica posizione.

Il sistema di modelli di Flask (Jinja per impostazione predefinita) offre due modi per riusare elementi specifici in più modelli: le inclusioni e l'ereditarietà.

- Le *inclusioni* sono altri modelli di pagina che vengono inseriti in un punto specifico nel modello di riferimento usando la sintassi `{% include <template_path> %}`. È anche possibile usare una variabile se si vuole modificare il percorso in modo dinamico nel codice. Le inclusioni vengono in genere usate nel corpo di una pagina per eseguire il pull nel modello condiviso in una posizione specifica della pagina.

- L'*ereditarietà* usa l'elemento `{% extends <template_path> %}` all'inizio di un modello di pagina per specificare un modello di base condiviso su cui è basato il modello di riferimento. L'ereditarietà viene comunemente usata per definire un layout condiviso, la barra di spostamento e altre strutture per le pagine dell'app, in modo che i modelli di riferimento debbano solo aggiungere o modificare aree specifiche del modello di base, dette *blocchi*.

In entrambi i casi `<template_path>` è relativo alla cartella *templates* dell'app (è consentito anche l'uso di `../` o `./`).

Un modello di base delinea i *blocchi* usando i tag `{% block <block_name> %}` e `{% endblock %}`. Se un modello di riferimento usa quindi tag con lo stesso nome di blocco, il contenuto del blocco esegue l'override di quello del modello di base.

I passaggi seguenti illustrano l'ereditarietà:

1. Nella cartella *templates* dell'app creare un nuovo file HTML (usando il menu di scelta rapida **Aggiungi** > **Nuovo elemento** o **Aggiungi** > **Pagina HTML**) denominato *layout.html* e sostituirne il contenuto con il markup riportato di seguito. È possibile notare che questo modello contiene un blocco denominato "content" che è quello che le pagine di riferimento devono sostituire:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Aggiungere gli stili seguenti al file *static/site.css* dell'app (questa procedura dettagliata non mira a illustrare la progettazione reattiva e questi stili servono semplicemente per generare un risultato interessante):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Modificare *templates/index.html* per fare riferimento al modello di base ed eseguire l'override del blocco di contenuto. È possibile notare che usando l'ereditarietà questo modello diventa semplice:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modificare anche *templates/about.html* per fare riferimento al modello di base ed eseguire l'override del blocco di contenuto:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Eseguire il server per osservare i risultati. Al termine, arrestare il server.

    ![App in esecuzione con la barra di spostamento](media/flask/step03-nav-bar.png)

1. Poiché sono state apportate modifiche sostanziali all'app, è di nuovo il momento di [eseguire il commit delle modifiche nel controllo del codice sorgente](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Usare il modello Progetto Web Flask completo](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Approfondimento

- [Distribuire l'app Web nel Servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Per altre funzionalità dei modelli Jinja, ad esempio il flusso di controllo, vedere la [documentazione relativa alla progettazione dei modelli Jinja](http://jinja.pocoo.org/docs/2.10/templates) (jinja.pocoo.org)
- Per informazioni dettagliate sull'uso di `url_for`, vedere [url_for](http://flask.pocoo.org/docs/1.0/api/?highlight=url_for#flask.url_for) nella documentazione dell'oggetto applicazione Flask (flask.pocoo.org)
- Codice sorgente dell'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
