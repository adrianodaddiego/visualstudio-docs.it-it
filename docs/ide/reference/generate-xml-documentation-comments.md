---
title: Inserire commenti relativi alla documentazione XML
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 085e2fe029daf246f6883e6856ddff6a9bacccdc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790109"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Procedura: Inserire commenti XML per la generazione di documentazione

Visual Studio consente di documentare gli elementi del codice, ad esempio classi e metodi, generando automaticamente la struttura standard per i commenti in formato documentazione XML. In fase di compilazione, è possibile generare un file XML che contiene i commenti in formato di documentazione.

> [!TIP]
> Per informazioni sulla configurazione di nome e percorso del file XML generato, vedere [Documentazione del codice con i commenti XML (Guida per C#)](/dotnet/csharp/codedoc).

Il file XML generato dal compilatore può essere distribuito insieme agli assembly .NET in modo che Visual Studio e altri IDE possano usare IntelliSense per visualizzare informazioni rapide su tipi e membri. È anche possibile eseguire il file XML tramite strumenti, ad esempio [DocFX](https://dotnet.github.io/docfx/) e [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) per generare i siti Web di riferimento all'API.

> [!NOTE]
> Il comando **Inserisci commento** per inserire automaticamente i commenti in formato documentazione XML è disponibile in [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) e [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). È comunque possibile inserire manualmente [commenti in formato documentazione XML in file C++](/cpp/ide/xml-documentation-visual-cpp) e generare file di documentazione XML in fase di compilazione.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Per inserire commenti XML per un elemento di codice

1. Posizionare il cursore del testo sopra l'elemento da documentare, ad esempio, un metodo.

1. Eseguire una delle operazioni seguenti:

   - Digitare `///` in C# o `'''` in Visual Basic

   - Dal menu **Modifica** scegliere **IntelliSense** > **Inserisci commento**

   - Dal menu di scelta rapida per l'elemento di codice o appena sopra l'elemento scegliere **Frammento** > **Inserisci commento**

   Il modello XML viene generato subito sopra l'elemento di codice. Ad esempio, quando si aggiungono commenti a un metodo, vengono generati l'elemento **\<summary\>**, un elemento **\<param\>** per ogni parametro e un elemento **\<returns\>** per documentare il valore restituito.

   ![Modello di commento XML - C#](media/doc-preview-cs.png)

   ![Modello di commento XML - Visual Basic](media/doc-preview-vb.png)

1. Immettere descrizioni per ogni elemento XML per documentare in modo completo l'elemento di codice.

   ![Commento completato](media/doc-result-cs.png)

> [!NOTE]
> È disponibile un'[opzione](../../ide/reference/options-text-editor-csharp-advanced.md) per attivare/disattivare i commenti in formato documentazione XML dopo aver digitato `///` in C# o `'''` in Visual Basic. Dalla barra dei menu scegliere **Strumenti** > **Opzioni** per aprire la finestra di dialogo **Opzioni**. Passare quindi a **Editor di testo** > **C#** o **Basic** > **Avanzate**. Nella sezione **Guida editor** cercare l'opzione **Genera commenti relativi alla documentazione XML**.

## <a name="see-also"></a>Vedere anche

- [Commenti in formato documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentazione del codice con i commenti XML (Guida per C#)](/dotnet/csharp/codedoc)
- [Procedura: Creare documentazione XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Commenti C++](/cpp/cpp/comments-cpp)
- [Documentazione XML (C++)](/cpp/ide/xml-documentation-visual-cpp)
- [Generazione di codice](../code-generation-in-visual-studio.md)