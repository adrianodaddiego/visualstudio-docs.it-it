---
title: Il debug di applicazioni ClickOnce che usano System
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d70697e3523fcb12384cb51415f73ebd210f45c9
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66262006"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Debug di applicazioni ClickOnce in cui si usa System.Deployment.Application
Nelle [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione consente di configurare la modalità di aggiornamento di un'applicazione. Tuttavia, se si desidera usare e personalizzare advanced [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funzionalità di distribuzione, è necessario accedere al modello di oggetto di distribuzione fornito da <xref:System.Deployment.Application>. È possibile usare il <xref:System.Deployment.Application> API per attività avanzate, ad esempio:

- Creazione di un'opzione "Aggiorna" nell'applicazione

- Il download su richiesta condizionale, dei vari componenti dell'applicazione

- Aggiornamenti integrati direttamente nell'applicazione

- Garantendo che l'applicazione client sia sempre aggiornato

  Poiché il <xref:System.Deployment.Application> API funzionano solo quando un'applicazione viene distribuita con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia, l'unico modo per eseguirne il debug consiste nel distribuire l'applicazione usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], connettersi a essa e quindi eseguirne il debug. Può essere difficile collegare il debugger in tempo, perché spesso questo codice viene eseguito quando l'applicazione si avvia e viene eseguito prima di collegare il debugger. Una soluzione consiste nell'inserire l'interruzione (o viene arrestato, per i progetti Visual Basic) prima di codice on demand o il codice di controllo di aggiornamento.

  La tecnica consigliata debug è il seguente:

1. Prima di iniziare, assicurarsi che i simboli (PDB) e vengono archiviati i file di origine.

2. Distribuire la versione 1 dell'applicazione.

3. Creare una nuova soluzione vuota. Dal **File** menu, fare clic su **New**, quindi **progetto**. Nel **nuovo progetto** finestra di dialogo, aprire il **altri tipi di progetto** nodo, quindi selezionare il **soluzioni di Visual Studio** cartella. Nel **modelli** riquadro, selezionare **soluzione vuota**.

4. Aggiungere il percorso di origine archiviati per le proprietà per questa nuova soluzione. Nelle **Esplora soluzioni**, fare doppio clic sul nodo della soluzione, quindi fare clic su **proprietà**. Nel **pagine delle proprietà** finestra di dialogo **Esegui Debug dei file di origine**, quindi aggiungere la directory del codice sorgente archiviato. In caso contrario, il debugger disponibili i file di origine non aggiornate, poiché i percorsi dei file di origine vengono registrate nel file con estensione pdb. Se il debugger utilizza file di origine non aggiornato, visualizzato un messaggio che informa che l'origine non corrisponde.

5. Assicurarsi che il debugger è possibile trovare il *PDB* file. Se questi sono stati distribuiti con l'applicazione, il debugger li trova automaticamente. Ha sempre l'aspetto accanto all'assembly in questione prima di tutto. In caso contrario, è necessario aggiungere il percorso di archiviazione per il **percorsi di file (con estensione pdb) di simboli** (per accedere a questa opzione, dal **Tools** dal menu fare clic su **opzioni**, quindi aprire il  **Debugging** nodo e fare clic su **simboli**).

6. Eseguire il debug cosa succede tra i `CheckForUpdate` e `Download` / `Update` chiamate al metodo.

    Ad esempio, il codice di aggiornamento potrebbe essere come segue:

   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
           If My.Application.Deployment.IsNetworkDeployed Then

               If (My.Application.Deployment.CheckForUpdate()) Then

                   My.Application.Deployment.Update()
                   Application.Restart()

               End If

           End If
       End Sub
   ```

7. Distribuire la versione 2.

8. Tentativo di collegare il debugger per la versione 1 dell'applicazione durante il download di un aggiornamento per la versione 2. In alternativa è possibile usare la `System.Diagnostics.Debugger.Break` metodo o semplicemente `Stop` in Visual Basic. Naturalmente, non è consigliabile lasciare queste chiamate al metodo nel codice di produzione.

    Si supponga, ad esempio, si sta sviluppando un'applicazione Windows Forms e un gestore eventi per questo metodo con la logica di aggiornamento è già. Per risolvere il problema, è sufficiente collegare prima il pulsante è premuto, quindi impostare un punto di interruzione (assicurarsi di aprire il file archiviato appropriato e impostare il punto di interruzione presenti).

   Usare la <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> proprietà da richiamare il <xref:System.Deployment.Application> API solo quando l'applicazione viene distribuita; le API non devono essere richiamate durante il debug di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Vedere anche
- <xref:System.Deployment.Application>