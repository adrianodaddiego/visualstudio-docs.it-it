---
title: 'Passaggio 2: Aggiungere un oggetto casuale e un elenco di icone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7a4af2e5cc4119c85570246e1908c111cc0b7d75
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442639"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Passaggio 2: Aggiungere un oggetto casuale e un elenco di icone
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo passaggio verrà creato un set di simboli corrispondenti per il gioco. Ciascun simbolo viene aggiunto a due celle casuali in TableLayoutPanel nel form. A tale scopo verranno utilizzate due istruzioni `new` per creare due oggetti. Il primo è un oggetto `Random`, simile a quello utilizzato nel quiz matematico. Viene utilizzato in questo codice per scegliere casualmente le celle in TableLayoutPanel. Il secondo oggetto, che potrebbe essere nuovo per l'utente, è un oggetto `List` utilizzato per archiviare i simboli scelti in modo casuale.  
  
### <a name="to-add-a-random-object-and-a-list-of-icons"></a>Per aggiungere un oggetto casuale e un elenco di icone  
  
1. In **Esplora soluzioni** scegliere **Form1.cs** se si usa Visual C# oppure **Form1.vb** se si usa Visual Basic, quindi nella barra dei menu scegliere **Visualizza**, **Codice**. In alternativa, è possibile premere **F7** oppure fare doppio clic su **Form1** in **Esplora soluzioni**.  
  
     Verrà visualizzato il modulo di codice dietro Form1.  
  
2. Nel codice esistente aggiungere il seguente codice:  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#1)]  
  
     Se si utilizza Visual C#, assicurarsi di inserire il codice dopo la parentesi graffa di apertura e appena dopo la dichiarazione di classe (`public partial class Form1 : Form`). Se si utilizza Visual Basic, inserire il codice subito dopo la dichiarazione di classe (`Public Class Form1`).  
  
3. Quando si aggiunge l'oggetto `List`, osservare la finestra di **IntelliSense** visualizzata. Di seguito è riportato un esempio di Visual C#, ma un testo simile apparirà quando si aggiunge un elenco in Visual Basic.  
  
     ![Finestra Proprietà con evento Click visualizzato](../ide/media/express-listintellisense.png "Express_ListIntellisense")  
Finestra di IntelliSense  
  
    > [!NOTE]
    > La finestra di IntelliSense verrà visualizzata solo quando si immette manualmente il codice. Se si utilizzano le operazioni di copia e incolla, il codice non verrà visualizzato.  
  
     Se si analizza il codice (e le note) in piccole sezioni, è più facile da comprendere. I programmi possono utilizzare oggetti `List` per tenere traccia di diversi tipi di elementi. Un elenco può contenere numeri, valori true/false, testo o altri oggetti. Un oggetto `List` può persino contenere altri oggetti `List`. Gli oggetti contenuti in un elenco sono definiti *elementi* e ogni elenco contiene un solo tipo di elemento. Un elenco di numeri, ad esempio, può contenere solo numeri; non è possibile aggiungervi testo. In modo analogo, non è possibile aggiungere numeri a un elenco di valori true/false.  
  
     Quando si crea un oggetto `List` utilizzando un'istruzione `new`, è necessario specificare il tipo di dati da archiviare al suo interno. Per questo la descrizione comando in cima alla finestra di **IntelliSense** visualizza i tipi di elementi nell'elenco. Inoltre, ecco cosa significa `List<string>` (in Visual C#) e `List(Of String)` (in Visual Basic): è un oggetto `List` che contiene elementi del tipo di dati `string`. Il programma usa le stringhe per archiviare il testo, vale a dire l'indicazione contenuta nella descrizione comandi a destra della finestra di **IntelliSense**.  
  
4. Considerare il perché in Visual Basic sia necessario innanzitutto creare una matrice temporanea, mentre in Visual C# è possibile creare l'elenco con un'unica istruzione. Questo perché il linguaggio Visual C# include *inizializzatori di raccolta*, che preparano l'accettazione dei valori nell'elenco. In Visual Basic è possibile utilizzare un inizializzatore di raccolta. Tuttavia, per motivi di compatibilità con la versione precedente di Visual Basic, si consiglia di utilizzare il codice precedente.  
  
     Quando si utilizza un inizializzatore di raccolta con un'istruzione `new`, una volta creato il nuovo oggetto `List`, il programma vi collocherà i dati forniti dall'utente racchiusi tra parentesi graffe. In questo caso, si ottiene un elenco di stringhe denominate **icone** e l'elenco sarà inizializzato in modo da contenere sedici stringhe. Ognuna di quelle stringhe è una singola lettera, e insieme corrispondono alle icone che saranno nelle etichette. Il gioco conterrà quindi una coppia di punti esclamativi, una coppia di lettere N maiuscole, una coppia di virgole e così via. Se per questi caratteri viene impostato il tipo Webdings, verranno visualizzati come simboli, ad esempio un autobus, una moto, un ragno e così via. L'oggetto `List` avrà in tutto sedici stringhe, una per ogni cella nel pannello TableLayoutPanel.  
  
    > [!NOTE]
    > In Visual Basic si ottiene lo stesso risultato, ma prima le stringhe vengono inserite in una matrice temporanea, quindi questa viene convertita in un oggetto `List`. Una matrice è simile a un elenco, salvo ad esempio che le matrici vengono create con una dimensione fissa. Gli elenchi possono essere ridotti o ingranditi in base alle necessità, caratteristica importante in questo programma.  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 3: Assegnare un'icona casuale a ogni etichetta](../ide/step-3-assign-a-random-icon-to-each-label.md).  
  
- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 1: Creare un progetto e aggiungere una tabella al Form](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
