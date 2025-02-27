---
title: Test di un'applicazione di grandi dimensioni con più mappe dell'interfaccia utente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 24
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 18180ee3277cdff60d11c0ae35e8aa3c990764de
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386039"
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>Test di un'applicazione di grandi dimensioni con più mappe dell'interfaccia utente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrato l'uso dei test codificati dell'interfaccia utente per il test di un'applicazione di grandi dimensioni con più mappe dell'interfaccia utente.  
  
 **Requisiti**  
  
- Visual Studio Enterprise  
  
  Quando si crea un nuovo test codificato dell'interfaccia utente, per impostazione predefinita, il framework di test di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera il codice per il test in una classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>. Per altre informazioni sulla registrazione di test codificati dell'interfaccia utente, vedere [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) e [Composizione di un test codificato dell'interfaccia utente](../test/anatomy-of-a-coded-ui-test.md).  
  
  Il codice generato per la mappa dell'interfaccia utente contiene una classe per ogni oggetto con cui il test interagisce. Per ogni metodo generato, viene generata una classe complementare per i parametri del metodo appositamente per quel metodo. Se l'applicazione contiene un numero elevato di oggetti, pagine, moduli e controlli, la mappa dell'interfaccia utente può raggiungere dimensioni significative. Inoltre, se più persone stanno operando sui test, l'applicazione può diventare difficile da gestire se è presente un solo file di mappa dell'interfaccia utente di grandi dimensioni.  
  
  L'uso di più file di mappa dell'interfaccia utente può offrire i vantaggi seguenti:  
  
- Ogni mappa può essere associata a un subset logico dell'applicazione per semplificare la gestione delle modifiche.  
  
- Ogni tester può operare su una sezione dell'applicazione e archiviare il proprio codice senza interferire con altri tester che lavorano su altre sezioni dell'applicazione.  
  
- Le aggiunte all'interfaccia utente dell'applicazione possono essere ridimensionate in modo incrementale con effetti minimi sui test per le altre parti dell'interfaccia utente.  
  
## <a name="do-you-need-multiple-ui-maps"></a>Situazioni in cui sono necessarie più mappe dell'interfaccia utente  
 Creare più mappe dell'interfaccia utente nei tipi di situazioni seguenti:  
  
- Diversi set complessi di controlli dell'interfaccia utente compositi che insieme eseguono un'operazione logica, ad esempio una pagina di registrazione in un sito Web o la pagina di acquisto di un carrello.  
  
- Un set indipendente di controlli a cui si accede da vari punti dell'applicazione, ad esempio una procedura guidata con numerose pagine di operazioni. Se le pagine di una procedura guidata sono particolarmente complesse, è possibile creare mappe dell'interfaccia utente separate per ogni pagina.  
  
## <a name="adding-multiple-ui-maps"></a>Aggiunta di più mappe dell'interfaccia utente  
  
#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Per aggiungere una mappa dell'interfaccia utente al progetto di test codificato dell'interfaccia utente  
  
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file del progetto di test codificato dell'interfaccia utente, scegliere **Aggiungi** e quindi **Nuova cartella** per creare una cartella nel progetto di test codificato dell'interfaccia utente in cui archiviare tutte le mappe dell'interfaccia utente. Ad esempio, la cartella potrebbe essere denominata `UIMaps`.  
  
    La nuova cartella verrà visualizzata sotto il progetto di test codificato dell'interfaccia utente.  
  
2. Fare clic con il pulsante destro del sulla cartella `UIMaps`, scegliere **Aggiungi** e quindi **Nuovo elemento**.  
  
    Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
   > [!NOTE]
   > È necessario essere all'interno di un progetto di test codificato dell'interfaccia utente per aggiungere una nuova mappa di test codificati dell'interfaccia utente.  
  
3. Selezionare **Mappa di test codificati dell'interfaccia utente** nell'elenco.  
  
    Nella casella **Nome** immettere un nome per la nuova mappa dell'interfaccia utente. Usare il nome del componente o della pagina che verrà rappresentata dalla mappa, ad esempio `HomePageMap`.  
  
4. Scegliere **Aggiungi**.  
  
    La finestra [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene ridotta a icona e viene visualizzata la finestra di dialogo **Generatore di test codificati dell'interfaccia utente**.  
  
5. Registrare le azioni per il primo metodo e scegliere **Genera codice**.  
  
6. Dopo avere registrato tutte le azioni e le asserzioni per il primo componente o pagina e averli raggruppati in metodi, chiudere la finestra di dialogo **Generatore di test codificati dell'interfaccia utente**.  
  
7. Continuare a creare le mappe dell'interfaccia utente. Registrare le azioni e le asserzioni, raggrupparle in metodi per ogni componente e quindi generare il codice.  
  
   In molti casi, la finestra di primo livello dell'applicazione rimane costante per tutte le procedure guidate, i moduli e le pagine. Sebbene ogni mappa dell'interfaccia utente abbia una classe per la finestra di primo livello, è probabile che tutte le mappe facciano riferimento alla stessa finestra di primo livello all'interno della quale sono in esecuzione tutti i componenti dell'applicazione. I test codificati dell'interfaccia utente eseguono la ricerca dei controlli in modo gerarchico dall'altro al basso, iniziando dalla finestra di primo livello in modo che in un'applicazione complessa la finestra di primo livello effettiva possa essere duplicata in ogni mappa dell'interfaccia utente. Se la finestra di primo livello effettiva viene duplicata, ogni cambiamento della finestra determina più modifiche. Questo può causare problemi di prestazioni nel passaggio da una mappa dell'interfaccia utente all'altra.  
  
   Per attenuare questo effetto, è possibile usare il metodo `CopyFrom()` per garantire che la nuova finestra di primo livello in quella determinata mappa dell'interfaccia utente corrisponda alla finestra di primo livello principale.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente fa parte di una classe di utilità che fornisce accesso a ogni componente e ai relativi controlli figlio che sono rappresentati dalle classi generati nelle varie mappe dell'interfaccia utente.  
  
 In questo esempio, un'applicazione Web denominata `Contoso` ha una home page, una pagina per i prodotti (Product Page) e una pagina per il carrello (Shopping Cart Page). Ognuna di queste pagine condivide una finestra di primo livello che è la finestra del browser. È disponibile una mappa dell'interfaccia utente per ogni pagina e la classe di utilità presenta un codice simile al seguente:  
  
```  
using ContosoProject.UIMaps;  
using ContosoProject.UIMaps.HomePageClasses;  
using ContosoProject.UIMaps.ProductPageClasses;  
using ContosoProject.UIMaps.ShoppingCartClasses;  
  
namespace ContosoProject  
{  
    public class TestRunUtility  
    {  
        // Private fields for the properties  
        private HomePage homePage = null;  
        private ProductPage productPage = null;  
        private ShoppingCart shoppingCart = null;  
  
        public TestRunUtility()  
        {  
            homePage = new HomePage();  
        }  
  
        // Properties that get each UI Map  
        public HomePage HomePage  
        {  
            get { return homePage; }  
            set { homePage = value; }  
        }  
  
        // Gets the ProductPage from the ProductPageMap.  
        public ProductPage ProductPageObject  
        {  
            get  
            {  
                if (productPage == null)  
                {  
                    // Instantiate a new page from the UI Map classes  
                    productPage = new ProductPage();  
  
                    // Since the Product Page and Home Page both use  
                    // the same browser page as the top level window,  
                    // get the top level window properties from the  
                    // Home Page.  
                    productPage.UIContosoFinalizeWindow.CopyFrom(  
                        HomePage.UIContosoWindowsIWindow);  
                }  
                return productPage;  
            }  
        }  
  
    // Continue to create properties for each page, getting the   
    // page object from the corresponding UI Map and copying the   
    // top level window properties from the Home Page.  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)   
 [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Composizione di un test codificato dell'interfaccia utente](../test/anatomy-of-a-coded-ui-test.md)
