---
title: Impostazione di un repository Subversion
description: Uso di Subversion in Visual Studio per Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: 7dfb5c645125afc1485c1422909e52741507b327
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988215"
---
# <a name="set-up-a-subversion-repository"></a>Impostare un repository Subversion

Subversion è un _sistema di controllo della versione_ centralizzato e ciò significa che vi è un unico server che contiene tutti i file e le revisioni da cui gli utenti possono estrarre qualsiasi versione di qualsiasi file. Quando i file vengono estratti da un repository Subversion remoto, l'utente riceve uno snapshot del repository in tale momento.

Per usare Subversion per il controllo della versione, deve essere installato nel computer in uso. Per verificare se Subversion è installato nel computer in uso, usare il comando seguente in Terminale:

```bash
svn --version
```

Questo comando restituisce il numero di versione.

Se Subversion non è già installato, il modo più semplice per ottenerlo consiste nell'installare gli _strumenti della riga di comando Xcode_. Usare il comando seguente per installare gli strumenti da riga di comando Xcode e Subversion.

```bash
xcode-select --install
```

Dopo aver installato Subversion nel computer, usare la procedura seguente per pubblicare il progetto in SVN.

1. Creare un repository SVN gratuito online. In questo esempio è stato usato [Assembla](https://app.assembla.com/). Dopo la creazione, verrà reso disponibile un URL che consentirà di connettersi al repository:

    ![copiare l'URL di SVN](media/version-control-subversion1-sml.png)

2. Aprire o creare un progetto Visual Studio per Mac.

3. Fare clic con il pulsante destro del mouse sul progetto e selezionare **Controllo della versione > Pubblica in controllo della versione...**:

    ![Avviare la pubblicazione del progetto](media/version-control-subversion2.png)

4. Nella scheda **Connetti al repository** selezionare **Subversion** nell'elenco a discesa in alto.

5. Inserire l'URL del passaggio 1. Dopo avere immesso l'URL, gli altri campi vengono compilati per impostazione predefinita:

    ![Finestra di dialogo di selezione del repository e di immissione dei dettagli](media/version-control-subversion3.png)

7. Fare clic su **OK** e quindi confermare premendo **Pubblica**.

7. Se richiesto, immettere le proprie credenziali per il sito in cui si crea il repository, come illustrato di seguito:

    ![Immissione delle credenziali per il repository Subversion](media/version-control-subversion5.png)

8. Tutti i comandi di controllo della versione disponibili verranno visualizzati nel menu del controllo della versione.

## <a name="see-also"></a>Vedere anche

- [Uso di Subversion](working-with-subversion.md)