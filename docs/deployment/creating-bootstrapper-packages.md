---
title: Creare pacchetti del programma di avvio automatico personalizzati
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 960ecd2680585602b2c026b00b36bf7d93b8021d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900231"
---
# <a name="create-bootstrapper-packages"></a>Creare pacchetti del programma di avvio automatico personalizzati
Il programma di installazione è un programma generico che può essere configurato per rilevare e installare componenti ridistribuibili quali file di Windows Installer (*.msi*) e programmi eseguibili. Il programma di installazione è noto anche come programma di avvio automatico. Viene programmato con un set di manifesti XML che specificano i metadati per gestire l'installazione del componente.  Ogni componente ridistribuibile o prerequisito, che viene visualizzato nei **prerequisiti** finestra di dialogo di ClickOnce è un pacchetto di programma di avvio automatico. Un pacchetto del programma di avvio automatico è un gruppo di directory e file che contengono i file manifesto in cui è descritto come deve essere installato il prerequisito.

Il programma di avvio automatico prima rileva se i prerequisiti sono già installati. Se i prerequisiti non sono installati, visualizza prima i contratti di licenza. Successivamente, dopo che l'utente finale accetta i contratti di licenza, ha inizio l'installazione dei prerequisiti. Se invece tutti i prerequisiti vengono rilevati, viene semplicemente avviato il programma di installazione dell'applicazione.

## <a name="create-custom-bootstrapper-packages"></a>Creare pacchetti di programma di avvio automatico personalizzato
È possibile generare i manifesti del programma di avvio automatico usando l'Editor XML in Visual Studio. Per un esempio di creazione di un pacchetto di programma di avvio automatico, vedere [procedura dettagliata: Creare un programma di avvio personalizzata con un prompt di privacy](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).

Per creare un pacchetto di programma di avvio automatico, è necessario creare un manifesto del prodotto e, per ogni versione localizzata di un componente, nonché un manifesto del pacchetto.

* Il manifesto del prodotto, *Product*, contiene tutti i metadati indipendenti dalla lingua per il pacchetto. Questo file contiene i metadati comuni a tutte le versioni localizzate del componente ridistribuibile.  Per creare questo file, vedere [come: Creare un manifesto del prodotto](../deployment/how-to-create-a-product-manifest.md).

* Il manifesto del pacchetto *package*, contiene metadati specifici del linguaggio; in genere contiene i messaggi di errore localizzato. Deve essere disponibile almeno un manifesto del pacchetto per ogni versione localizzata del componente. Per creare questo file, vedere [come: Creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md).

Dopo aver creato questi file, inserire il file manifesto del prodotto in una cartella denominata per il programma di avvio automatico personalizzato. Il file manifesto del pacchetto deve essere inserito in una cartella denominata per le impostazioni locali. Ad esempio, se il file manifesto del pacchetto è destinato alla ridistribuzione in inglese, inserire il file in una cartella denominata en. Ripetere questo processo per ogni impostazione locale, ad esempio ja per il giapponese e de per il tedesco. Il pacchetto del programma di avvio automatico personalizzato finale potrebbe avere la struttura di cartelle seguente.

    ```xml
    CustomBootstrapperPackage
      product.xml
      CustomBootstrapper.msi
      de
        eula.rtf
        package.xml
      en
        eula.rtf
        package.xml
      ja
        eula.rtf
        package.xml
    ```

Quindi copiare i file ridistribuibili nel percorso della cartella di programma di avvio automatico. Per altre informazioni, vedere [Procedura: Creare un pacchetto localizzato del programma di avvio automatico](../deployment/how-to-create-a-localized-bootstrapper-package.md).

    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*

oppure

    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*

È anche possibile determinare il percorso della cartella del programma di avvio automatico usando il valore **Percorso** nella chiave del Registro di sistema seguente:

    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*

Nei sistemi a 64 bit, usare la chiave del Registro di sistema seguente:

    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*

Ciascun componente ridistribuibile viene mostrato nella propria sottocartella nella directory dei pacchetti. Il prodotto del manifesto e pacchetto ridistribuibile di file devono essere inseriti in questa sottocartella. Le versioni localizzate dei manifesti di pacchetto e del componente devono essere inserite nelle sottocartelle denominate in base al nome delle impostazioni cultura.

Dopo aver copiato i file nella cartella del programma di avvio automatico, il relativo pacchetto viene visualizzato automaticamente nella finestra di dialogo **Prerequisiti** in Visual Studio. Se il pacchetto del programma di avvio automatico personalizzato non viene visualizzato, chiudere e riaprire la finestra di dialogo **Prerequisiti**. Per altre informazioni, vedere [Finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).

La tabella seguente illustra le proprietà popolate automaticamente dal programma di avvio automatico.

|Proprietà|Descrizione|
|--------------|-----------------|
|ApplicationName|Nome dell'applicazione.|
|ProcessorArchitecture|Processore e bit per parola della piattaforma di destinazione di un file eseguibile. Sono inclusi i valori seguenti:<br /><br /> -   Intel<br />-   IA64<br />-   AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Numero di versione per i sistemi operativi Microsoft Windows 95, Windows 98 o Windows ME. La sintassi della versione è Principale.Secondario.ServicePack.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Numero di versione per i sistemi operativi Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 o Windows 7. La sintassi della versione è Principale.Secondario.ServicePack.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|La versione dell'assembly di Windows Installer (MSI) per l'esecuzione durante l'installazione.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Questa proprietà viene impostata se l'utente ha i privilegi di amministratore. I valori sono true o false.|
|InstallMode|La modalità di installazione indica il percorso dal quale deve essere installato il componente. Sono inclusi i valori seguenti:<br /><br /> -   HomeSite: i prerequisiti vengono installati dal sito Web del fornitore.<br />-   SpecificSite: i prerequisiti vengono installati dal percorso selezionato.<br />-   SameSite: i prerequisiti vengono installati dallo stesso percorso dell'applicazione.|

## <a name="separate-redistributables-from-application-installations"></a>Componenti ridistribuibili separati dalle installazioni delle applicazioni
Per impedire che i file ridistribuibili vengano distribuiti nei progetti di installazione, creare un elenco di ridistribuibili nella cartella RedistList situata nella directory di .NET Framework:

`%ProgramFiles%\Microsoft.NET\RedistList`

L'elenco dei ridistribuibili è un file XML che deve essere denominato utilizzando il formato seguente: *\<Nome società >. \<Nome componente >. RedistList*. Quindi, se ad esempio il nome del componente è Datawidgets e la società che lo produce è Acme, usare il nome *Acme.DataWidgets.RedistList.xml*. Ecco un esempio del possibile contenuto dell'elenco dei file ridistribuibili:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Vedere anche
- [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md)
- [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)
- [Usare il programma di avvio automatico di Visual Studio 2005 per avviare l'installazione](http://go.microsoft.com/fwlink/?LinkId=107537)
