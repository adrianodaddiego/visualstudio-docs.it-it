---
title: La migrazione di un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43e4a119ae84f7b86b9b1a54f1f55dc2ffa78b15
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349263"
---
# <a name="migrating-a-legacy-language-service"></a>Migrazione di un servizio di linguaggio legacy
È possibile eseguire la migrazione di un servizio di linguaggio legacy a una versione successiva di Visual Studio l'aggiornamento del progetto e l'aggiunta di un file vsixmanifest al progetto. Il servizio di linguaggio stesso continuerà a funzionare come prima, poiché l'editor di Visual Studio consente di adattare lo.

 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>La migrazione di una soluzione di servizio di linguaggio di Visual Studio 2008 a una versione successiva
 La procedura seguente viene illustrato come adattare un esempio di Visual Studio 2008 denominato RegExLanguageService. È possibile trovare in questo esempio in un'installazione di Visual Studio 2008 SDK, il *percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ cartella.

> [!IMPORTANT]
> Se il servizio di linguaggio non definisce i colori, è necessario impostare esplicitamente <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> a `true` nel pacchetto VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Eseguire la migrazione di un servizio di linguaggio di Visual Studio 2008 a una versione successiva

1. Installare le versioni più recenti di Visual Studio e Visual Studio SDK. Per altre informazioni sui modi per installare il SDK, vedere [installazione di Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).

2. Modificare il file RegExLangServ.csproj (senza il caricamento in Visual Studio.

     Nel `Import` nodo che fa riferimento al file Microsoft.VsSDK.targets, sostituire il valore con il testo seguente.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Salvare il file e quindi chiuderla.

4. Aprire la soluzione RegExLangServ.sln.

5. Il **aggiornamento unidirezionale** verrà visualizzata la finestra. Fare clic su **OK**.

6. Aggiornare le proprietà del progetto. Aprire il **proprietà progetto** finestra selezionando il nodo del progetto nel **Esplora soluzioni**, mouse e selezionando **proprietà**.

    - Nel **Application** scheda, modificare **framework di destinazione** al **4.6.1**.

    - Nel **Debug** nella scheda il **Avvia programma esterno** , digitare  **\<percorso di installazione di Visual Studio > \Common7\IDE\devenv.exe.** .

         Nel **argomenti della riga di comando** , digitare /**rootsuffix Exp**.

7. Aggiornare i riferimenti seguenti:

    - Rimuovere il riferimento a Microsoft.VisualStudio.Shell.9.0.dll, quindi aggiungere i riferimenti a Microsoft.VisualStudio.Shell.14.0.dll e Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Rimuovere il riferimento a Microsoft.VisualStudio.Package.LanguageService.9.0.dll, quindi aggiungere un riferimento a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Aprire il file VsPkg.cs e modificare il valore della `DefaultRegistryRoot` dell'attributo

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. L'esempio originale non registra il servizio di linguaggio, pertanto è necessario aggiungere l'attributo seguente a VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. È necessario aggiungere un file vsixmanifest.

    - Copiare questo file da un'estensione esistente alla directory del progetto. (Un modo per ottenere questo file consiste nel creare un progetto VSIX (sotto **File**, fare clic su **New**, quindi fare clic su **progetto**. Fare clic in Visual Basic o c# **estendibilità**, quindi selezionare **progetto VSIX**.)

    - Aggiungere il file al progetto.

    - Il file **delle proprietà**, impostare **azione di compilazione** a **None**.

    - Aprire il file con il **Editor Manifest VSIX**.

    - Modificare i campi seguenti:

    - **ID**: RegExLangServ

    - **Nome del prodotto**: RegExLangServ

    - **Descrizione**: Un servizio di linguaggio di espressione regolare.

    - Sotto **asset**, fare clic su **New**, selezionare il **tipo** al **Microsoft.VisualStudio.VsPackage**, impostare il **origine** al **un progetto nella soluzione corrente**, quindi impostare il **progetto** a **RegExLangServ**.

    - Salvare e chiudere il file.

11. Compilare la soluzione. Vengono distribuiti i file compilati **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\** .

12. Avviare il debug. Aprire una seconda istanza di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)