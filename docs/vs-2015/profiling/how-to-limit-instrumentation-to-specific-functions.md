---
title: 'Procedura: Limitare la strumentazione a funzioni specifiche | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8923323a3aed96a9dd441a4a36b2084ffd8197e6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432645"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Procedura: Limite di strumentazione a specifiche funzioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile limitare la strumentazione e la raccolta dei dati a una o più funzioni impostando le opzioni nella pagina **Avanzate** di **Sessione prestazioni** o nelle pagine delle proprietà del file binario di destinazione:  
  
- Se si specificano le funzioni nella pagina delle proprietà della sessione di prestazioni, solo tali funzioni vengono instrumentate in tutti i file binari instrumentati della sessione.  
  
- Se si specificano le funzioni nella pagina delle proprietà del file binario di destinazione, solo le funzioni presenti in quel determinato file binario vengono instrumentate. Le funzioni negli altri file binari delle prestazioni vengono instrumentate con la modalità consueta.  
  
  Questo tipo di limitazione della raccolta dei dati è supportato solo quando viene selezionato il metodo di profilatura della strumentazione.  
  
> [!NOTE]
> È inoltre possibile usare la pagina **Avanzate** delle pagine delle proprietà di **Sessione prestazioni** per impostare le altre opzioni disponibili nello strumento di strumentazione da riga di comando [VSInstr](../profiling/vsinstr.md) disponibile negli strumenti di profilatura.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Per limitare la strumentazione a specifiche funzioni in una sessione di prestazioni  
  
1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul nome della sessione e quindi scegliere **Proprietà**.  
  
    Verrà visualizzata la finestra di dialogo **Pagine delle proprietà**.  
  
2. Nella finestra di dialogo **Pagine delle proprietà** fare clic su **Avanzate**.  
  
3. Nella casella di testo **Opzioni di strumentazione aggiuntive** usare la sintassi seguente per digitare il nome delle funzioni da instrumentare:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` è il nome dello spazio dei nomi e della funzione in questo formato `Namespace`**::**`FunctionName`. Usare un punto e virgola per separare più funzioni. Usare un asterisco (\*) per specificare un carattere jolly per uno o più caratteri. Ad esempio, **/include: MyNS::\\*** specifica tutte le funzioni nello spazio dei nomi MyNS.  
  
   > [!NOTE]
   > Per elencare le funzioni in un file binario, aprire una finestra del prompt dei comandi nella directory di installazione degli strumenti di profilatura (in genere, la directory \Team Tools\Performance Tools nella directory di installazione di [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]) e quindi digitare **vsinstr /DumpFuncs**  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Per limitare la strumentazione a specifiche funzioni in un file binario  
  
1. In **Esplora prestazioni** individuare il nome del file binario nel nodo **Destinazioni** della sessione di prestazioni.  
  
2. Fare clic con il pulsante destro del mouse sul nome del file binario e quindi scegliere **Proprietà**.  
  
    Verrà visualizzata la finestra di dialogo **Pagine delle proprietà**.  
  
3. Nella finestra di dialogo **Pagine delle proprietà** fare clic su **Avanzate**.  
  
4. Nella casella di testo **Opzioni di strumentazione aggiuntive** usare la sintassi seguente per digitare il nome delle funzioni da instrumentare:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` è il nome dello spazio dei nomi e della funzione in questo formato `Namespace`**::**`FunctionName`. Usare un punto e virgola per separare più funzioni. Usare un asterisco (\*) per specificare un carattere jolly per uno o più caratteri. Ad esempio, **/include: MyNS::\\*** specifica tutte le funzioni nello spazio dei nomi MyNS.  
  
   > [!NOTE]
   > Per elencare le funzioni in un file binario, aprire una finestra del prompt dei comandi nella directory di installazione degli strumenti di profilatura (in genere, la directory \Team Tools\Performance Tools nella directory di installazione di [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]) e quindi digitare **vsinstr /DumpFuncs**  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)   
 [Procedura: Limite di strumentazione a specifiche DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Procedura: Specificare opzioni di strumentazione aggiuntive](../profiling/how-to-specify-additional-instrumentation-options.md)
