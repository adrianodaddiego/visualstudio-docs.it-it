---
title: Controllo della versione
description: Uso di Git e Subversion in Visual Studio per Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 0505177e01afd701fe5506df7dd0fc2a2e1f859c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62986528"
---
# <a name="version-control"></a>Controllo della versione

Il controllo della versione è un sistema per la gestione di file in molte versioni diverse e, nello sviluppo di software, vi partecipano generalmente molti sviluppatori. Lo scopo principale di qualsiasi sistema di controllo della versione (_VCS_) è trovare una soluzione che consenta a tutti gli utenti di lavorare contemporaneamente sulla codebase.

Il centro di ogni sistema di controllo della versione è un _repository_ che funge da archivio di dati centrale per tutti i diversi file, analogamente a un file server. Tuttavia, a differenza di un file server, il repository contiene l'intera cronologia del progetto e tutte le revisioni che sono state effettuate.

Dal momento che il repository è l'archivio dati centrali, è logico che ogni utente abbia un archivio locale di dati su cui possa lavorare. Questo archivio è denominato _copia di lavoro_. In Visual Studio per Mac la copia di lavoro si presenza come qualsiasi altra directory locale nel computer, in cui è possibile leggere e scrivere su qualsiasi dei file. Tuttavia, poiché Visual Studio per Mac offre l'integrazione del sistema di controllo della versione, è possibile usare Subversion e Git senza lasciare l'IDE.

Subversion è un sistema di controllo della versione centralizzato e ciò significa che vi è un unico server che contiene tutti i file e le revisioni da cui gli utenti possono estrarre qualsiasi versione di qualsiasi file. Quando i file vengono estratti da un repository Subversion remoto, l'utente riceve uno snapshot del repository in tale momento.

Git è un sistema di controllo della versione della versione distribuito che consente ai team di lavorare contemporaneamente sugli stessi documenti. Con Git può essere presente un unico server che contiene tutti i file ma l'intero repository viene clonato localmente nel computer in uso ogni volta che viene estratto un repository da questa origine centrale.

## <a name="basic-concepts"></a>Concetti di base

Visual Studio per Mac offre supporto per entrambi i sistemi di controllo della versione Git e Subversion. Gli articoli seguenti illustrano come impostare i repository di Git e Subversion tramite Visual Studio per Mac e descrivono funzionalità semplici, quali ad esempio la revisione, il commit e il push delle modifiche.

* [Impostazione di un repository Git](set-up-git-repository.md)
* [Uso di Git](working-with-git.md)
* [Impostazione di un repository Subversion](set-up-subversion-repository.md)
* [Uso di Subversion](working-with-subversion.md)

## <a name="see-also"></a>Vedere anche

* [Controllo della versione in Visual Studio (in Windows)](/visualstudio/version-control/)