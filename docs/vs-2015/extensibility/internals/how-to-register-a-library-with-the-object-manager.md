---
title: 'Procedura: Registrare una libreria con il gestore oggetti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c40c695a912e97269263ba14747b72382847324d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042463"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Procedura: Registrare una libreria con il gestore degli oggetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I simboli per l'esplorazione strumenti, ad esempio **Visualizzazione classi**, **Visualizzatore oggetti**, **Visualizzatore chiamate** e **risultati ricerca simbolo**, consentono di visualizzare simboli nel progetto o nei componenti esterni. I simboli includono gli spazi dei nomi, classi, interfacce, metodi e altri elementi del linguaggio. Le librerie di tenere traccia di questi simboli ed esporle al [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestione degli oggetti che popolano gli strumenti con i dati.  
  
 Object manager tiene traccia di tutte le librerie disponibili. Ogni libreria è necessario registrare con il gestore oggetti prima di fornire i simboli per gli strumenti di esplorazione dei simboli.  
  
 In genere, si registra una libreria quando si carica un pacchetto VSPackage. Tuttavia, si può essere eseguito in un secondo momento come necessario. Annullare la registrazione della libreria quando il VSPackage viene arrestato.  
  
 Per registrare una libreria, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> (metodo). Nel caso di libreria di codice gestito, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> (metodo).  
  
 Per annullare la registrazione di una libreria, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> (metodo).  
  
 Per ottenere un riferimento al gestore oggetti, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID al servizio `GetService` (metodo).  
  
## <a name="registering-and-unregistering-a-library-with-the-object-manager"></a>La registrazione e annullamento della registrazione di una libreria con il gestore oggetti  
  
#### <a name="to-register-a-library-with-the-object-manager"></a>Per registrare una libreria con il gestore oggetti  
  
1. Creare una libreria.  
  
    ```vb  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```csharp  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2. Ottenere un riferimento a un oggetto del <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> digitare e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> (metodo).  
  
    ```vb  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### <a name="to-unregister-a-library-with-the-object-manager"></a>Per annullare la registrazione di una libreria con il gestore oggetti  
  
1. Ottenere un riferimento a un oggetto del <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> digitare e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> (metodo).  
  
    ```vb  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensibilità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Supporto di strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Procedura: Esporre gli elenchi dei simboli forniti dalla libreria al gestore degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
