---
title: La registrazione di un tipo di linguaggio legacy1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e30123d0514acc935a1caf475c01086ca9aab62e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341401"
---
# <a name="registering-a-legacy-language-service"></a>La registrazione di un servizio di linguaggio Legacy
Nel framework di pacchetto gestito (MPF), il servizio di linguaggio è fornito da un pacchetto VSPackage (vedere [VSPackage](../../extensibility/internals/vspackages.md)) e viene registrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante l'aggiunta di voci e chiavi del Registro di sistema. Questo processo di registrazione viene eseguito in parte durante l'installazione e in parte in fase di esecuzione.

## <a name="register-the-language-service-by-using-attributes"></a>Registrare il servizio di linguaggio con gli attributi
 Gli attributi seguenti vengono utilizzati per registrare un servizio di linguaggio.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Questi attributi vengono spiegati di seguito

### <a name="provideserviceattribute"></a>ProvideServiceAttribute
 Questo attributo registra il servizio di linguaggio come un servizio.

### <a name="example"></a>Esempio

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideServiceAttribute(typeof(TestLanguageService),
                             ServiceName = "Test Language Service")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute
 Questo attributo registra il servizio di linguaggio in modo specifico come un servizio di linguaggio. Consente di impostare le opzioni che specificano le funzionalità offerte del servizio di linguaggio. Nell'esempio viene illustrato un subset delle opzioni di che un servizio di linguaggio. Per il set completo di opzioni del servizio linguaggio, vedere <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.

### <a name="example"></a>Esempio

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),
                             "Test Language",
                             106,             // resource ID of localized language name
                             CodeSense = true,             // Supports IntelliSense
                             RequestStockColors = false,   // Supplies custom colors
                             EnableCommenting = true,      // Supports commenting out code
                             EnableAsyncCompletion = true  // Supports background parsing
                             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute
 Questo attributo associa il servizio di linguaggio con un'estensione di file. Ogni volta che viene caricato un file con tale estensione, in qualsiasi progetto, il servizio di linguaggio è stato avviato e usato per visualizzare il contenuto del file.

### <a name="example"></a>Esempio

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),
                                       ".Testext")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute
 Questo attributo registra una posizione dalla quale codice si ottengono i modelli di espansione o frammento di codice. Queste informazioni vengono usate per la **Browser di frammenti di codice** e dall'editor quando viene inserito un frammento di codice nel file di origine.

### <a name="example"></a>Esempio

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageCodeExpansionAttribute(
             typeof(TestLanguageService),
             "Test Language", // Name of language used as registry key.
             106,           // Resource ID of localized name of language service.
             "testlanguage",  // language key used in snippet templates.
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute
 Questo attributo registra una pagina delle proprietà da visualizzare nella **le opzioni** nella finestra di dialogo il **Editor di testo** categoria. Usare uno di questi attributi per ogni pagina da visualizzare per il servizio di linguaggio. Se è necessario organizzare le pagine in una struttura ad albero, usare gli attributi aggiuntivi per definire ogni nodo dell'albero.

### <a name="example"></a>Esempio
 In questo esempio mostra due pagine delle proprietà, **le opzioni** e **rientri**e un nodo che contiene la seconda pagina delle proprietà.

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Options",      // Registry key name for property page
             "#242",         // Localized name of property page
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Advanced",     // Registry key name for node
             "#243",         // Localized name of node
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             @"Advanced\Indenting",     // Registry key name for property page
             "#244",         // Localized name of property page
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

## <a name="proffer-the-language-service-at-runtime"></a>Fornire il servizio di linguaggio in fase di esecuzione
 Quando viene caricato il pacchetto di lingua, è necessario indicare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che il servizio di linguaggio è pronto. Questo scopo si proffering il servizio. Questa operazione viene eseguita <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (metodo). Inoltre, è necessario avviare un timer che chiama il servizio di linguaggio durante i periodi di inattività in modo che può essere eseguita l'analisi in background. Questo timer di inattività viene inoltre utilizzato per aggiornare le proprietà del documento se è stato implementato uno tramite il <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe. Per supportare un timer, il pacchetto deve implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> interface (solo il <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> metodo deve essere implementata completamente; dei rimanenti metodi possono restituire valori predefiniti).

### <a name="example"></a>Esempio
 Questo esempio illustra un approccio tipico per un servizio proffering e fornendo un timer di inattività.

```csharp

using System;
using System.Runtime.InteropServices;
using System.ComponentModel.Design;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.OLE.Interop;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,
        AutoOutlining = true,
        EnableCommenting = true,
        MatchBraces = true,
        ShowMatchingBrace = true)]
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package

    public class TestLanguagePackage : Package, IOleComponent
    {
        private uint m_componentID;

        protected override void Initialize()
        {
            base.Initialize();  // required

            // Proffer the service.
            IServiceContainer serviceContainer = this as IServiceContainer;
            TestLanguageService langService      = new TestLanguageService();
            langService.SetSite(this);
            serviceContainer.AddService(typeof(TestLanguageService),
                                        langService,
                                        true);

            // Register a timer to call our language service during
            // idle periods.
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                       as IOleComponentManager;
            if (m_componentID == 0 && mgr != null)
            {
                OLECRINFO[] crinfo = new OLECRINFO[1];
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
                                              (uint)_OLECADVF.olecadvfRedrawOff |
                                              (uint)_OLECADVF.olecadvfWarningsOff;
                crinfo[0].uIdleTimeInterval = 1000;
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);
            }
        }

        protected override void Dispose(bool disposing)
        {
            if (m_componentID != 0)
            {
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                           as IOleComponentManager;
                if (mgr != null)
                {
                    int hr = mgr.FRevokeComponent(m_componentID);
                }
                m_componentID = 0;
            }

            base.Dispose(disposing);
        }

        #region IOleComponent Members

        public int FDoIdle(uint grfidlef)
        {
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;
            // Use typeof(TestLanguageService) because we need to
            // reference the GUID for our language service.
            LanguageService service = GetService(typeof(TestLanguageService))
                                      as LanguageService;
            if (service != null)
            {
                service.OnIdle(bPeriodic);
            }
            return 0;
        }

        public int FContinueMessageLoop(uint uReason,
                                        IntPtr pvLoopData,
                                        MSG[] pMsgPeeked)
        {
            return 1;
        }

        public int FPreTranslateMessage(MSG[] pMsg)
        {
            return 0;
        }

        public int FQueryTerminate(int fPromptUser)
        {
            return 1;
        }

        public int FReserved1(uint dwReserved,
                              uint message,
                              IntPtr wParam,
                              IntPtr lParam)
        {
            return 1;
        }

        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)
        {
            return IntPtr.Zero;
        }

        public void OnActivationChange(IOleComponent pic,
                                       int fSameComponent,
                                       OLECRINFO[] pcrinfo,
                                       int fHostIsActivating,
                                       OLECHOSTINFO[] pchostinfo,
                                       uint dwReserved)
        {
        }

        public void OnAppActivate(int fActive, uint dwOtherThreadID)
        {
        }

        public void OnEnterState(uint uStateID, int fEnter)
        {
        }

        public void OnLoseActivation()
        {
        }

        public void Terminate()
        {
        }

        #endregion
    }
}
```