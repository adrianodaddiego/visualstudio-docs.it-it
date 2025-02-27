---
title: Creare un progetto unit test | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 10
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f792c29b50be5bbadf34980b81f7c5dd329cccfb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442825"
---
# <a name="create-a-unit-test-project"></a>Creare un progetto di unit test
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli unit test spesso simulano la struttura del codice sottoposto a test. Ad esempio, si crea un progetto unit test per ogni progetto di codice del prodotto. Il progetto test può essere nella stessa soluzione del codice di produzione o in una soluzione separata. È possibile avere più progetti unit test in una soluzione.  
  
> [!NOTE]
> Il percorso degli unit test per un codice nativo e la struttura del progetto test possono essere diversi da quelli descritti in questo argomento. Per altre informazioni, vedere [Aggiunta di unit test alle applicazioni C++ esistenti](../test/unit-testing-existing-cpp-applications-with-test-explorer.md).  
  
## <a name="to-create-a-unit-test-project"></a>Per creare un progetto unit test:  
  
1. Scegliere **Nuovo** dal menu **File** , quindi scegliere **Progetto** oppure premere CTRL+MAIUSC+N.  
  
2. Nella finestra di dialogo Nuovo progetto espandere il nodo **Installato**, scegliere il linguaggio da usare per il progetto test e quindi scegliere **Test**.  
  
3. Per usare uno dei framework per unit test Microsoft, scegliere **Progetto unit test** dall'elenco di modelli di progetto. In alternativa, scegliere il modello di progetto del framework per unit test che si vuole usare. Per testare il progetto Accounts dell'esempio, assegnare al progetto il nome AccountsTests.  
  
4. Nel progetto unit test, aggiungere un riferimento al codice sottoposto a test.  Di seguito viene illustrato come creare il riferimento a un progetto codice nella stessa soluzione:  
  
    1. Selezionare il progetto in Esplora soluzioni.  
  
    2. Scegliere **Aggiungi riferimento** dal menu **Progetto**.  
  
    3. Nella finestra di dialogo Gestione riferimenti aprire il nodo **Soluzione** e scegliere **Progetti**. Selezionare il nome del progetto codice e chiudere la finestra di dialogo.  
  
5. Se il codice che si vuole testare è in un altro percorso, vedere [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md) per informazioni sull'aggiunta di riferimenti.  
  
## <a name="next-steps"></a>Passaggi successivi  
 **Scrittura di unit test**  
  
 Vedere una delle sezioni seguenti:  
  
- [Scrittura di unit test per .NET Framework con il framework unit test di Microsoft per codice gestito](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
- [Scrittura di unit test per C/C++ con il framework unit test di Microsoft per C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
  **Esecuzione di unit test**  
  
  [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)
