---
title: Uso di Subversion
description: Uso di Subversion in Visual Studio per Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: 7dcbd619fe0c1a0ab84a8667f5a781d006f80999
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62985531"
---
# <a name="working-with-subversion"></a>Uso di Subversion

Subversion è il sistema di controllo della versione centralizzato che consente di estrarre una singola copia master dei dati centralizzati. A differenza di Git, l'estrazione di un repository Subversion non clona l'intero repository, crea solo uno snapshot in questo punto nel tempo.

Subversion usa un modello copia-modifica-unione per consentire agli utenti di lavorare contemporaneamente sullo stesso repository. Ciò significa che ogni utente crea una copia locale, o di lavoro, dei dati centralizzati, su cui può lavorare in modo indipendente. Le modifiche apportate alle copie di lavoro degli utenti vengono unite in modo cronologico.

Ad esempio, supporre che sia l'utente A che l'utente B estraggano una copia dal repository remoto e che ognuno modifichi i file. L'utente A completa le modifiche e ne esegue il commit remoto. Prima che l'utente B esegua il commit del suo lavoro, deve aggiornare la sua copia di lavoro con le modifiche dal repository remoto e pertanto unire le modifiche apportate dall'utente A.

Le sezioni seguenti illustrano come sia possibile usare Subversion per il controllo della versione in Visual Studio per Mac.

L'immagine seguente illustra le opzioni offerte da Visual Studio per Mac dalla voce di menu Controllo della versione:

![Voci di menu Controllo della versione](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Estrai...

Prima di iniziare a usare un repository Subversion remoto, estrarre il repository per creare una copia di lavoro di tale directory nel computer locale.

Per informazioni sull'uso della funzionalità **Estrai** in Visual Studio per Mac, seguire la procedura riportata nella sezione [Impostazione di un repository Subversion](set-up-subversion-repository.md).

## <a name="update-solution"></a>Aggiorna soluzione

Quando si usa un repository remoto, è importante tenere presente che è possibile che altri utenti modifichino i file e che pertanto la propria copia di lavoro non sia aggiornata. Per evitare conflitti, è sempre consigliabile eseguire il pull di tutte le modifiche dal repository alla propria soluzione prima di iniziare il lavoro e prima di eseguire il commit. Per eseguire il pull delle modifiche, selezionare la voce di menu **Controllo della versione > Aggiorna soluzione**.

## <a name="review-solution-and-commit"></a>Rivedi soluzione ed esegui commit

Per rivedere le modifiche nei file, usare le schede Modifiche, Segnala errore, Log e Unisci in ogni documento, come illustrato nell'immagine seguente:

![Schede del controllo della versione](media/version-control-vcTabs.png)

Rivedere tutte le modifiche di un progetto spostandosi sulla voce di menu **Controllo della versione > Rivedi soluzione ed esegui commit**:

![Revisione della soluzione](media/version-control-vcStatus.png)

Ciò consente di visualizzare tutte le modifiche in ogni file di un progetto con l'opzione di annullarle, creare una patch o eseguire il commit.

Per eseguire il commit di un file in un repository remoto, premere Commit..., inserire un messaggio di commit e confermare con il pulsante Commit:

![Commit di un file](media/version-control-svnCommit.png)

In questo modo si invieranno le modifiche al repository dove verrà creata la nuova revisione di tutte le modifiche.

## <a name="see-also"></a>Vedere anche

- [Impostare un repository Subversion](set-up-subversion-repository.md)
