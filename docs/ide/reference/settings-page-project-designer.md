---
title: Pagina Impostazioni, Creazione progetti
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7422b87d0f812de2d99d59c2932e9aa2b9e6315
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62989971"
---
# <a name="settings-page-project-designer"></a>Pagina Impostazioni, Creazione progetti

Usare la pagina **Impostazioni** di Creazione progetti per specificare le impostazioni dell'applicazione del progetto. Le impostazioni dell'applicazione consentono di archiviare e recuperare dinamicamente le impostazioni delle proprietà e altre informazioni per l'applicazione. Consentono anche di mantenere le preferenze applicazione e utente personalizzate in un computer client. Per altre informazioni, vedere [Gestire le impostazioni dell'applicazione (.NET)](../managing-application-settings-dotnet.md).

Per accedere alla pagina **Impostazioni**, selezionare un nodo del progetto in **Esplora soluzioni** e quindi scegliere **Progetto** > **Proprietà**. Quando viene visualizzata Creazione progetti, selezionare la scheda **Impostazioni**.

## <a name="header-bar"></a>Barra intestazione

La barra intestazione nella parte superiore della pagina **Impostazioni** contiene diversi controlli:

**Sincronizza**

**Sincronizza** ripristina le impostazioni con ambito utente usate dall'applicazione in fase di esecuzione o durante il debug ai valori predefiniti specificati in fase di progettazione. Per ripristinare i dati, rimuovere i file specifici dell'applicazione generati in fase di esecuzione dal disco e non dai dati del progetto.

**Carica impostazioni Web**

**Carica impostazioni Web** visualizza una finestra di dialogo **Accesso** che consente di caricare le impostazioni di un utente autenticato o di utenti anonimi. Questo pulsante è abilitato solo se i servizi delle applicazioni client sono attivati nella pagina **Servizi** ed è stato specificato un **Percorso servizi impostazioni Web**.

**Visualizza codice**

Per i progetti C#, il pulsante **Visualizza codice** consente di visualizzare il codice del file *Settings.cs*. Il file definisce la classe `Settings` che consente di gestire eventi specifici nell'oggetto `Settings`. Nei linguaggi diversi da Visual Basic è necessario chiamare in modo esplicito il metodo `Save` di questa classe wrapper per rendere persistenti le impostazioni utente. Questa operazione viene generalmente effettuata nel gestore eventi **Closing** del form principale. Di seguito è riportato un esempio di chiamata al metodo `Save`:

```csharp
Properties.Settings.Default.Save();
```

Per i progetti Visual Basic, il pulsante **Visualizza codice** consente di visualizzare il codice del file *Settings.vb*. Il file definisce la classe `MySettings` che consente di gestire eventi specifici nell'oggetto `My.Settings`. Per altre informazioni sull'accesso alle impostazioni dell'applicazione mediante l'oggetto `My.Settings`, vedere [Accesso alle impostazioni dell'applicazione](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Per altre informazioni sull'accesso alle impostazioni dell'applicazione, vedere [Impostazioni delle applicazioni per Windows Form](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modificatore di accesso**

Il pulsante **Modificatore di accesso** specifica il livello di accesso delle classi helper `Properties.Settings` (in C#) o `My.Settings` (in Visual Basic) generate da Visual Studio in *Settings.Designer.cs* o *Settings.Designer.vb*.

Per i progetti Visual C#, il modificatore di accesso può essere **Internal** o **Public**.

Per i progetti Visual Basic, il modificatore di accesso può essere **Friend** o **Pubblico**.

Per impostazione predefinita, l'impostazione è **Internal** in C# e **Friend** in Visual Basic. Quando Visual Studio genera classi helper come **Internal** o **Friend**, le applicazioni eseguibili (con estensione *exe*) non possono accedere alle risorse e alle impostazioni aggiunte alle librerie di classi (file con estensione *dll*). Se è necessario condividere le risorse e le impostazioni da una libreria di classi, impostare il modificatore di accesso su **Public**.

Per altre informazioni sulle classi helper delle impostazioni, vedere [Gestire le impostazioni dell'applicazione](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Griglia Impostazioni

La **griglia Impostazioni** consente di configurare le impostazioni dell'applicazione. La griglia include le colonne seguenti:

**Name**

Immettere il nome dell'impostazione dell'applicazione in questo campo.

**Type**

Usare l'elenco a discesa per selezionare un tipo di impostazione. L'elenco include i tipi più utilizzati, ad esempio **String**, **(Stringa di connessione)** e **System.Drawing.Font**. È possibile scegliere un tipo diverso selezionando **Sfoglia** alla fine dell'elenco e quindi selezionando un tipo dalla finestra di dialogo **Seleziona un tipo**. Il tipo selezionato viene aggiunto ai tipi più utilizzati dell'elenco a discesa (solo per la soluzione corrente).

**Ambito**

Selezionare **Applicazione** o **Utente**.

Le impostazioni con ambito di applicazione, ad esempio le stringhe di connessione, vengono associate all'applicazione. Gli utenti non possono modificare le impostazioni con ambito di applicazione in fase di esecuzione.

Le impostazioni con ambito utente, ad esempio i tipi di carattere di sistema, sono progettate per essere usate per le preferenze utente. Gli utenti possono modificarle in fase di esecuzione.

**Valore**

Dati o valore associato all'impostazione dell'applicazione. Ad esempio, se l'impostazione è un tipo di carattere, il valore può essere **Verdana, 9.75pt, style=Bold**.

## <a name="see-also"></a>Vedere anche

- [Gestire le impostazioni dell'applicazione](../managing-application-settings-dotnet.md)
- [Accesso alle impostazioni dell'applicazione (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)