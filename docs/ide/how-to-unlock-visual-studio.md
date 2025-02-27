---
title: 'Procedura: Sbloccare Visual Studio'
titleSuffix: ''
ms.date: 03/30/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 2bb6de32188abb11e0286c200383bdb1e8fb12f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62549201"
---
# <a name="how-to-unlock-visual-studio"></a>Procedura: Sbloccare Visual Studio

È possibile valutare gratuitamente Visual Studio per un massimo di 30 giorni. L'accesso all'IDE estende il periodo di valutazione di 90 giorni. Per continuare a usare Visual Studio, sbloccare l'IDE in uno dei modi seguenti:

- usando un abbonamento online

- immettendo un codice Product Key

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Per sbloccare Visual Studio usando un abbonamento online

Per sbloccare Visual Studio usando una sottoscrizione di Visual Studio o un'organizzazione di Azure DevOps associata a un account Microsoft o un account aziendale o dell'istituto di istruzione:

1. Scegliere il pulsante **Accedi** nell'angolo superiore destro dell'IDE oppure scegliere **File** > **Impostazioni account** per aprire la finestra di dialogo **Impostazioni account** e scegliere il pulsante **Accedi**.

1. Immettere le credenziali per un account Microsoft oppure un account aziendale o dell'istituto di istruzione. Visual Studio individua una sottoscrizione di Visual Studio o un'organizzazione di Azure DevOps associata all'account.

> [!IMPORTANT]
> Visual Studio cerca automaticamente le sottoscrizioni online associate quando ci si connette a un'organizzazione di Azure DevOps dalla finestra dello strumento **Team Explorer**. Quando ci si connette a un'organizzazione di Azure DevOps, si può accedere sia con un account Microsoft, sia con un account aziendale o dell'istituto di istruzione. Se è disponibile un abbonamento online per l'account utente, Visual Studio sbloccherà automaticamente l'IDE.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Per sbloccare Visual Studio con un codice Product Key

1. Selezionare **File** > **Impostazioni account** per aprire la finestra di dialogo **Impostazioni account** e quindi scegliere il collegamento **Licenza con codice Product Key**.

1. Immettere il codice Product Key nell'apposita casella.

> [!TIP]
> Le versioni preliminari di Visual Studio non includono codici Product Key. Per usare le versioni preliminari, è necessario accedere all'IDE.

## <a name="address-license-problem-states"></a>Risolvere i problemi di licenza

### <a name="update-stale-licenses"></a>Aggiornare le licenze non aggiornate

 È possibile che sia stato visualizzato il messaggio seguente, che indica che la licenza sta per diventare obsoleta in Visual Studio. Il messaggio è "La licenza è diventata obsoleta e deve essere aggiornata."

 ![Messaggio di licenza non aggiornata di Visual Studio](../ide/media/vs2017_stale-license.png)

 Questo messaggio indica che, anche se è possibile che l'abbonamento sia ancora valido, il token della licenza usato da Visual Studio per mantenere aggiornata la sottoscrizione non è stato aggiornato ed è diventato obsoleto per uno dei motivi seguenti:

- Visual Studio non è stato usato o non è stata disponibile alcuna connessione a Internet per un lungo periodo di tempo.
- È stata effettuata la disconnessione da Visual Studio.

Prima che il token della licenza diventi obsoleto, Visual Studio visualizza un messaggio di avviso che richiede di immettere nuovamente le credenziali.

Se non si immettono di nuovo le credenziali, il token inizia a diventare obsoleto e la finestra di dialogo **Impostazioni account** indica il numero di giorni rimanenti prima della scadenza completa del token. Dopo la scadenza del token, è necessario immettere nuovamente le credenziali per l'account prima di continuare a usare Visual Studio.

> [!Important]
> Se si usa Visual Studio per lunghi periodi di tempo in ambienti con accesso a Internet assente o limitato, è consigliabile usare un codice Product Key per sbloccare Visual Studio ed evitare interruzioni.

### <a name="update-expired-licenses"></a>Aggiornare le licenze scadute

 Se l'abbonamento è completamente scaduto e non si hanno più i diritti di accesso a Visual Studio, è necessario rinnovare l'abbonamento o aggiungere un altro account con abbonamento. Per visualizzare altre informazioni sulla licenza in uso, passare a **File** > **Impostazioni account** e quindi verificare le informazioni sulla licenza nella parte destra della finestra di dialogo. Se si ha un altro abbonamento associato a un account diverso, aggiungere l'account all'elenco **Tutti gli account** sul lato sinistro della finestra di dialogo selezionando il collegamento **Aggiungi un account**.

## <a name="see-also"></a>Vedere anche

* [Accedere a Visual Studio](../ide/signing-in-to-visual-studio.md)
