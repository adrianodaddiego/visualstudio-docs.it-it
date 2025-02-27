---
title: Eseguire unit test del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1e6f0dd19c9d5d3ea1ee28a267aa969aad638948
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695216"
---
# <a name="unit-test-your-code"></a>Eseguire unit test del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli unit test rappresentano per sviluppatori e tester un modo rapido per verificare la presenza di errori di logica nei metodi delle classi in progetti [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] e [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)].  
  
 Gli strumenti di unit test includono:  
  
1. **Esplora test.** Esplora test consente di eseguire unit test e visualizzare i relativi risultati. Esplora test può utilizzare qualsiasi framework per unit test, incluso un framework di terze parti provvisto di un apposito adapter.  
  
2. **Framework per unit test di Microsoft per codice gestito.** Il framework per unit test di Microsoft per il codice gestito viene installato con Visual Studio e fornisce un framework per testare il codice .NET.  
  
3. **Framework per unit test di Microsoft per C++.** Il framework per unit test di Microsoft per C++ viene installato con Visual Studio e fornisce un framework per testare il codice nativo.  
  
4. **Strumenti di code coverage.** È possibile determinare la quantità di codice del prodotto sottoposta agli unit test da un comando in Esplora test.  
  
5. **Framework di isolamento Microsoft Fakes.** Il framework di isolamento Microsoft Fakes può creare classi e metodi sostitutivi per il codice di sistema e di produzione che creano le dipendenze nel codice sottoposto a test. L'implementazione di delegati falsi per una funzione consente di controllare il comportamento e l'output dell'oggetto di dipendenza.  
  
   È anche possibile creare [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) che esplorano il codice .NET per generare dati di test e un gruppo di unit test. Per ogni istruzione nel codice viene generato un input di test che eseguirà l'istruzione. Viene eseguita un'analisi del caso per ogni branch condizionale nel codice.  
  
## <a name="key-tasks"></a>Attività chiave  
 Usare gli argomenti seguenti per la comprensione e la creazione di unit test:  
  
|Attività|Argomenti correlati|  
|-----------|-----------------------|  
|**Guide introduttive e procedure dettagliate:** usare gli argomenti seguenti per ottenere informazioni sugli unit test in Visual Studio da esempi di codice.|-   [Procedura dettagliata: creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Avvio rapido: sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Aggiunta di unit test alle applicazioni C++ esistenti](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Unit test di codice nativo con Esplora test](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**Unit test con Esplora test:** informazioni su come Esplora test può agevolare la creazione di unit test più produttivi ed efficienti.|-   [Nozioni fondamentali sugli unit test](../test/unit-test-basics.md)<br />-   [Creare un progetto di unit test](../test/create-a-unit-test-project.md)<br />-   [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)<br />-   [Installare framework di unit test di terze parti](../test/install-third-party-unit-test-frameworks.md)<br />-   [Aggiornamento di unit test da Visual Studio 2010](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**Testing unità di codice gestito:**|-   [Scrittura di unit test per .NET Framework con il framework unit test di Microsoft per codice gestito](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Eseguire unit test del codice**|-   [Scrittura di unit test per C-C++ con il framework di unit test Microsoft per C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Isolamento degli unit test**|-   [Isolamento del codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Uso di code coverage per identificare quale percentuale del codice del progetto è sottoposto a test mediante unit test:** Informazioni sulle funzionalità di code coverage [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] gli strumenti di test.|-   [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Eseguire analisi di stress e prestazioni usando test di carico per gli unit test:** è possibile creare un test di carico e aggiungervi gli unit test per isolare problemi di prestazioni e di stress nell'applicazione. **Nota:**  Per la creazione e l'uso dei test di carico è necessario Visual Studio Enterprise.|-   [Creazione e modifica dei test di carico](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Procedura: Aggiungere test prestazioni Web e Unit test per uno Scenario di Test di carico](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Procedura: Rimuovere i test Web e Unit test da uno Scenario di Test di carico](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**Impostare e applicare controlli di qualità:** È possibile creare quality gate per imporre che i test vengono eseguiti prima dell'archiviazione code per garantire la qualità del codice.|-   [Impostare e applicare controlli di qualità](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Estendere l'unità di tipo di test:** È possibile aggiungere la funzionalità per i test che potrebbero non essere presenti nel Framework di Unit Test. Ad esempio, è possibile aggiungere una proprietà di test che specifica se un test deve essere eseguito o meno come utente normale. Oppure è possibile estendere il framework per aggiungere attributi di riga a un metodo e utilizzare i dati in tale riga all'interno del test.|Per codice di esempio su come estendere il framework per unit test, visitare il [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkId=185591) seguente.|  
|**Impostare le opzioni di test:** ad esempio, è possibile specificare dove archiviare i risultati dei test.|[Configurazione di unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
 [Revisione dei risultati dei test in Microsoft Test Manager](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 Vengono descritti i risultati dei test e le relative modalità di utilizzo, ad esempio come visualizzarli, salvarli ed eliminarli.  
  
 [Esecuzione di test di sistema mediante Microsoft Visual Studio](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)  
  
 Fornisce collegamenti alle informazioni sull'utilizzo di Visual Studio rispetto all'utilizzo di  [!INCLUDE[TCMext](../includes/tcmext-md.md)] per eseguire test automatizzati.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Viene descritto lo spazio dei nomi UnitTesting, che rende disponibili attributi, eccezioni, asserzioni e altre classi che supportano il testing unità.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Viene descritto lo spazio dei nomi UnitTesting.Web, che estende lo spazio dei nomi UnitTesting fornendo il supporto per gli unit test [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] e dei servizi Web.  
  
## <a name="external-resources"></a>Risorse esterne  
  
### <a name="videos"></a>Video  
 [Channel 9: Unit test di App Windows Store compilate utilizzando XAML](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Forum  
 [Visual Studio Unit Testing](http://go.microsoft.com/fwlink/?LinkId=224477) (Testing unità con Visual Studio)  
  
### <a name="guidance"></a>Materiale sussidiario  
 [Esecuzione di test per il recapito continuo con Visual Studio 2012 – capitolo 2: Unit test: Test interni](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>Riferimenti  
 [Indice dei contenuti relativi agli unit test](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>Vedere anche  
 [Migliorare la qualità del codice](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [Test dell'applicazione](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)
